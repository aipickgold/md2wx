# md2wx · 微信公众号 Markdown 排版工具

<div align="center">

<br/>

**AI 时代独立创作者的公众号排版神器**

**把 Markdown 一键变成微信公众号美文 · 40+ 主题 · 发稿只花 30 秒**

<br/>

[English](./README.en.md) · **简体中文**

[![Website](https://img.shields.io/badge/官网-aipickgold.com-F43F5E?style=for-the-badge&logoColor=white)](https://aipickgold.com)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](./LICENSE)
[![Themes](https://img.shields.io/badge/Themes-40%2B-6366F1?style=for-the-badge)](https://aipickgold.com/theme-gallery)
[![Stars](https://img.shields.io/github/stars/aipickgold/md2wx?style=for-the-badge&logo=github&color=yellow)](https://github.com/aipickgold/md2wx/stargazers)
[![Release](https://img.shields.io/github/v/release/aipickgold/md2wx?style=for-the-badge&color=brightgreen)](https://github.com/aipickgold/md2wx/releases)
[![Last Commit](https://img.shields.io/github/last-commit/aipickgold/md2wx?style=for-the-badge)](https://github.com/aipickgold/md2wx/commits/main)
[![Issues](https://img.shields.io/github/issues/aipickgold/md2wx?style=for-the-badge)](https://github.com/aipickgold/md2wx/issues)

<br/>

[官网使用](https://aipickgold.com) · [主题画廊](https://aipickgold.com/theme-gallery) · [查看定价](https://aipickgold.com/pricing) · [姐妹产品 md2card](https://github.com/aipickgold/md2card)

</div>

---

## 🚀 独家 · 一键发布到微信公众号

别的在线排版工具让你「复制 → 切到公众号后台 → 粘贴 → 确认样式」,**WxMD 直接推进你的草稿箱**。

```
Markdown 编辑 → 🚀 一键发布 → 📝 公众号草稿箱
```

- 填一次 AppID + AppSecret(只存在你的浏览器,不上传服务器)
- 编辑完 → 点「一键发布」 → **3 秒完成**
- 告别来回切窗口,真正打通创作闭环
- 适用于已认证的订阅号 / 服务号(个人订阅号因微信 API 限制暂不支持)
- **Pro 订阅专享** · 这是 WxMD 相对其他排版工具最大的差异化能力

> 📌 获取凭证:登录 [mp.weixin.qq.com](https://mp.weixin.qq.com) → 开发 → 基本配置

---

## ✨ 为什么选 WxMD

公众号创作者 90% 的时间浪费在排版上。**WxMD 把这个时间压缩到 30 秒**。

- **🚀 独家:一键发布到公众号草稿箱** — 其他工具没有的能力(Pro)
- **打开浏览器就能用** — 不装软件、不注册、免费起步
- **40+ 精选主题** — 5 大系列 × 8 配色,覆盖科技/资讯/情感/生活/财经
- **完整 GFM 扩展** — 提示框、对话框、图集、长图、脚注全支持
- **一键复制到公众号** — 粘贴直出,样式不丢、排版不乱
- **微信原生兼容** — 每个主题都在微信后台实测过
- **本地渲染** — 内容不上传服务器,隐私友好

---

## 🚀 快速开始

### 方法一:直接浏览器使用(推荐)

```
1. 打开 https://aipickgold.com
2. 把 Markdown 粘贴到左侧编辑区
3. 选择主题 → 右上角「复制」
4. 粘贴到公众号后台图文编辑器 → 完成!
```

### 方法二:API 调用(Pro 订阅)

```bash
curl -X POST https://aipickgold.com/api/convert \
  -H "Content-Type: application/json" \
  -H "X-API-Key: your-key-here" \
  -d '{"markdown": "# Hello\n\n这是正文", "theme": "bytedance"}'
```

响应:

```json
{
  "html": "<section>...</section>",
  "wordCount": 2,
  "theme": "bytedance"
}
```

---

## 🎨 主题系列

| 系列 | 风格 | 典型场景 |
|---|---|---|
| **经典** | 色带标题 + 引用块 + 装饰 | 科技、资讯、评测 |
| **极简** | 白底黑字,无装饰 | 深度文章、学术 |
| **聚焦** | 居中对齐,强调阅读节奏 | 商业、金融 |
| **渐变** | 标题渐变色 | 品牌、营销 |
| **卡片** | 内容分块,类似微信服务号 | 产品、教程 |

每个系列 8 种配色 —— 红、橙、黄、绿、青、蓝、紫、黑。

[→ 查看全部 40+ 主题的完整预览](https://aipickgold.com/theme-gallery)

---

## 📸 截图

> 截图建设中 —— 可先访问官网 [aipickgold.com](https://aipickgold.com) 看实时效果

---

## 📝 支持的语法

**标准 Markdown**:H1-H6 标题、加粗、斜体、链接、图片、列表、表格、代码块、引用、分割线

**GFM 扩展**:
- `> [!NOTE]` 蓝色提示
- `> [!TIP]` 绿色技巧
- `> [!IMPORTANT]` 紫色重要
- `> [!WARNING]` 橙色警告
- `> [!CAUTION]` 红色注意

**自定义容器**:
- `:::dialogue[标题]` — 多人对话气泡
- `:::gallery[标题]` — 多图横滑画廊
- `:::longimage[标题]` — 长图容器
- `[^1]` + `[^1]: 内容` — 脚注

---

## 💎 定价

| 档位 | 价格 | 适合 |
|---|---|---|
| **免费版** | ¥0 | 个人偶尔排版 |
| **Pro 年付** | ¥79 / 年 | 活跃创作者 |
| **Pro Lifetime** | ¥199 买断 | 长期用户 |
| **合并 Lifetime** | ¥299 | WxMD + [md2card](https://github.com/aipickgold/md2card) 两产品永久 |

[→ 完整定价方案与功能对比](https://aipickgold.com/pricing)

---

## 🗺️ 路线图

- [x] 40+ 主题库
- [x] GFM 扩展语法
- [x] 一键复制到公众号
- [x] API 服务
- [ ] 自定义主题编辑器(2026 Q3)
- [ ] AI 写作助手集成(2026 Q4)
- [ ] Claude Code / OpenClaw Skill 适配

---

## 🎴 姐妹产品

如果你也在做小红书图文,看看我们的另一款工具:

> **[md2card](https://github.com/aipickgold/md2card)** — 把长文一键切成 3:4 小红书卡片,55+ 主题。
>
> 两个产品共用一套账号,合并 Lifetime ¥299 一次搞定。

---

## 📜 License

MIT License · 个人与商业使用均免费,主题版权归作者所有。详见 [LICENSE](./LICENSE)。

---

## 👤 作者

由 **[宸的拾金笔记](https://aipickgold.com/about)** 独立开发维护。

- 🌐 **官网**:[aipickgold.com](https://aipickgold.com)
- 📢 **公众号**:宸的拾金笔记
- ✉️ **邮箱**:hello@aipickgold.com
- 💚 **微信**:待补充 (即将开放,可先邮件预约)

---

<div align="center">

**如果 md2wx 帮你省下了排版的时间,请点个 ⭐ Star 支持一下!**

Made with ❤️ by [宸的拾金笔记](https://aipickgold.com) · 2026

💬 [Discussions](https://github.com/aipickgold/md2wx/discussions) · 🐛 [Issues](https://github.com/aipickgold/md2wx/issues) · 🤝 [Contributing](./CONTRIBUTING.md) · 🔒 [Security](./SECURITY.md) · 🗺️ [Roadmap](./docs/roadmap.md)

[![Star History Chart](https://api.star-history.com/svg?repos=aipickgold/md2wx&type=Date)](https://star-history.com/#aipickgold/md2wx&Date)

</div>
