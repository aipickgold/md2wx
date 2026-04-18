# md2wx Skill for Claude Code

让 Claude Code 直接帮你把文章排版成公众号格式 + 一键发到草稿箱,全程在对话里完成。

## 安装

### 方式一:项目级(推荐用于单个项目)

```bash
cd 你的项目根目录
mkdir -p .claude/skills
curl -fsSL https://raw.githubusercontent.com/aipickgold/md2wx/main/skills/md2wx/SKILL.md \
  -o .claude/skills/md2wx.md
```

### 方式二:全局级(所有项目共用)

```bash
mkdir -p ~/.claude/skills
curl -fsSL https://raw.githubusercontent.com/aipickgold/md2wx/main/skills/md2wx/SKILL.md \
  -o ~/.claude/skills/md2wx.md
```

下次打开 Claude Code 时,skill 自动生效。

## 使用

在 Claude Code 对话里说:

- "帮我写一篇关于 AI 工具的公众号文章,用聚焦蓝主题"
- "把这段 Markdown 排版成公众号格式"
- "一键发到我的公众号草稿箱"
- "换个暖橙主题看看"

Claude Code 会自动调用 md2wx 的渲染 API + 可选的发布 API。

## 要素

- 免费用户每天 10 次 API 调用额度
- Pro / Lifetime 用户可以无限调用 + 一键发布到草稿箱
- 详见 [定价](https://aipickgold.com/pricing)

## 配套

姐妹 skill:`md2card`(小红书图文卡片生成)— https://github.com/aipickgold/md2card

---

任何问题:issue 或邮件 hello@aipickgold.com
