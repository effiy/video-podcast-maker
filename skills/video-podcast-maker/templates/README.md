---
title: "templates — Remotion video project templates"
tags: [remotion, templates, video-podcast, components]
category: "projects/video-podcast-maker/skills/templates"
created: "2026-10-20"
updated: "2026-10-20"
source: "external"
type: "index"
status: "stable"
lifecycle: "active"
---

# Templates

💡 概述

Template files for creating Remotion video projects. Copy them to your project directory.

---

⚡ 功能

Template files split into two groups with different copy semantics:

1. **Shared scaffolding** (`Root.tsx`, `Thumbnail.tsx`, `components/`) -- copied once per Remotion project. Edit in place; never overwrite when adding new videos.
2. **Per-video composition** (`Video.tsx`) -- copied as `{PascalCaseName}Video.tsx` for each video.

Files:

| File | Purpose |
|------|---------|
| `podcast.txt` | Script template with `[SECTION:xxx]` markers |
| `Video.tsx` | Main video composition (imports from components/) |
| `Root.tsx` | Remotion root with Composition and Still registrations |
| `Thumbnail.tsx` | Thumbnail component (white centered, 16:9 + 4:3) |
| `components/` | Reusable visual building blocks |

---

📊 指标

Component Library:

| Component | Purpose |
|-----------|---------|
| `ComparisonCard` | Two-column VS layout for product/feature comparisons |
| `Timeline` | Vertical timeline with connected nodes for history/steps |
| `CodeBlock` | Dark terminal-style code display with title bar |
| `QuoteBlock` | Large centered quote with attribution |
| `FeatureGrid` | 2-3 column grid of icon + title + description cards |
| `DataBar` | Horizontal bar chart for data comparison |
| `ChapterProgressBar` | Bottom progress bar with chapter indicators |
| `Scale4K` | 4K scaling wrapper (design at 1080p, render at 4K) |
| `FullBleedLayout` | Full-screen layout without padding |
| `PaddedLayout` | Standard layout with 40px padding |
| `useEntrance` | Spring-based entrance animation hook |
| `getPresentation` | Transition type mapper (fade/slide/wipe/none) |

---

🏛️ 设计

Import via barrel export:

```tsx
import { ComparisonCard, Timeline, CodeBlock, QuoteBlock, FeatureGrid, DataBar } from "./components";
```

---

📁 目录

「待补充」

---

🔗 资源

Never overwrite shared files (`Root.tsx`, `Thumbnail.tsx`, `components/`) when adding a second/third video to an existing project -- you'd lose registrations and edits from earlier videos.

---

🚀 快速开始

```bash
# Resolve skill directory
export SKILL_DIR="${SKILL_DIR:-${CLAUDE_SKILL_DIR}}"

# First time only (per project) -- copy shared scaffolding
cp "${SKILL_DIR}"/templates/Root.tsx       src/remotion/Root.tsx
cp "${SKILL_DIR}"/templates/Thumbnail.tsx  src/remotion/Thumbnail.tsx
cp "${SKILL_DIR}"/templates/ShortVideo.tsx src/remotion/ShortVideo.tsx
cp -r "${SKILL_DIR}"/templates/components  src/remotion/components

# Each new video -- copy per-video files
cp "${SKILL_DIR}"/templates/podcast.txt    videos/{name}/podcast.txt
cp "${SKILL_DIR}"/templates/Video.tsx      src/remotion/{PascalCase}Video.tsx
```

---

⚙️ 技术栈

| 技术 | 用途 |
|------|------|
| Remotion | Video rendering |
| React/TypeScript | Component development |
| Node.js 18+ | Runtime |