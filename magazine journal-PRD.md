# Reflections — Product Requirements Document
**Version 1.0 · April 2026**

---

## 1. Product Vision

**Reflections** 是一款以杂志排版美学为核心的个人日记 PWA（渐进式 Web 应用），目标是将"记录日常"这件事本身变得赏心悦目、充满节奏感。

> **Core Proposition**: 不是功能最多的日记 app，而是用户最愿意每天打开的那一个。

**设计基调**：杂志风 (City Boy / POPEYE style)、清新自然、极简克制、有节奏感的排版，低饱和度自然色系。

---

## 2. Target Users

| 维度 | 描述 |
|---|---|
| 年龄 | 20–32 岁 |
| 画像 | 对美学有要求的城市年轻人；关注生活方式、音乐、设计 |
| 使用场景 | 睡前、咖啡馆、通勤后 |
| 核心痛点 | 传统日记 app 太功能化、不好看；坚持不下去 |
| 激励因素 | 视觉成就感、连续记录的仪式感、音乐情绪联动 |

---

## 3. Information Architecture

```
Reflections PWA
├── 首页 (Today) ─── 杂志封面式首屏，显示今日入口 + 模块卡片
├── 写作 (Write) ─── 杂志化编辑器，模板 + 图文混排 + 贴纸
├── 音乐 (Music) ─── 今日歌单 + 情绪标签 + 歌曲与条目关联
└── 档案 (Archive)── 历史条目 + 角色系统 + 奖杯 + 角色解锁
```

---

## 4. Core Features (MVP)

### 4.1 首页 — 杂志封面布局

**布局结构**
- 顶部：Logo + 期数/日期（仿杂志刊头）
- 主视觉卡片：占满宽度，黑底大字，今日入口 → 点击进入写作
- 双列模块卡：音乐模块 + 成就/Streak 模块
- Streak 条横幅：跨列，展示当周打卡状态

**交互细节**
- 右下角 FAB 按钮（悬浮操作按钮）→ 快速进入写作
- 日期自动更新，跨零点提示"新的一天已经开始"

---

### 4.2 写作模块 — Magazine Editor

**顶部操作栏**
- 左：← 返回（不保存）
- 中：条目标题（斜体衬线字）
- 右：Publish → （保存并发布）

**情绪选择**
- 5 个 emoji 选项（排成一行），点击激活，对应当天条目情绪 tag

**模板系统**

| 模板名 | 排版特点 |
|---|---|
| Editorial | 大标题 + 横线分割 + 图片 + 正文 + pullquote |
| Minimal | 纯文字，大号衬线体，留白充分 |
| Photo-led | 图片占主视觉，配短文字 |
| Quote | 全版引用式排版 |
| List | 条目化内容，适合 bullet journal 风格 |

**块元素（Block System）**
- Headline Block：Playfair Display，大号，可编辑
- Body Block：DM Sans Light，正文，可多段
- Image Block：点击选图/上传，自动裁切填满比例
- Pullquote Block：左线 + 斜体，适合摘出金句
- Divider：细线分割
- Two-Column Image：双图并排

**贴纸系统**
- 底部托盘，点击添加至编辑画布
- 贴纸可拖动定位（绝对定位）
- MVP 内置 20 枚贴纸（生活类：咖啡、植物、音乐、城市、天气等）

---

### 4.3 音乐模块

**功能**
- 展示当日"Now Playing"（手动设置或联动）
- 情绪 tag 标注（Chill / Melancholic / Energetic / Focused 等）
- 今日发现列表（手动添加歌曲）
- 播放进度条（演示用，非实际播放）

**Phase 2 扩展**
- Apple Music / 网易云音乐 API 对接
- 自动读取最近播放，一键附加到日记条目
- 每月"本月歌单"汇总

---

### 4.4 游戏化系统

#### Streak（连续打卡）
- 每天写 1 条 → +1 streak
- 首页 + 档案页展示当周打卡点（7 个圆点）
- 断掉归零，支持 1 次/月 "Freeze"（冻结续杯）

#### Trophy（奖杯）
| 奖杯 | 解锁条件 |
|---|---|
| First Page | 完成第 1 条 |
| 3-Day Strike | 连续 3 天 |
| 7-Day Strike | 连续 7 天 |
| 30-Day Strike | 连续 30 天 |
| Music Linker | 关联 5 首歌 |
| Photo Story | 完成 10 条 Photo-led 模板 |
| Deep Writer | 累计写超过 10,000 字 |

#### Character（角色系统）
- 默认角色：The City Wanderer（通用男生扁平风格）
- 解锁条件 → 角色替换首页/档案页展示

| 角色 | 解锁 |
|---|---|
| The Artist | 完成 10 条 Photo-led 条目 |
| The Music Head | 关联 20 首歌曲 |
| The Café Regular | 7 天连续 Streak |
| The Night Owl | 连续 5 天在午夜后写日记 |
| The Storyteller | 单条字数超过 1000 字，3 次 |

---

## 5. UI / UX Design Spec

### 5.1 色彩系统

| Token | Hex | 用途 |
|---|---|---|
| `--cream` | #F5F0E8 | 主背景，纸张感 |
| `--ink` | #1C1A16 | 主文字、深色背景 |
| `--sage` | #8A9E89 | 植物绿，次要元素 |
| `--terracotta` | #C4714A | Streak 高亮、活跃状态 |
| `--warm-gray` | #B8B0A4 | 辅助文字、分割线 |
| `--paper` | #FDFAF4 | 卡片背景，比 cream 更白 |
| `--charcoal` | #2E2C28 | 音乐模块深色背景 |

