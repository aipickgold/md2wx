# md2wx API Reference

基础 URL:`https://aipickgold.com`

所有请求用 `Content-Type: application/json`。

---

## `POST /api/convert`

Markdown → 公众号兼容 HTML。无状态,可缓存结果。

### 请求

```json
{
  "markdown": "# 标题\n\n正文...",
  "theme": "bytedance"
}
```

| 字段 | 类型 | 说明 |
|---|---|---|
| `markdown` | string | 必填。Markdown 源文 |
| `theme` | string | 可选。主题 id,默认 `bytedance`。详见 [theme-gallery](https://aipickgold.com/theme-gallery) |

Header:

| 字段 | 说明 |
|---|---|
| `X-API-Key` | Pro/Lifetime 必填。去 aipickgold.com 账号页获取 |

### 响应

```json
{
  "html": "<section>...</section>",
  "wordCount": 1280,
  "theme": "bytedance"
}
```

### 错误

| HTTP | errmsg | 解决 |
|---|---|---|
| 400 | "markdown 不能为空" | 检查请求体 |
| 401 | "API Key 无效" | 在账号页重新获取 |
| 429 | "调用频率超限" | 免费版 10/天,升级 Pro |
| 500 | "服务器内部错误" | 稍后重试或邮件反馈 |

---

## `POST /api/publish-wechat/verify`

仅验证 AppID + AppSecret 是否能换取 access_token。不创建任何草稿。

### 请求

```json
{
  "appid": "wx...",
  "appsecret": "..."
}
```

### 响应

成功:
```json
{
  "success": true,
  "expiresIn": 7200,
  "message": "凭证有效,可以发布了"
}
```

失败:
```json
{
  "success": false,
  "errcode": 40001,
  "errmsg": "AppID 或 AppSecret 错误,请检查凭证"
}
```

---

## `POST /api/publish-wechat`

代理到微信官方 `/cgi-bin/draft/add`,创建公众号草稿。

### 请求

```json
{
  "appid": "wx...",
  "appsecret": "...",
  "title": "文章标题(必填,≤64 字符)",
  "content": "<渲染后的 HTML>",
  "author": "作者(可选)",
  "digest": "摘要(可选,≤120 字符)",
  "coverImageUrl": "https://...cover.jpg(可选,公网 URL)",
  "showCoverPic": 1
}
```

| 字段 | 类型 | 说明 |
|---|---|---|
| `appid` | string | 公众号 AppID |
| `appsecret` | string | 公众号 AppSecret |
| `title` | string | 标题,自动截断到 64 字符 |
| `content` | string | HTML 内容,≤200KB |
| `author` | string? | 作者,可选 |
| `digest` | string? | 摘要,自动截断到 120 字符 |
| `coverImageUrl` | string? | 封面图公网 URL,http/https 协议,≤10MB |
| `showCoverPic` | 0 \| 1 | 是否在正文显示封面,默认 1 |

### 响应

成功:
```json
{
  "success": true,
  "media_id": "...(草稿 id)",
  "coverMediaId": "...(封面素材 id,若传了封面)",
  "message": "草稿已创建,请到公众号后台「草稿箱」查看"
}
```

失败:同 verify 的格式,`errcode` 映射:

| errcode | 含义 | 解决 |
|---|---|---|
| 40001 | AppID/AppSecret 错 | 检查凭证 / 重置 |
| 40013 | AppID 无效 | 核对 AppID |
| 45009 | 频率超限 | 等几分钟再试 |
| 48001 | API 未授权 | 确认公众号已企业/个人认证 |
| 400 | 参数错 | 检查 title/content 是否为空 |
| 500 | 内部错 | 邮件反馈 |

### 隐私

- 服务器不记录 appid/appsecret 到任何日志
- 请求结束立即丢弃,不持久化
- 详见 [aipickgold.com/privacy](https://aipickgold.com/privacy)

---

## 代码示例

### cURL

```bash
# 1. 渲染
curl -X POST https://aipickgold.com/api/convert \
  -H "Content-Type: application/json" \
  -H "X-API-Key: wme_xxx" \
  -d '{"markdown": "# Hello\n\n世界", "theme": "bytedance"}' \
  | jq .

# 2. 发布草稿
curl -X POST https://aipickgold.com/api/publish-wechat \
  -H "Content-Type: application/json" \
  -d '{
    "appid": "wx...",
    "appsecret": "...",
    "title": "Hello",
    "content": "<section>...</section>"
  }'
```

### JavaScript

```js
async function convert(markdown, theme = "bytedance") {
  const r = await fetch("https://aipickgold.com/api/convert", {
    method: "POST",
    headers: { "Content-Type": "application/json", "X-API-Key": process.env.WXMD_KEY },
    body: JSON.stringify({ markdown, theme }),
  });
  return r.json();
}
```

### Python

```python
import httpx

async def convert(markdown: str, theme: str = "bytedance") -> dict:
    async with httpx.AsyncClient() as c:
        r = await c.post(
            "https://aipickgold.com/api/convert",
            json={"markdown": markdown, "theme": theme},
            headers={"X-API-Key": os.environ["WXMD_KEY"]},
        )
        return r.json()
```

---

## Rate Limiting

| Plan | /api/convert | /api/publish-wechat |
|---|---|---|
| Free | 10/day | — |
| Pro Monthly | 1000/day | Pro 起 |
| Pro Yearly | 无限 | 无限 |
| Lifetime | 无限 + 优先 | 无限 + 优先 |

---

## 版本兼容

- 目前 API 在 v1,无破坏性变更
- 新增字段向后兼容
- 废弃字段会在 CHANGELOG 预告 30 天以上

[详见 CHANGELOG.md](../CHANGELOG.md)
