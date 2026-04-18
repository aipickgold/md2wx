# md2wx · 微信公众号 Markdown 排版

<div align="center">

<br/>

**AI 时代创作者的公众号排版神器 · Skill-first**

**在 Claude Code 对话里说一句话,排版 + 发布一气呵成**

<br/>

[English](./README.en.md) · **简体中文**

[![Website](https://img.shields.io/badge/\u5b98\u7f51-aipickgold.com-F43F5E?style=for-the-badge&logoColor=white)](https://aipickgold.com)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](./LICENSE)
[![Themes](https://img.shields.io/badge/Themes-40%2B-6366F1?style=for-the-badge)](https://aipickgold.com/theme-gallery)
[![Stars](https://img.shields.io/github/stars/aipickgold/md2wx?style=for-the-badge&logo=github&color=yellow)](https://github.com/aipickgold/md2wx/stargazers)
[![Release](https://img.shields.io/github/v/release/aipickgold/md2wx?style=for-the-badge&color=brightgreen)](https://github.com/aipickgold/md2wx/releases)
[![Last Commit](https://img.shields.io/github/last-commit/aipickgold/md2wx?style=for-the-badge)](https://github.com/aipickgold/md2wx/commits/main)
[![Issues](https://img.shields.io/github/issues/aipickgold/md2wx?style=for-the-badge)](https://github.com/aipickgold/md2wx/issues)

<br/>

[🧠 Skill 文档](./skills/md2wx/README.md) · [📚 Skill 教程](./docs/skill-tutorial.md) · [🎯 使用示例](./docs/examples.md) · [📐 架构](./docs/architecture.md) · [🌐 官网](https://aipickgold.com) · [🎴 姐妹产品 md2card](https://github.com/aipickgold/md2card)

</div>

---

## 🧠 Part 1 · 推荐用法(Claude Code Skill)

**md2wx 的主要使用方式不是打开网页,而是作为 Claude Code Skill 安装。**
安装一次后,在对话里让 AI 帮你"写文章 + 排版 + 发公众号",全程不切窗口。

### 一键安装

```bash
# 项目级(推荐用于单个写作项目)
mkdir -p .claude/skills && curl -fsSL \
  https://raw.githubusercontent.com/aipickgold/md2wx/main/skills/md2wx/SKILL.md \
  -o .claude/skills/md2wx.md

# 全局级(所有项目共用)
mkdir -p ~/.claude/skills && curl -fsSL \
  https://raw.githubusercontent.com/aipickgold/md2wx/main/skills/md2wx/SKILL.md \
  -o ~/.claude/skills/md2wx.md
```

### 3 个对话示范

```
👤 "帮我写一篇关于 AI 工具的公众号,用聚焦蓝主题"

🤖 ✓ 已起草 1280 字
   ✓ 已用聚焦蓝主题渲染
   ✓ 已推送到你的公众号草稿箱 📝
   → mp.weixin.qq.com 草稿箱查看
```

```
👤 "把这段 markdown 排版成公众号格式,换 5 个不同主题给我看"

🤖 已为你生成 5 个版本:
   1. 经典橙 · 适合通用场景
   2. 极简墨 · 适合深度文章
   3. 聚焦蓝 · 适合商业
   4. 渐变紫 · 适合品牌
   5. 卡片绿 · 适合教程
   你选哪个版本推送?
```

```
👤 "用科技黑主题排,加个封面图 https://xxx.jpg"

🤖 ✓ 已渲染 + 已发 + 已带封面
   草稿 ID: 23xxx...
```

### Skill 工作流

```
Claude Code 对话
    ↓ 起草 Markdown(若没有)
    ↓ 调 /api/convert 渲染
    ↓ 调 /api/publish-wechat(BYO AppID+Secret)
    ↓
你公众号的草稿箱 📝
```

👉 **详细教程**:[docs/skill-tutorial.md](./docs/skill-tutorial.md) · **10 个使用场景**:[docs/examples.md](./docs/examples.md)

---

## 💻 Part 2 · 替代方案(网页 Demo / REST API)

如果你不用 Claude Code,也可以走网页或 API。**功能一模一样**,只是手工操作更繁琐。

### 网页版

打开 [**aipickgold.com**](https://aipickgold.com) → 粘贴 Markdown → 选主题 → 右上角「复制」→ 粘到公众号后台。

或走独家 **🚀 一键发布**(Pro):填入 AppID + AppSecret(仅本地存储)→ 点「发布」3 秒直达草稿箱。

### REST API

```bash
curl -X POST https://aipickgold.com/api/convert \
  -H "Content-Type: application/json" \
  -H "X-API-Key: your-key" \
  -d '{"markdown": "# 标题\n\n正文", "theme": "bytedance"}'
```

响应:
```json
{"html": "<section>...</section>", "wordCount": 1280, "theme": "bytedance"}
```

👉 **完整 API 文档**:[docs/api-reference.md](./docs/api-reference.md)

---

## 🎨 40+ 主题 · 5 大系列 × 8 配色

| 系列 | 风格 | 适合 |
|---|---|---|
| **经典** | 色带标题 + 装饰 | 通用、科技、资讯 |
| **极简** | 白底黑字、无装饰 | 深度文章、学术 |
| **聚焦** | 居中对称 | 商业、金融 |
| **渐变** | 渐变色彩 | 品牌、营销 |
| **卡片** | 分块、服务号风 | 产品、教程 |

每系列 8 种配色:红/橙/黄/绿/青/蓝/紫/黑。

👉 [aipickgold.com/theme-gallery](https://aipickgold.com/theme-gallery) 看全部 40+ 主题的完整预览

---

## 🚀 一键发布到微信公众号(WxMD 独家)

**这是 WxMD 相对其他排版工具最大的差异化能力**。无论走 Skill 还是网页,最后都能:

- 填一次 AppID + AppSecret(只存你本地)
- 排版完 → 3 秒推送到你公众号的「草稿箱」
- 适用于已认证的订阅号 / 服务号
- **Pro 订阅专享**

等于把创作闭环的最后一公里(复制 → 切后台 → 粘贴 → 再确认样式)直接抹平。

---

## 📐 技术架构

```
┌──────────────────────────┐
│  用户(你)                │
│  ──────────────────────  │
│  🧠 Claude Code Skill    │  ← 首推用法
│        ↓                 │
└────────┼─────────────────┘
         ↓ HTTPS
┌────────┴─────────────────┐
│  aipickgold.com 服务器    │  ← 我们只做这一层
│  /api/convert            │
│  /api/publish-wechat     │
│  /api/publish-wechat/verify │
└────────┬─────────────────┘
         ↓ HTTPS
┌────────┴─────────────────┐
│  微信官方 API             │
│  /cgi-bin/token          │
│  /cgi-bin/material/add_* │
│  /cgi-bin/draft/add      │
└──────────────────────────┘

   平行降级备选:
   aipickgold.com/ (网页 Demo · 浏览器里跑)
```

- **用户侧**:Skill(AI 对话触发)或 网页(手动粘贴)
- **服务器侧**:阿里云 ECS,JSON API 中转,不存内容、不跑 headless Chrome
- **浏览器侧**:Web Demo 用 React + Tailwind 渲染预览

👉 [docs/architecture.md](./docs/architecture.md) 完整架构说明

---

## 💎 定价

| 档位 | 价格 | 适合 |
|---|---|---|
| **免费版** | ¥0 | 每天 10 次 API 调用 + 10 基础主题 |
| **Pro 月付** | ¥19/月 | 无限调用 + 全部主题 + 一键发布 |
| **Pro 年付** | ¥99/年 | 月付 × 2 价格 × 12 省 63% |
| **Pro Lifetime** | ¥199 买断 | 永久 + 所有后续更新 |
| **合并 Lifetime** | ¥299 | md2wx + [md2card](https://github.com/aipickgold/md2card) 两产品永久 |

[→ 完整定价与 FAQ](https://aipickgold.com/pricing)

---

## 🗺️ Roadmap · 🕒 CHANGELOG

- [📝 v1.1.0](./CHANGELOG.md) — 2026-04 · Skill 官方上线 + 一键发布改选择器 UI + 网页降级为 demo
- [🗺️ 近期 / 中期 / 长期规划](./docs/roadmap.md)

---

## 🎴 姐妹产品

> **[md2card](https://github.com/aipickgold/md2card)** — 把长文一键切成 3:4 小红书卡片,55+ 主题,同样有 Claude Code Skill。
>
> 两产品共用账号,合并 Lifetime ¥299 一次永久拥有。

---

## 📜 License · 🤝 Contributing · 🔒 Security

- **License**:MIT(引擎代码开源,Pro 主题商业授权,字体 SIL OFL)
- **贡献**:欢迎提 Issue / PR。主题设计贡献参考 [CONTRIBUTING.md](./CONTRIBUTING.md)
- **安全**:[SECURITY.md](./SECURITY.md)

---

## 👤 作者 · 💬 联系

由 **[宸的拾金笔记](https://aipickgold.com/about)** 独立开发维护。

- 🌐 **官网**:[aipickgold.com](https://aipickgold.com)
- 📢 **公众号**:宸的拾金笔记
- ✉️ **邮箱**:soarwill06@gmail.com
- 💚 **微信**:`aipickgold`(大浪淘金)· 扫站内二维码加友

---

<div align="center">

**如果 md2wx 帮你省下了排版的时间,请点个 ⭐ Star 支持一下!**

Made with ❤️ by [宸的拾金笔记](https://aipickgold.com) · 2026

💬 [Discussions](https://github.com/aipickgold/md2wx/discussions) · 🐛 [Issues](https://github.com/aipickgold/md2wx/issues) · 🤝 [Contributing](./CONTRIBUTING.md) · 🔒 [Security](./SECURITY.md) · 🗺️ [Roadmap](./docs/roadmap.md)

[![Star History Chart](https://api.star-history.com/svg?repos=aipickgold/md2wx&type=Date)](https://star-history.com/#aipickgold/md2wx&Date)

</div>
