# Project: md2wx

**品牌**:宸的拾金笔记(aipickgold)
**官网**:https://aipickgold.com
**产品定位**:AI 时代独立创作者的公众号排版神器 — 把 Markdown 一键变成微信公众号美文

## 仓库性质

这是 **推广仓库**,只承载 README、LICENSE、CHANGELOG、截图、文档等用于 GitHub 展示的元数据。
**不含应用代码**。实际代码在私有仓库 `soarsky1991/md2wx`(Next.js + TypeScript)。

## 相关链接

- 产品页:https://aipickgold.com
- 主题画廊:https://aipickgold.com/theme-gallery
- 定价:https://aipickgold.com/pricing
- API 文档:https://aipickgold.com/api-docs
- 姐妹仓库:https://github.com/aipickgold/md2card(小红书图文卡片生成器)

## PR Checklist

- [ ] 更新 `CHANGELOG.md`,版本号遵循 SemVer
- [ ] 更新 `README.md` 与 `README.en.md` 若有外部信息变化(定价、主题数量、feature)
- [ ] 所有链接可解析(官网、文档、姐妹仓库)
- [ ] 图片资源放 `assets/`,不提交大于 1MB 的单文件
- [ ] 敏感信息(.env、token、API Key)绝不提交

## Commit Format

`<type>(<scope>): <subject>`

**type**:`feat` · `fix` · `docs` · `chore` · `style`

示例:
- `docs(readme): bump theme count to 45`
- `chore(meta): enrich project metadata`
- `fix(link): correct pricing URL`
