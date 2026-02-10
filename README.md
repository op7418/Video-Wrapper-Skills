<div align="center">

# 🎬 Video Wrapper

**Add Variety Show Style Visual Effects to Interview/Podcast Videos**

AI-powered subtitle analysis, automatic effect suggestions, one-click professional visual rendering

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Claude Skills](https://img.shields.io/badge/Claude-Skills-blueviolet.svg)](https://claude.ai)

[Quick Start](#-quick-start) • [Features](#-features) • [Demo](#-demo) • [Use Cases](#-use-cases) • [Architecture](./ARCHITECTURE.md)

[中文文档](./README_CN.md)

</div>

---

## ✨ Features

<table>
<tr>
<td width="50%">

### 🎨 8 Visual Components
- **Key Phrases** - Short phrases highlighting core ideas
- **Lower Thirds** - Display guest name and title
- **Chapter Titles** - Topic transition title cards
- **Term Cards** - Professional terminology explanations
- **Quote Callouts** - Highlight memorable quotes
- **Animated Stats** - Dynamic number displays
- **Bullet Points** - Core takeaways summary
- **Social Bars** - Follow call-to-action

</td>
<td width="50%">

### 🎭 4 Visual Themes
- **Notion** 🟡 - Warm knowledge style
- **Cyberpunk** 💜 - Neon futuristic
- **Apple** ⚪ - Minimalist business
- **Aurora** 🌈 - Gradient flowing

### 🤖 Smart Workflow
1. 📝 AI analyzes subtitle content
2. 💡 Auto-generates effect suggestions
3. ✅ User approves configuration
4. 🎬 One-click video rendering

</td>
</tr>
</table>

### 🛠️ Dual Rendering Engines

| Engine | Tech Stack | Features |
|--------|-----------|----------|
| **Browser** 🌐 | Playwright + HTML/CSS/Anime.js | High quality, complex animations (Recommended) |
| **PIL** 🎨 | Python PIL | Pure Python, no browser required |

---

## 🚀 Quick Start

### Installation

**Method 1: One-Click Install (Recommended)**

```bash
npx skills add https://github.com/op7418/Video-Wrapper-Skills
```

**Method 2: Manual Install**

```bash
# Clone to Claude Skills directory
cd ~/.claude/skills/
git clone https://github.com/op7418/Video-Wrapper-Skills.git video-wrapper
cd video-wrapper

# Install dependencies
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
playwright install chromium
```

### Usage

**In Claude Code**

```bash
/video-wrapper interview.mp4 subtitles.srt
```

Claude will:
1. 📊 Analyze subtitles, identify key information
2. 💡 Generate effect suggestions (lower thirds, key phrases, term cards, etc.)
3. 📝 Present suggestions in Markdown for review
4. ✅ Auto-render output video after confirmation

**Command Line**

```bash
# Direct rendering with config file
python src/video_processor.py video.mp4 subs.srt config.json output.mp4

# Specify renderer
python src/video_processor.py video.mp4 subs.srt config.json -r browser  # Browser
python src/video_processor.py video.mp4 subs.srt config.json -r pil      # PIL
```

---

## 🎥 Demo

> 💡 Visual effects showcase across different themes and components

### Theme Comparison

<table>
<tr>
<td align="center" width="25%"><strong>Notion Theme</strong><br/>Warm Knowledge</td>
<td align="center" width="25%"><strong>Cyberpunk Theme</strong><br/>Neon Futuristic</td>
<td align="center" width="25%"><strong>Apple Theme</strong><br/>Minimalist Elegant</td>
<td align="center" width="25%"><strong>Aurora Theme</strong><br/>Gradient Flow</td>
</tr>
<tr>
<td align="center">🟡 Education/Knowledge</td>
<td align="center">💜 Tech/Innovation</td>
<td align="center">⚪ Business/Professional</td>
<td align="center">🌈 Creative/Artistic</td>
</tr>
</table>

### Component Examples

| Component | Preview | Use Case |
|-----------|---------|----------|
| 🏷️ **Key Phrase** | _[Preview placeholder]_ | When guest mentions "Artificial General Intelligence", show "AI Development is Smooth Curve" |
| 👤 **Lower Third** | _[Preview placeholder]_ | Show "Dario Amodei · CEO · Anthropic" at video start |
| 📖 **Term Card** | _[Preview placeholder]_ | Auto popup explanation when "Moore's Law" first mentioned |
| 💬 **Quote** | _[Preview placeholder]_ | Highlight "AI development is a very smooth exponential curve" |

---

## 📋 Use Cases

<table>
<tr>
<td width="33%">

### 🎓 Educational Content
- Knowledge sharing videos
- Course recordings
- Online lectures
- Heavy terminology needs

</td>
<td width="33%">

### 🎙️ Interviews & Podcasts
- Personal interviews
- Panel discussions
- Industry dialogues
- Guest info display needs

</td>
<td width="33%">

### 📱 Social Media
- YouTube long-form
- B站 content
- Podcast shows
- Highlight clips needed

</td>
</tr>
</table>

---

## 🎨 Theme System

Choose the right theme based on content style:

```json
{
  "theme": "notion"  // or "cyberpunk", "apple", "aurora"
}
```

| Theme | Color Scheme | Characteristics | Best For |
|-------|--------------|----------------|----------|
| **Notion** | Warm Yellow + Blue | Soft gradients, knowledge-focused | Education, knowledge sharing, courses |
| **Cyberpunk** | Neon Purple + Cyan | High contrast, tech-forward | Tech, sci-fi, innovation topics |
| **Apple** | Black/White/Gray | Minimal, professional | Business, corporate, formal interviews |
| **Aurora** | Rainbow Gradient | Flowing light, artistic | Creative, design, artistic content |

---

## 🧩 Component Configuration

### Complete Configuration Example

<details>
<summary>Expand to view full JSON config</summary>

```json
{
  "theme": "notion",

  "lowerThirds": [
    {
      "name": "John Doe",
      "role": "Chief Scientist",
      "company": "AI Research Lab",
      "startMs": 1000,
      "durationMs": 5000
    }
  ],

  "chapterTitles": [
    {
      "number": "Part 1",
      "title": "The Journey of AI",
      "subtitle": "The History of AI Development",
      "startMs": 0,
      "durationMs": 4000
    }
  ],

  "keyPhrases": [
    {
      "text": "AI Development is Smooth Curve",
      "style": "emphasis",
      "startMs": 2630,
      "endMs": 5500
    }
  ],

  "termDefinitions": [
    {
      "chinese": "摩尔定律",
      "english": "Moore's Law",
      "description": "Number of transistors doubles every 18-24 months",
      "firstAppearanceMs": 37550,
      "displayDurationSeconds": 6
    }
  ],

  "quotes": [
    {
      "text": "AI development is a very smooth exponential curve",
      "author": "— John Doe",
      "startMs": 30000,
      "durationMs": 5000
    }
  ],

  "stats": [
    {
      "prefix": "Growth Rate ",
      "number": 240,
      "unit": "%",
      "label": "Annual Computing Power Growth",
      "startMs": 45000,
      "durationMs": 4000
    }
  ],

  "bulletPoints": [
    {
      "title": "Key Takeaways",
      "points": [
        "AI development is smooth exponential curve",
        "Similar to Moore's Law intelligence growth",
        "No sudden singularity moment"
      ],
      "startMs": 50000,
      "durationMs": 6000
    }
  ],

  "socialBars": [
    {
      "platform": "twitter",
      "label": "Follow us",
      "handle": "@ai_research",
      "startMs": 52000,
      "durationMs": 8000
    }
  ]
}
```

</details>

### Component Parameters Quick Reference

| Component | Required | Optional | Notes |
|-----------|----------|----------|-------|
| Lower Third | name, role, company, startMs | durationMs (default 5s) | Guest information |
| Chapter Title | number, title, startMs | subtitle, durationMs | Topic segmentation |
| Key Phrase | text, startMs, endMs | style, position | **text must be phrase** |
| Term Card | chinese, english, firstAppearanceMs | description, displayDurationSeconds | Terminology explanation |
| Quote | text, author, startMs | durationMs, position | Memorable quotes |
| Stats | number, label, startMs | prefix, unit, durationMs | Number display |
| Bullet Points | title, points, startMs | durationMs | List summary |
| Social Bar | platform, handle, startMs | label, durationMs | Follow CTA |

> ⚠️ **Key Phrase Usage**: text must be a phrase (e.g., "AI Development is Smooth Curve"), not a single word (e.g., "Artificial Intelligence"). Use term cards for single words.

---

## 🗂️ Project Structure

```
video-wrapper/
├── 📄 SKILL.md                  # Claude Skill definition
├── 📄 README.md                 # This document (English)
├── 📄 README_CN.md              # Chinese documentation
├── 📄 ARCHITECTURE.md           # Detailed architecture
├── 📄 requirements.txt          # Python dependencies
├── 📁 src/                      # Source code
│   ├── video_processor.py       # Main processing flow
│   ├── browser_renderer.py      # Playwright renderer
│   ├── content_analyzer.py      # AI content analysis
│   ├── fancy_text.py            # PIL key phrase rendering
│   ├── term_card.py             # PIL card rendering
│   └── animations.py            # Animation functions
├── 📁 templates/                # HTML templates
│   ├── fancy-text.html
│   ├── term-card.html
│   ├── lower-third.html
│   ├── chapter-title.html
│   ├── quote-callout.html
│   ├── animated-stats.html
│   ├── bullet-points.html
│   ├── social-bar.html
│   └── video-config.json.template
└── 📁 static/                   # Static assets
    ├── css/                     # Theme styles
    │   ├── effects.css
    │   ├── theme-notion.css
    │   ├── theme-cyberpunk.css
    │   ├── theme-apple.css
    │   └── theme-aurora.css
    └── js/
        └── anime.min.js         # Animation engine
```

---

## ❓ FAQ

<details>
<summary><strong>Q: Playwright installation failed?</strong></summary>

```bash
# Ensure Python version >= 3.8
pip install playwright
playwright install chromium

# macOS may need to remove quarantine flag
xattr -r -d com.apple.quarantine ~/.cache/ms-playwright

# Verify installation
playwright --version
```

</details>

<details>
<summary><strong>Q: Processing too slow?</strong></summary>

**Optimization Tips**:
1. Use PIL renderer: `-r pil` (simpler but 2-3x faster)
2. Lower video resolution (1080p → 720p)
3. Process long videos in segments (5-10 min chunks)
4. Reduce component count (keep only essentials)

</details>

<details>
<summary><strong>Q: Out of memory?</strong></summary>

**Solutions**:
1. Close other applications to free memory
2. Process long videos in segments
3. Use lower resolution (720p or 480p)
4. Reduce number of simultaneous components
5. Use PIL renderer (smaller memory footprint)

</details>

<details>
<summary><strong>Q: Font display issues?</strong></summary>

Ensure Chinese fonts are installed:

```bash
# macOS - PingFang SC included
# No additional installation needed

# Ubuntu/Debian
sudo apt-get install fonts-noto-cjk

# CentOS/RHEL
sudo yum install google-noto-sans-cjk-fonts

# Verify fonts
fc-list :lang=zh
```

</details>

<details>
<summary><strong>Q: How to customize themes?</strong></summary>

1. Copy existing theme CSS file
2. Modify CSS variables
3. Specify new theme name in config

See [ARCHITECTURE.md](./ARCHITECTURE.md#adding-new-themes) for details

</details>

---

## 🔧 Tech Stack

| Layer | Technology | Description |
|-------|-----------|-------------|
| **Visual Rendering** | HTML + CSS + Anime.js | Screenshot via Playwright browser |
| **Video Compositing** | MoviePy | Python video editing library |
| **Animation Engine** | Anime.js | Spring physics animations |
| **Fallback Rendering** | Python PIL | Pure Python image processing |
| **Content Analysis** | AI Analysis | Auto-identify key information |

Detailed architecture available in [ARCHITECTURE.md](./ARCHITECTURE.md)

---

## 📚 Resources

- [Claude Skills Documentation](https://docs.anthropic.com/claude/docs)
- [MoviePy Documentation](https://zulko.github.io/moviepy/)
- [Playwright Documentation](https://playwright.dev/python/)
- [Anime.js Documentation](https://animejs.com/)

---

## 🤝 Contributing

Issues and Pull Requests are welcome!

Before submitting a PR, please ensure:
- ✅ Code style follows project conventions
- ✅ Added necessary tests
- ✅ Updated relevant documentation

---

## 📄 License

[MIT License](./LICENSE)

---

<div align="center">

**Powered by [Claude](https://claude.ai)**

If you find this useful, please give it a ⭐️ Star!

</div>
