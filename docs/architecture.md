# md2wx · 3 层架构说明

## 为什么不是"又一个 Web 编辑器"

市场上公众号排版工具很多,大部分逻辑是:用户打开网页 → 粘贴 markdown → 选主题 → 复制 HTML → 切后台 → 粘贴 → 手工调整。

我们换一种角度:**把排版能力暴露给 AI 编程工作流**,让 AI 直接调用,免去用户切窗口。这就是 Skill-first 架构。

## 3 层设计

```
┌────────────────────────────────────┐
│ Layer 1 · 用户侧                    │
│ ──────────────────                  │
│ 🧠 Claude Code Skill(首推)         │
│    - 在 AI 对话里触发                │
│    - 自动起草 / 选主题 / 调 API     │
│                                    │
│ 💻 网页(降级备选)                  │
│    aipickgold.com                  │
│    - 手动粘贴 / 手动点按钮          │
└──────────────┬─────────────────────┘
               ↓ HTTPS POST
┌──────────────┴─────────────────────┐
│ Layer 2 · 服务器侧(API)           │
│ ──────────────────                  │
│ 阿里云 ECS 单实例 · 894MB RAM       │
│                                    │
│ /api/convert                       │
│   Markdown → 渲染 HTML(无状态)    │
│                                    │
│ /api/publish-wechat/verify         │
│   验证 AppID+Secret(仅 token 交换) │
│                                    │
│ /api/publish-wechat                │
│   代理到微信官方 draft API         │
│   (上传封面 + 创建草稿)           │
│                                    │
│ 🔒 不存内容 · 不跑 Chrome · 不记日志 │
└──────────────┬─────────────────────┘
               ↓ HTTPS POST
┌──────────────┴─────────────────────┐
│ Layer 3 · 微信官方 API              │
│ ──────────────────                  │
│ api.weixin.qq.com                  │
│ /cgi-bin/token                     │
│ /cgi-bin/material/add_material     │
│ /cgi-bin/draft/add                 │
└────────────────────────────────────┘
```

## 各层的边界

### 用户侧
- **Skill 不存任何凭证**,每次对话即用即走
- **网页凭证**只存在你的浏览器 localStorage,不上传我们服务器
- 渲染、预览、复制都是浏览器本地完成

### 服务器侧(我们)
- 不持久化你的 Markdown 或 AppSecret
- 代理请求完成后立即丢弃凭证
- 日志只记 `errcode` 映射,不记业务内容
- 单实例无状态,水平扩展简单

### 微信侧
- 所有"发布"动作最终落在你自己的公众号账号下
- 我们不持有微信 API 权限,你随时可以在微信后台重置 AppSecret 把我们踢出

## 为什么这么设计

1. **成本**:服务器只做 JSON 中转,资源占用极低(ECS 894MB 内存足够跑几万次/日)
2. **隐私**:你的 Markdown 内容不留在我们这,只经过瞬间
3. **安全**:AppSecret 的掌控权始终在你手上
4. **AI 友好**:Skill 的输入/输出是纯文本,AI 能无缝对接
5. **速度**:没有 Chrome 开销,Skill 一次调用 < 3 秒

## 极端情况

### 如果 aipickgold.com 挂了?

- Skill 会报错,但**不影响你的公众号账号**(API 没调用到)
- 网页版用户无法打开,但已有草稿不受影响
- 我们有阿里云单机+多地备份,可快速恢复

### 如果你不信任我们的中转?

- 完全可以自己部署:Clone 仓库(`soarsky1991/md2wx` 私有) → 自己运行 Next.js
- Skill 里的 API URL 改成你自己的域名即可

### 如果 AppSecret 泄露?

- 登录 [mp.weixin.qq.com](https://mp.weixin.qq.com) → 开发 → 基本配置 → 重置 AppSecret
- 立即生效,旧 Secret 失效

## 未来扩展

- `/api/convert` 输出多格式(HTML / PDF / 图片)
- `/api/publish-wechat/list-drafts` 列出已发草稿(只读)
- Skill 支持多账号切换
- 更多目标平台:头条号、企鹅号、知乎

---

有问题或建议,欢迎 [提 Issue](https://github.com/aipickgold/md2wx/issues)。
