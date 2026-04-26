# SuperBased — Eyes AND Hands for Cursor

Screenshot capture, AI vision, OCR, screen recording, visual regression testing, token compression, voice dictation, proactive screen monitoring, **and full GUI automation with humanization v2** — all via 72 MCP tools, directly inside Cursor.

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

## Skills (11)

| Skill | When Cursor Uses It |
|-------|-------------------|
| **screenshot** | Cursor needs to see the screen to answer a question or verify a UI change |
| **visual-qa** | Visual regression testing: record baseline, make changes, record again, diff |
| **monitor** | Proactive screen watching during deploys, tests, or builds |
| **compress** | Large text content (>500 tokens) that would be cheaper as an image |
| **redact** | Screenshots that may contain API keys, tokens, or PII before sharing |
| **dictation** | User wants voice input, audio transcription, or speech-to-text |
| **annotate** | Highlighting areas, marking regressions, creating annotated screenshots |
| **walkthrough** | Multi-frame product walkthrough: capture, narrate, export |
| **gui-automation** | "Click that", "type into this", "fill the form" — drives the desktop with click/type/hotkey/scroll/drag/form-fill/sequence |
| **captcha-solving** | reCAPTCHA / Cloudflare Turnstile / drag puzzles / rotation puzzles / image grids |
| **humanization** | Sites with bot detection — picks the right humanization profile (off/light/human/paranoid) |

## Cursor Rules (4)

| Rule | Description |
|------|-------------|
| **superbased-capture** | When to use SuperBased for screen capture, window targeting, OCR |
| **superbased-privacy** | Redact sensitive info from screenshots before sharing |
| **superbased-recording** | Smart recording modes and visual regression testing workflow |
| **superbased-walkthrough** | Walking through scrollable sections with `superbased_scroll_capture` |

## Slash Commands (26)

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
| `/superbased:click` | Click an on-screen element by label or coordinates |
| `/superbased:form` | Fill a form by label/value pairs (`superbased_form_fill`) |
| `/superbased:record-gui` | Record a multi-step GUI workflow for replay |
| `/superbased:captcha` | Open the CAPTCHA-solving guidance (rotation puzzles, drag puzzles, image grids) |

## Agents (3)

| Agent | Description |
|-------|-------------|
| **visual-qa** | Record baselines, capture after changes, diff, annotate regressions, export reports |
| **monitor** | Watch screen for errors during deploys/tests, flag issues proactively, summarize findings |
| **gui-automation** | Orchestrate multi-step GUI workflows with `superbased_sequence` + the click/type/drag/scroll/form-fill primitives, with the safety checklist baked in |

## Hooks

**Post-test auto-capture:** After test commands (`npm test`, `jest`, `vitest`, `pytest`, `cargo test`, `go test`), SuperBased automatically captures a screenshot at quarter resolution.

## Humanization v2

GUI automation actions (`click`, `type`, `drag`, `hover`) ship with a humanization layer to reduce the bot-detection signal: sin-shaped velocity envelope on cursor walks, gaussian click-target jitter, gamma-distributed pre-click settle dwell, 50–110 ms click hold variation, 45–95 ms key hold, wired typo simulation with QWERTY same-row neighbors, pre-click tremor on the target element, occasional 2–4× micro-pauses, per-process cross-session salt mixed into seeds, inter-action catch-up pause, and opt-in idle cursor drift.

Four profiles selectable per call: `humanize: 'off' | 'light' | 'human' | 'paranoid'`. Default `light`. Bump to `human` or `paranoid` for sites with active bot detection — see the **humanization** skill.

## CAPTCHA solving

Plugin ships proactive guidance for the four CAPTCHA classes: image grids (vision identifies, batched click sequence), drag puzzles (one-motion drag with `humanize: 'light'`), rotation puzzles (calibrate-then-execute), and checkbox-only Turnstile. Plus the honest "what humanization can't defeat" list (server-side fingerprinting, audio CAPTCHAs, hCaptcha enterprise mode). See the **captcha-solving** skill.

## MCP Tools (72)

The plugin exposes all 72 SuperBased MCP tools across 9 categories: Capture & View (5), AI & OCR (8), Gallery (2), Privacy & Annotations (2), Dictation & Voice (2), Recording & Visual QA (7), Settings/Auth/System (6), and **GUI Automation (40)** — `_ui_dump`, `_scroll_capture`, `_scroll_to`, `_sequence`, `_click`, `_type`, `_hotkey`, `_scroll`, `_drag`, `_drag_file`, `_hover`, `_context_menu_select`, `_form_fill`, `_dialog_handle`, `_open_url`, `_find_in_page`, `_tab_management`, `_tray_click`, `_virtual_desktop`, `_window_state`, `_resize_window`, `_focus_window`, `_window_bounds`, `_find_title_bar_drag_region`, `_display_list`, `_launch_app`, `_find_image`, `_capture_template`, `_pixel_color`, `_ax_invoke`, `_accessibility_tree`, `_locate`, `_wait`, `_wait_for`, `_mouse_position`, `_dry_run`, `_replay`, `_doctor_gui_automation`, `_undo_last`, `_tools`.

See [the source-of-truth Claude Code plugin README](https://github.com/marmutapp/superbased-claude-code-plugin#mcp-tools-72) for the full categorized list with collapsibles.

## Links

- [SuperBased](https://superbased.app) — Desktop app download
- [npm package](https://www.npmjs.com/package/superbased) — Headless CLI
