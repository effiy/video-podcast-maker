---
title: "kinetic-typography — bold type-driven video preset"
tags: [remotion, typography, animation, preset, video-podcast]
category: "projects/video-podcast-maker/skills/templates/presets/kinetic-typography"
created: "2026-10-20"
updated: "2026-10-20"
source: "external"
type: "index"
status: "stable"
lifecycle: "active"
---

# Kinetic Typography Preset

💡 概述

A bold, type-driven preset: black-ish background, oversized Chinese typography, two-color accent system, character-pop and marker-reveal animations, ambient particle/glow background. No card layouts, no icons in body -- text is the visual.

---

⚡ 功能

When to use:
- Topic is opinion / argument / declaration (not a tutorial or product walkthrough)
- Script is naturally short-sentence, punch-line driven
- You want a distinctive look that breaks out of the standard card-based design
- Audience is younger / video-platform-native (Bilibili, Douyin, TikTok)
- Each beat conveys a single idea in 1-3 short lines

When NOT to use:
- Technical tutorials with code blocks, screenshots, diagrams
- Product comparisons with feature tables
- Long explanations needing detailed visual support
- News-anchor-style narration with B-roll
- Stories with characters, settings, scenes

---

📊 指标

Files:

| File | Purpose |
|------|---------|
| `Video.tsx.template` | Main composition with KineticBeat + ParticleField + GlowOrbs + VerticalDecor |
| `Thumbnail.tsx.template` | Black BG + huge white title + mint marker subtitle |
| `colors.json` | Recommended palette + variants |
| `voice.json` | Recommended TTS settings |
| `motion.json` | Animation timing constants (entrance/exit, character delays) |

---

🏛️ 设计

Design rules specific to this preset:
- Background: dark navy `#08091A` (NOT pure black)
- Two accent colours: mint `#5EEAD4` for primary punch, yellow `#FACC15` for warnings/numbers/contrast
- Typography: 100-280px range, most beats have small line + HUGE punch line (3-4x size delta)
- Marker style: secondary lines use `marker: true` for skewed mint/yellow handwritten-feel reveal
- No flash strobe -- soft pulses only
- Side decor: persistent vertical-rl chapter markers and topic tag on left/right edges
- One concept per beat -- never cram 4+ lines

Common mistakes:
- Using weight-based beat distribution -> drift. Always use SRT-derived `startSec`
- Cramming long sentences into one beat -> text feels stuck while narrator finishes
- Skipping middle narration concepts -> visual freezes for 5+ seconds
- Using Multilingual voice for AI-heavy scripts -> vocoder artifacts
- Reusing same beat variant for entire section -> monotonous

---

📁 目录

「待补充」

---

🔗 资源

---

🚀 快速开始

1. Plan script as 8-15 short punch lines per section
2. Generate TTS first:

   ```bash
   TTS_VOICE=zh-CN-XiaoxiaoNeural TTS_STYLE="" TTS_RATE=+5% \
     python3 ${SKILL_DIR}/scripts/generate_tts.py \
     -i videos/{name}/podcast.txt -o videos/{name}/
   ```

3. Copy templates:

   ```bash
   cp ${SKILL_DIR}/templates/presets/kinetic-typography/Video.tsx.template \
      src/remotion/{Name}Video.tsx
   cp ${SKILL_DIR}/templates/presets/kinetic-typography/Thumbnail.tsx.template \
      src/remotion/{Name}Thumbnail.tsx
   ```

4. Use SRT timestamps as beat startSec
5. Audit alignment:

   ```bash
   python3 ${SKILL_DIR}/scripts/audit_beat_sync.py \
     src/remotion/{Name}Video.tsx \
     videos/{name}/timing.json
   ```

6. Studio preview, then render 4K

---

⚙️ 技术栈

| 技术 | 用途 |
|------|------|
| Remotion | Video rendering |
| React/TypeScript | Composition |
| edge-tts | Chinese TTS |