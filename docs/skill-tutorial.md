# md2wx Skill · 5 分钟入门教程

本教程教你如何在 Claude Code 里用 md2wx Skill,全程在对话里完成"起草 → 排版 → 发布"。

## 第一步:安装 Skill

```bash
# 项目级(推荐)
mkdir -p .claude/skills && curl -fsSL \
  https://raw.githubusercontent.com/aipickgold/md2wx/main/skills/md2wx/SKILL.md \
  -o .claude/skills/md2wx.md
```

装完重启 Claude Code 或 `/reload`,skill 自动加载。

## 第二步:准备你的 API Key

- 打开 [aipickgold.com](https://aipickgold.com) 注册(免费版即可开始)
- 订阅 Pro 或 Lifetime 后在账号页拿到 `X-API-Key`
- (可选)准备公众号 AppID + AppSecret,用于一键发布草稿箱

## 第三步:在 Claude Code 里触发

### 触发词

说这些词 Skill 自动激活:

- 公众号 · 微信排版 · 发公众号 · 推送草稿
- WxMD · md2wx · 一键发布 · 草稿箱

### 示例对话

```
用户:帮我写一篇关于 AI 写作工具的公众号文章,用聚焦蓝主题,然后发到草稿箱

Claude: 好的!我理解为:
  - 主题:AI 写作工具(生产力/测评向)
  - 风格:聚焦蓝(focus-blue,商业/专业)
  - 目标:推送到你公众号的草稿箱

  正在起草...
  [markdown 草稿 1280 字]

  正在调用 md2wx API 渲染... ✓
  正在推送草稿... ✓

  已完成:草稿 ID 23xxx 已推到你公众号的草稿箱。
  去 mp.weixin.qq.com → 草稿箱即可看到、编辑、发布。
```

## 第四步:常见陷阱

### 凭证管理

- 不要在对话里明文贴 AppSecret
- 可以让 Skill 使用环境变量或让它提示用户"请到浏览器网页端配置一次"
- Skill 在调用完成后不会记住凭证

### 图片处理

- Markdown 里的图片必须是**公网 URL**(`https://...`)
- 不支持本地路径 `./img.png`,不支持 `data:` base64(公众号后台不认)
- 推荐图床:微信公众号自带素材库(最稳)、阿里云 OSS、腾讯云 COS

### 主题选择

如果不指定,Skill 默认用 `bytedance`(经典蓝)。常用主题:
- `bytedance`:通用 / 科技 / 资讯
- `minimal`:深度 / 长文 / 学术
- `focus-blue`:商业 / 金融
- `gradient-purple`:品牌 / 营销

完整列表:[theme-gallery](https://aipickgold.com/theme-gallery)

### 公众号限制

- 个人订阅号不支持 draft API(微信限制,需要企业或个人认证后才能用)
- 一篇文章最多 20000 字,建议 15000 字内最稳
- 草稿箱每个月有配额上限,超了会报 `48001`

## 第五步:Pro 解锁的能力

- 无限 API 调用(免费版每天 10 次)
- 40+ 主题 vs 免费的 10 基础主题
- 一键发布 API 访问
- 优先邮件支持

订阅:[aipickgold.com/pricing](https://aipickgold.com/pricing)

## 下一步

- [看 10 个使用场景示例](./examples.md)
- [查完整 API 参考](./api-reference.md)
- [理解 3 层架构](./architecture.md)

遇到问题?开 Issue 或邮件 hello@aipickgold.com。
