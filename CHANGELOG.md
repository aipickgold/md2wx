# Changelog

All notable changes to **md2wx** are documented here. This project follows [Semantic Versioning](https://semver.org/) and the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format.

## [v1.1.0] · 2026-04-18

### Added
- 🧠 **Claude Code Skill 官方上线**(`skills/md2wx/SKILL.md`)· 一键安装到 Claude Code,对话式排版+发布
- 📚 `docs/skill-tutorial.md` · `docs/examples.md`(10 场景)· `docs/architecture.md` · `docs/api-reference.md`
- README 全面改版为 Skill-first 结构

### Changed
- 网页版"🚀 一键发布"按钮改为**选择器弹窗**:推荐 Skill 路径,保留网页直接发布作为替代
- 网页版定位调整为**演示用**,主要使用方式是 Skill
- Skill 安装命令 + 3 个对话示范加入 README 第一节

### Notes
- 订阅价格不变:¥19/月 · ¥99/年 · ¥199 Lifetime · ¥299 合并
- API schema 向后兼容

## [Unreleased]

### Planned
- 自定义主题编辑器(2026 Q3)
- AI 写作助手集成(2026 Q4)
- Claude Code / OpenClaw Skill 适配

---

## [v2.1.0] - 2026-04

最大的一次排版引擎升级,新增对话框、图片画廊、脚注等高级排版组件。

### Added
- 排版引擎升级:完整支持 H1-H6 六级标题、图片布局、代码语法高亮、GFM 提示框
- 对话框系统:`:::dialogue[标题]` 多人对话,自动分配渐变气泡颜色与 emoji 头像
- 图片画廊:`:::gallery[标题]` 多图横滑展示
- 长图容器:`:::longimage[标题]` 固定高度内部滚动
- 脚注系统:`[^1]` 正文引用 + `[^1]: 内容` 文末定义
- 主题画廊悬浮详情弹窗:预览缩放 0.45,详情 modal

### Changed
- 标题由固定宽度改为自适应胶囊形设计
- 编辑器预览区改为米色背景 + 纸张效果
- 预览区滚动同步逻辑重写,对应关系更精准

### Fixed
- 修复某些主题下表格错位
- 修复列表嵌套渲染异常

---

## [v2.0.0] - 2026-03

全新主题系统上线,主题数量从 10 扩展到 40,同步完成全站页面体系。

### Added
- 全新 **5 系列 × 8 配色 = 40 款主题**:经典 / 极简 / 聚焦 / 渐变 / 卡片
- 首页 API 渲染,支持扩展语法
- 主题画廊重构:卡片网格 + 详情预览
- 全站页面体系:特色功能 / 定价 / 博客 / 更新日志 / API 文档 / 帮助
- Hamburger 侧滑导航菜单

### Changed
- 品牌从「极客杰尼 / geeki.cc」全站替换为「宸的拾金笔记 / aipickgold.com」
- 主题渲染完全本地化,隐私更友好

---

## [v1.5.0] - 2025-03

API 转换服务正式对外开放。

### Added
- API 转换服务:`POST /api/convert`,BYO X-API-Key
- 主题画廊页面
- 批量转换支持

---

## [v1.2.0] - 2025-02

编辑器体验优化版。

### Added
- Markdown 快捷键(加粗、斜体、标题切换、插入链接)
- 实时字数 + 阅读时间统计

### Changed
- 预览区滚动同步优化

### Fixed
- 修复列表嵌套渲染异常
- 修复表格在部分主题下错位

---

## [v1.0.0] - 2025-01

### Added
- 在线 Markdown 编辑器 + 实时预览面板
- 一键复制到微信后台
- 10 款基础主题
- 标准 Markdown 语法:标题、列表、引用、粗斜体、链接、图片、表格、代码块
- CodeMirror 语法高亮与自动补全

[Unreleased]: https://github.com/aipickgold/md2wx/compare/v2.1.0...HEAD
[v2.1.0]: https://github.com/aipickgold/md2wx/releases/tag/v2.1.0
[v2.0.0]: https://github.com/aipickgold/md2wx/releases/tag/v2.0.0
[v1.5.0]: https://github.com/aipickgold/md2wx/releases/tag/v1.5.0
[v1.2.0]: https://github.com/aipickgold/md2wx/releases/tag/v1.2.0
[v1.0.0]: https://github.com/aipickgold/md2wx/releases/tag/v1.0.0