### 5.2 字体系统

| 层级 | 字体 | 用法 |
|---|---|---|
| Display | Playfair Display Italic | 标题、Logo、大标题 |
| Body | DM Sans Light/Regular | 正文、UI 文字 |
| Monospace | Space Mono | 日期、时间、数字 |
| Serif (Block) | DM Serif Display | Pullquote、特殊引用 |

### 5.3 间距规范
- 页面边距：1.5rem (24px)
- 组件内间距：1rem / 1.25rem
- 分割线：0.5px rgba(0,0,0,0.1)
- 圆角：0（保持杂志版块感，方角为主）

### 5.4 动效原则
- 页面切换：fadeIn 0.2s ease
- 交互反馈：hover opacity 0.7–0.9，active scale 0.97
- Toast 提示：fadeUp 0.3s，2 秒后消失
- 无多余动效，克制为先

---

## 6. Technical Architecture

### Stack（推荐 Codex 实现）

```
Frontend:  Next.js 14 (App Router) + TypeScript
Styling:   Tailwind CSS（自定义设计 token）
State:     Zustand（全局状态）+ localStorage（本地持久化）
Database:  Supabase（Postgres + Auth + Storage）
Deploy:    Vercel（一键部署）
Fonts:     Google Fonts（Playfair Display, DM Sans, Space Mono）
PWA:       next-pwa（离线支持，Add to Home Screen）
```

### Data Models

```typescript
// Entry（日记条目）
interface Entry {
  id: string
  date: string               // "2026-04-05"
  template: TemplateType     // 'editorial' | 'minimal' | 'photo' | 'quote' | 'list'
  mood: MoodType             // 'chill' | 'reflective' | 'melancholic' | 'glowing' | 'energetic'
  headline: string
  blocks: Block[]            // 混排块
  stickers: Sticker[]        // 贴纸位置信息
  musicTrack?: MusicTrack    // 关联歌曲
  wordCount: number
  createdAt: Date
  updatedAt: Date
}

// Block（内容块）
interface Block {
  id: string
  type: 'headline' | 'body' | 'image' | 'pullquote' | 'divider' | 'twocol'
  content: string
  imageUrl?: string
}

// Sticker
interface Sticker {
  emoji: string
  x: number   // percentage of canvas width
  y: number   // absolute px from top
  rotation: number
}

// UserProfile
interface UserProfile {
  id: string
  streak: number
  lastEntryDate: string
  trophies: string[]         // trophy IDs earned
  currentCharacter: string   // character ID
  totalEntries: number
  totalWords: number
  xp: number
}
```

---

## 7. File Structure (Next.js)

```
reflections/
├── app/
│   ├── page.tsx            # Splash / Today page
│   ├── write/
│   │   └── page.tsx        # Magazine Editor
│   ├── music/
│   │   └── page.tsx        # Music module
│   └── archive/
│       └── page.tsx        # Achievements + history
├── components/
│   ├── MagazineEditor/
│   │   ├── BlockRenderer.tsx
│   │   ├── StickerTray.tsx
│   │   └── TemplateSelector.tsx
│   ├── HomeCard/
│   ├── MusicPlayer/
│   ├── CharacterStage/
│   └── StreakBar/
├── store/
│   ├── useEntryStore.ts
│   └── useUserStore.ts
├── lib/
│   ├── supabase.ts
│   └── achievements.ts     # Trophy logic
├── styles/
│   └── globals.css         # Design tokens
└── public/
    └── manifest.json       # PWA manifest
```

---

## 8. MVP Scope (Phase 1)

### 包含 ✅
- 首页（杂志封面布局）
- 写作编辑器（Editorial 模板完整）
- 情绪选择
- 贴纸（点击添加 + 拖动）
- 本地 Streak 计数
- 奖杯展示（3 种解锁）
- 角色预览（3 个角色）
- 音乐模块（手动输入歌曲信息）
- Vercel 部署 + PWA 基础

### 不包含 ❌（Phase 2）
- 音乐平台 API 对接（Apple Music / 网易云）
- 云同步（Supabase Auth + DB）
- 图片上传到云存储
- 多模板（Minimal, Photo-led, Quote, List）
- 贴纸拖动位置持久化
- 分享功能（生成分享图）

---

## 9. Deployment Checklist (Vercel)

```bash
# 1. Init project
npx create-next-app@latest reflections --typescript --tailwind --app

# 2. Install dependencies
npm install zustand next-pwa @supabase/supabase-js

# 3. Configure tailwind.config.ts
# Add custom colors, fonts

# 4. Deploy
vercel deploy

# 5. PWA
# Add next.config.js withPWA wrapper
# Add public/manifest.json
# Add apple-touch-icon
```

**Vercel 环境变量**
```
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
```

---

## 10. Success Metrics (Personal Use)

| 指标 | 目标 |
|---|---|
| 日均使用频率 | ≥ 1 次/天 |
| 平均停留时长 | ≥ 3 分钟 |
| 30 天后 Streak | ≥ 14 天 |
| 主观满意度 | "我真的愿意每天打开它" |

---

*Reflections PRD v1.0 · Built for personal use · Powered by vibes and caffeine ☕*
