---
name: vision
description: Analyze images and videos using Z.AI GLM-4.6V vision model via MCP. Use when the user sends an image or asks about image/video content, OCR, UI screenshots, error screenshots, diagrams, charts, or data visualizations. Triggers on "analyze this image", "what's in this picture", "read this screenshot", "describe this chart", "OCR", "圖片講咩", "認圖".
---

# Vision - Image & Video Analysis

Use `mcporter` to call the Z.AI Vision MCP Server for image and video understanding.

## Quick Start

```bash
mcporter call zai-vision.analyze_image image_source=/path/to/image.jpg prompt="Describe this image"
```

## Available Tools

| Tool | Use Case |
|------|----------|
| `analyze_image` | General image analysis (fallback for other tools) |
| `extract_text_from_screenshot` | OCR for code, terminals, docs, text |
| `diagnose_error_screenshot` | Analyze error messages and stack traces |
| `understand_technical_diagram` | Architecture, flowcharts, UML, ER diagrams |
| `analyze_data_visualization` | Charts, dashboards, data trends |
| `ui_to_artifact` | UI screenshot → code/prompt/spec/description |
| `ui_diff_check` | Compare two UI screenshots |
| `analyze_video` | Video understanding (≤8MB, MP4/MOV/M4V) |

## Usage Examples

**General image analysis:**
```bash
mcporter call zai-vision.analyze_image image_source=/path/to/img.jpg prompt="Describe in Cantonese"
```

**OCR screenshot:**
```bash
mcporter call zai-vision.extract_text_from_screenshot image_source=/path/to/screenshot.png prompt="Extract all text"
```

**Error diagnosis:**
```bash
mcporter call zai-vision.diagnose_error_screenshot image_source=/path/to/error.png prompt="What's wrong?"
```

**Chart analysis:**
```bash
mcporter call zai-vision.analyze_data_visualization image_source=/path/to/chart.png prompt="Summarize trends"
```

**Video analysis:**
```bash
mcporter call zai-vision.analyze_video video_source=/path/to/video.mp4 prompt="What happens in this video?"
```

## Notes

- Set `MCPORTER_CALL_TIMEOUT=120000` for longer processing
- Images received via Telegram are saved to `/root/.openclaw/media/inbound/`
- Respond in the user's preferred language (Cantonese for Bob)
