# xhs-auto-publish

Xiaohongshu (小红书) auto-publish skill for [OpenClaw](https://github.com/openclaw/openclaw) agents.

Automate image+text post (图文笔记) publishing on xiaohongshu.com creator platform via browser CDP automation. No API key needed.

## Features

- 📸 Multi-image upload (1-18 images)
- ✏️ Auto-fill title (20 char limit) and body (1000 char limit)
- #️⃣ Hashtag support
- 🚀 Auto-publish or dry-run preview
- 📱 Works with any Chromium browser via CDP
- 🔒 No API keys or credentials stored — uses your existing browser session

## Install

### Via ClawHub (for OpenClaw users)
```bash
clawhub install xhs-auto-publish
```

### Manual
```bash
git clone https://github.com/jerryops2026-del/xhs-auto-publish.git
cd xhs-auto-publish
npm install
```

## Usage

```bash
node scripts/publish.js \
  --title "你的标题" \
  --body "正文内容" \
  --images cover.png,slide2.png \
  --hashtags "AI绘画,独立开发" \
  --cdp-url http://127.0.0.1:9222
```

### Options

| Flag | Description | Default |
|------|-------------|---------|
| `--title` | Post title (max 20 chars) | Required |
| `--body` | Post body (max 1000 chars) | Required* |
| `--body-file` | Read body from text file | — |
| `--images` | Comma-separated image paths | Required |
| `--hashtags` | Comma-separated hashtags | Optional |
| `--cdp-url` | Chrome CDP endpoint | `http://127.0.0.1:9222` |
| `--dry-run` | Preview only, don't publish | Off (auto-publish) |
| `--screenshot` | Save preview screenshot | Auto-generated |

### Prerequisites

1. `playwright-core` (`npm install`)
2. A Chromium browser with remote debugging enabled
3. Logged in to `creator.xiaohongshu.com`

For **OpenClaw** users: the managed browser provides CDP automatically.

## How It Works

1. Connects to your browser via Chrome DevTools Protocol (CDP)
2. Opens `creator.xiaohongshu.com/publish/publish`
3. Switches to image post mode (上传图文)
4. Uploads images, fills title & body
5. Clicks publish (or saves preview in dry-run mode)

## License

MIT
