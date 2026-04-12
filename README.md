# SuperBased — Give Cursor Eyes on Your Screen

Screenshot capture, AI vision, OCR, screen recording, visual regression testing, token compression, voice dictation, and proactive screen monitoring — all via 28 MCP tools, directly inside Cursor.

## Install

### From Cursor Marketplace

Submit pending at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish).

### Local Plugin

Place in `~/.cursor/plugins/local/superbased` or symlink for development.

### MCP Server Only

Add to your project's `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "superbased": {
      "command": "superbased",
      "args": ["mcp"]
    }
  }
}
```

## Prerequisites

- **SuperBased desktop app** running (Windows or macOS), OR
- **SuperBased CLI** installed globally: `npm install -g superbased`
- Node.js 20+

## Skills (7)

| Skill | When Cursor Uses It |
|-------|-------------------|
| **screenshot** | Cursor needs to see the screen to answer a question or verify a UI change |
| **visual-qa** | Visual regression testing: record baseline, make changes, record again, diff |
| **monitor** | Proactive screen watching during deploys, tests, or builds |
| **compress** | Large text content (>500 tokens) that would be cheaper as an image |
| **redact** | Screenshots that may contain API keys, tokens, or PII before sharing |
| **dictation** | User wants voice input, audio transcription, or speech-to-text |
| **annotate** | Highlighting areas, marking regressions, creating annotated screenshots |

## Cursor Rules (3)

| Rule | Description |
|------|-------------|
| **superbased-capture** | When to use SuperBased for screen capture, window targeting, OCR |
| **superbased-privacy** | Redact sensitive info from screenshots before sharing |
| **superbased-recording** | Smart recording modes and visual regression testing workflow |

## Slash Commands (22)

| Command | Description |
|---------|-------------|
| `/superbased:capture` | Take a screenshot (fullscreen, window, or region) |
| `/superbased:window` | List open windows or capture a specific window |
| `/superbased:extract` | Capture + OCR to extract text from screen |
| `/superbased:explain` | Capture + AI analysis of what's on screen |
| `/superbased:ocr` | Extract text from screenshot or image file (local Tesseract) |
| `/superbased:clipboard` | Read or write system clipboard (text or image) |
| `/superbased:annotate` | Add rectangles, arrows, text labels, blur to captures |
| `/superbased:redact` | Auto-redact secrets and PII from screenshots |
| `/superbased:record` | Start, stop, or manage screen recording sessions |
| `/superbased:monitor` | Start proactive AI screen monitoring |
| `/superbased:sessions` | List recording sessions and view frames |
| `/superbased:diff` | Compare two recording sessions for visual regressions |
| `/superbased:baseline` | Manage visual regression testing baselines |
| `/superbased:export` | Export sessions as zip, markdown, PDF, HTML, or GIF |
| `/superbased:gallery` | Browse, search, and manage capture gallery |
| `/superbased:compress` | Compress text into token-efficient images |
| `/superbased:dictate` | Record from microphone and transcribe |
| `/superbased:transcribe` | Transcribe audio file to text (raw Whisper) |
| `/superbased:settings` | View or update app settings |
| `/superbased:presets` | Manage AI instruction presets |
| `/superbased:status` | Health, auth, and AI usage check |
| `/superbased:auth` | Authentication management |

## Agents (2)

| Agent | Description |
|-------|-------------|
| **visual-qa** | Record baselines, capture after changes, diff, annotate regressions, export reports |
| **monitor** | Watch screen for errors during deploys/tests, flag issues proactively, summarize findings |

## Hooks

**Post-test auto-capture:** After test commands (`npm test`, `jest`, `vitest`, `pytest`, `cargo test`, `go test`), SuperBased automatically captures a screenshot at quarter resolution.

## MCP Tools (28)

**Capture & View:** `superbased_capture`, `superbased_capture_image`, `superbased_clipboard`, `superbased_window_list`
**AI & OCR:** `superbased_ai`, `superbased_ai_usage`, `superbased_ocr`, `superbased_transcribe`, `superbased_compress_text`
**Gallery:** `superbased_gallery`, `superbased_gallery_update`, `superbased_gallery_image`
**Recording:** `superbased_recording`, `superbased_sessions`, `superbased_export`, `superbased_describe_frames`, `superbased_narrate`
**Visual Testing:** `superbased_diff`, `superbased_baseline`, `superbased_annotate`
**Dictation:** `superbased_dictate`, `superbased_dictation_history`
**Privacy:** `superbased_redact`
**Settings:** `superbased_settings`, `superbased_presets`
**Auth & System:** `superbased_auth`, `superbased_license`, `superbased_health`

## Links

- [SuperBased](https://superbased.app) — Desktop app download
- [npm package](https://www.npmjs.com/package/superbased) — Headless CLI
