<div align="center">

# 🎬 Video Wrapper

**为访谈/播客视频添加综艺风格视觉包装**

AI 智能分析字幕内容，自动生成特效建议，一键渲染专业级视觉效果

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Claude Skills](https://img.shields.io/badge/Claude-Skills-blueviolet.svg)](https://claude.ai)

[快速开始](#-快速开始) • [功能特性](#-功能特性) • [效果展示](#-效果展示) • [使用场景](#-使用场景) • [架构文档](./ARCHITECTURE.md)

[English Documentation](./README.md)

</div>

---

## ✨ 功能特性

<table>
<tr>
<td width="50%">

### 🎨 8 种视觉组件
- **花字高亮** - 短语概括核心观点
- **人物条** - 显示嘉宾姓名职位
- **章节标题** - 话题切换标题卡
- **名词卡片** - 专业术语解释
- **金句卡片** - 精彩言论突出
- **数据动画** - 数字动态展示
- **要点列表** - 核心观点总结
- **社交条** - 关注引导信息

</td>
<td width="50%">

### 🎭 4 种视觉主题
- **Notion** 🟡 - 温暖知识风格
- **Cyberpunk** 💜 - 霓虹未来感
- **Apple** ⚪ - 极简商务风格
- **Aurora** 🌈 - 渐变流光效果

### 🤖 智能工作流
1. 📝 AI 分析字幕内容
2. 💡 自动生成特效建议
3. ✅ 用户审批确认
4. 🎬 一键渲染视频

</td>
</tr>
</table>

### 🛠️ 双渲染引擎

| 引擎 | 技术栈 | 特点 |
|------|--------|------|
| **Browser** 🌐 | Playwright + HTML/CSS/Anime.js | 高质量，支持复杂动画（推荐） |
| **PIL** 🎨 | Python PIL | 纯 Python，无需浏览器 |

---

## 🚀 快速开始

### 安装 Skill

**方式一：一键安装（推荐）**

```bash
npx skills add https://github.com/op7418/Video-Wrapper-Skills
```

**方式二：手动安装**

```bash
# 克隆到 Claude Skills 目录
cd ~/.claude/skills/
git clone https://github.com/op7418/Video-Wrapper-Skills.git video-wrapper
cd video-wrapper

# 安装依赖
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
playwright install chromium
```

### 使用

**在 Claude Code 中**

```bash
/video-wrapper interview.mp4 subtitles.srt
```

Claude 会：
1. 📊 分析字幕，识别关键信息
2. 💡 生成特效建议（人物条、花字、名词卡片等）
3. 📝 展示 Markdown 格式建议供审批
4. ✅ 确认后自动渲染输出视频

**命令行使用**

```bash
# 有配置文件时直接渲染
python src/video_processor.py video.mp4 subs.srt config.json output.mp4

# 指定渲染器
python src/video_processor.py video.mp4 subs.srt config.json -r browser  # 浏览器渲染
python src/video_processor.py video.mp4 subs.srt config.json -r pil      # PIL 渲染
```

---

## 🎥 效果展示

> 💡 以下展示不同主题和组件的视觉效果

### 主题风格对比

<table>
<tr>
<td align="center" width="25%"><strong>Notion 主题</strong><br/>温暖知识风</td>
<td align="center" width="25%"><strong>Cyberpunk 主题</strong><br/>霓虹未来感</td>
<td align="center" width="25%"><strong>Apple 主题</strong><br/>极简优雅</td>
<td align="center" width="25%"><strong>Aurora 主题</strong><br/>渐变流光</td>
</tr>
<tr>
<td align="center">🟡 教育/知识分享</td>
<td align="center">💜 科技/前沿话题</td>
<td align="center">⚪ 商务/专业访谈</td>
<td align="center">🌈 创意/艺术内容</td>
</tr>
</table>

### 组件效果示例

| 组件 | 效果预览 | 使用场景 |
|------|---------|----------|
| 🏷️ **花字** | _[效果图占位]_ | 嘉宾说到"通用人工智能"时，屏幕上方显示"AI发展是平滑曲线" |
| 👤 **人物条** | _[效果图占位]_ | 视频开始时展示"Dario Amodei · CEO · Anthropic" |
| 📖 **名词卡片** | _[效果图占位]_ | 首次提到"摩尔定律"时，自动弹出解释卡片 |
| 💬 **金句** | _[效果图占位]_ | 精彩观点"AI的发展是一个非常平滑的指数曲线"突出显示 |

---

## 📋 使用场景

<table>
<tr>
<td width="33%">

### 🎓 教育内容
- 知识分享视频
- 课程录制
- 在线讲座
- 术语解释需求多

</td>
<td width="33%">

### 🎙️ 访谈播客
- 人物专访
- 圆桌讨论
- 行业对话
- 需要嘉宾信息展示

</td>
<td width="33%">

### 📱 社交媒体
- YouTube 长视频
- B站 UP主内容
- 播客节目
- 需要精彩片段突出

</td>
</tr>
</table>

---

## 🎨 主题系统

根据内容风格选择合适主题：

```json
{
  "theme": "notion"  // 或 "cyberpunk", "apple", "aurora"
}
```

| 主题 | 色系 | 特点 | 适用内容 |
|------|------|------|----------|
| **Notion** | 暖黄 + 蓝色 | 柔和渐变，知识感 | 教育、知识分享、课程 |
| **Cyberpunk** | 霓虹紫 + 青色 | 高对比，科技感 | 技术、科幻、前沿话题 |
| **Apple** | 黑白灰 | 极简，专业感 | 商务、企业、正式访谈 |
| **Aurora** | 渐变彩虹 | 流光溢彩，艺术感 | 创意、设计、艺术内容 |

---

## 🧩 组件配置

### 完整配置示例

<details>
<summary>展开查看完整 JSON 配置</summary>

```json
{
  "theme": "notion",

  "lowerThirds": [
    {
      "name": "张三",
      "role": "首席科学家",
      "company": "AI 研究院",
      "startMs": 1000,
      "durationMs": 5000
    }
  ],

  "chapterTitles": [
    {
      "number": "Part 1",
      "title": "AI 的发展历程",
      "subtitle": "The History of AI Development",
      "startMs": 0,
      "durationMs": 4000
    }
  ],

  "keyPhrases": [
    {
      "text": "AI 发展是平滑曲线",
      "style": "emphasis",
      "startMs": 2630,
      "endMs": 5500
    }
  ],

  "termDefinitions": [
    {
      "chinese": "摩尔定律",
      "english": "Moore's Law",
      "description": "集成电路晶体管数量每18-24个月翻一番",
      "firstAppearanceMs": 37550,
      "displayDurationSeconds": 6
    }
  ],

  "quotes": [
    {
      "text": "AI 的发展是一个非常平滑的指数曲线",
      "author": "— 张三",
      "startMs": 30000,
      "durationMs": 5000
    }
  ],

  "stats": [
    {
      "prefix": "增长率 ",
      "number": 240,
      "unit": "%",
      "label": "计算能力年增长",
      "startMs": 45000,
      "durationMs": 4000
    }
  ],

  "bulletPoints": [
    {
      "title": "核心观点",
      "points": [
        "AI 发展是平滑的指数曲线",
        "类似摩尔定律的智能增长",
        "没有突然的奇点时刻"
      ],
      "startMs": 50000,
      "durationMs": 6000
    }
  ],

  "socialBars": [
    {
      "platform": "twitter",
      "label": "关注我们",
      "handle": "@ai_research",
      "startMs": 52000,
      "durationMs": 8000
    }
  ]
}
```

</details>

### 组件参数速查

| 组件 | 必需参数 | 可选参数 | 说明 |
|------|---------|---------|------|
| 人物条 | name, role, company, startMs | durationMs (默认5s) | 显示嘉宾信息 |
| 章节标题 | number, title, startMs | subtitle, durationMs | 话题分段 |
| 花字 | text, startMs, endMs | style, position | **text 必须是短语** |
| 名词卡片 | chinese, english, firstAppearanceMs | description, displayDurationSeconds | 术语解释 |
| 金句 | text, author, startMs | durationMs, position | 精彩观点 |
| 数据 | number, label, startMs | prefix, unit, durationMs | 数字展示 |
| 要点 | title, points, startMs | durationMs | 列表总结 |
| 社交条 | platform, handle, startMs | label, durationMs | 关注引导 |

> ⚠️ **花字使用规范**：text 必须是短语（如"AI发展是平滑曲线"），不能是单词（如"人工智能"）。单词应使用名词卡片。

---

## 🗂️ 项目结构

```
video-wrapper/
├── 📄 SKILL.md                  # Claude Skill 定义
├── 📄 README.md                 # 英文文档（GitHub 首页）
├── 📄 README_CN.md              # 本文档（中文）
├── 📄 ARCHITECTURE.md           # 详细架构说明
├── 📄 requirements.txt          # Python 依赖
├── 📁 src/                      # 源代码
│   ├── video_processor.py       # 主处理流程
│   ├── browser_renderer.py      # Playwright 渲染器
│   ├── content_analyzer.py      # AI 内容分析
│   ├── fancy_text.py            # PIL 花字渲染
│   ├── term_card.py             # PIL 卡片渲染
│   └── animations.py            # 动画函数库
├── 📁 templates/                # HTML 模板
│   ├── fancy-text.html
│   ├── term-card.html
│   ├── lower-third.html
│   ├── chapter-title.html
│   ├── quote-callout.html
│   ├── animated-stats.html
│   ├── bullet-points.html
│   ├── social-bar.html
│   └── video-config.json.template
└── 📁 static/                   # 静态资源
    ├── css/                     # 主题样式
    │   ├── effects.css
    │   ├── theme-notion.css
    │   ├── theme-cyberpunk.css
    │   ├── theme-apple.css
    │   └── theme-aurora.css
    └── js/
        └── anime.min.js         # 动画引擎
```

---

## ❓ 常见问题

<details>
<summary><strong>Q: Playwright 安装失败？</strong></summary>

```bash
# 确保 Python 版本 >= 3.8
pip install playwright
playwright install chromium

# macOS 可能需要移除隔离标记
xattr -r -d com.apple.quarantine ~/.cache/ms-playwright

# 验证安装
playwright --version
```

</details>

<details>
<summary><strong>Q: 处理速度太慢？</strong></summary>

**优化建议**：
1. 使用 PIL 渲染器：`-r pil`（效果略简单但速度快 2-3 倍）
2. 降低视频分辨率（从 1080p 降至 720p）
3. 分段处理长视频（每次处理 5-10 分钟）
4. 减少组件数量（只保留必要的）

</details>

<details>
<summary><strong>Q: 内存不足？</strong></summary>

**解决方案**：
1. 关闭其他应用释放内存
2. 分段处理长视频
3. 使用更低的分辨率（720p 或 480p）
4. 减少同时渲染的组件数量
5. 使用 PIL 渲染器（内存占用更小）

</details>

<details>
<summary><strong>Q: 字体显示异常？</strong></summary>

确保系统已安装中文字体：

```bash
# macOS - 自带 PingFang SC
# 无需额外安装

# Ubuntu/Debian
sudo apt-get install fonts-noto-cjk

# CentOS/RHEL
sudo yum install google-noto-sans-cjk-fonts

# 验证字体
fc-list :lang=zh
```

</details>

<details>
<summary><strong>Q: 如何自定义主题？</strong></summary>

1. 复制现有主题 CSS 文件
2. 修改 CSS 变量
3. 在配置中指定新主题名

详见 [ARCHITECTURE.md](./ARCHITECTURE.md#添加新主题)

</details>

---

## 🔧 技术栈

| 层级 | 技术 | 说明 |
|------|------|------|
| **视觉渲染** | HTML + CSS + Anime.js | 通过 Playwright 浏览器截图 |
| **视频合成** | MoviePy | Python 视频编辑库 |
| **动画引擎** | Anime.js | Spring 物理动画 |
| **备用渲染** | Python PIL | 纯 Python 图像处理 |
| **内容分析** | AI 分析 | 自动识别关键信息 |

详细架构说明请查看 [ARCHITECTURE.md](./ARCHITECTURE.md)

---

## 📚 相关资源

- [Claude Skills 文档](https://docs.anthropic.com/claude/docs)
- [MoviePy 文档](https://zulko.github.io/moviepy/)
- [Playwright 文档](https://playwright.dev/python/)
- [Anime.js 文档](https://animejs.com/)

---

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

在提交 PR 前，请确保：
- ✅ 代码风格符合项目规范
- ✅ 添加了必要的测试
- ✅ 更新了相关文档

---

## 📄 许可证

[MIT License](./LICENSE)

---

<div align="center">

**由 [Claude](https://claude.ai) 强力驱动**

如果觉得有用，请给个 ⭐️ Star！

</div>
