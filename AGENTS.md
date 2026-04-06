# AGENTS.md

> Personal coding agent instructions — Bon
> Compatible with: OpenAI Codex, Claude Code, Cursor, GitHub Copilot

---

## Identity & Context

This is a personal project repo. The developer works in SaaS Customer Success (AU region)
and builds side projects involving HTML tools, French learning apps, music, and design.
Primary stack: vanilla HTML/CSS/JS (single-file preferred), localStorage, occasionally React/Vite.

---

## Core Rules

- **Single-file first** — prefer self-contained `.html` files over multi-file setups unless
  the project is explicitly a framework app (React/Vite)
- **No unnecessary dependencies** — don't add npm packages unless the task clearly requires it
- **Ask before restructuring** — if you think the architecture should change, propose first, don't act
- **Never modify** `AGENTS.md`, `.env`, or any file containing API keys
- **Preserve existing comments** — don't strip out `<!-- section -->` markers or `// TODO` notes

---

## Code Style

- Indent: 2 spaces
- Quotes: double quotes in HTML attributes, single quotes in JS
- CSS: use CSS variables (`--color-primary`, `--font-base`) for any design tokens
- JS: vanilla ES6+, no TypeScript unless project already uses it
- Naming: camelCase for JS, kebab-case for CSS classes, UPPER_SNAKE for constants
- Always add a brief comment above any function longer than 10 lines

---

## UI & Design Standards

- Mobile-first responsive layout
- Avoid default browser styling — always reset or normalize
- Use smooth transitions (`transition: 0.2s ease`) for interactive elements
- Prefer CSS Grid or Flexbox, avoid fixed pixel widths
- Dark mode support via `prefers-color-scheme` media query when relevant
- Information hierarchy: clear H1 > H2 > body text distinction

---

## Testing & Verification

- After any JS change, confirm no `console.error` would fire on load
- For HTML tools: verify localStorage read/write doesn't throw in private browsing
- For any fetch/API call: always include try/catch with user-facing error message
- Don't assume external APIs are available — add graceful fallback UI

---

## Project Types & Shortcuts

### HTML Learning App (e.g. French course)
- Store progress in localStorage with key pattern: `[projectName]_day[N]_[type]`
- Audio slots: use `<audio>` tags with `data-slot` attributes
- Always include a progress bar component at top of page

### HTML Toolkit / Excel Tool
- File input should accept `.xlsx`, `.xls`, `.csv`
- Show file name + row count after upload
- Export button always bottom-right, sticky if content is long

### Landing Page / Sticker Sheet
- Include a hero section, feature section, and CTA
- Use Bagel Cat as mascot/icon where appropriate (orange cartoon cat character)
- Palette: warm tones preferred unless project specifies otherwise

### CS Workspace Tool
- Always include a search/filter input at top
- Tables: sortable columns, alternating row colors
- Status badges: use color-coded pills (green/yellow/red)

---

## Skills to Call (if available)

If the `.agents/skills/` folder exists in this repo, use these skills when relevant:
- `$create-plan` — before starting any task over 30 lines of code
- `$code-change-verification` — before finalizing any edit to core logic

---

## What NOT to Do

- Don't generate placeholder Lorem Ipsum — use realistic dummy data relevant to the project
- Don't add Google Fonts or CDN links without asking — some projects are offline-first
- Don't use `alert()` for any UX feedback — use inline UI messages instead
- Don't open new browser tabs or redirect without explicit user instruction
- Don't generate AI-looking filler copy ("Welcome to your amazing dashboard!")

---

## Communication Style

- Be concise — bullet points over paragraphs when listing options
- If a task is ambiguous, ask ONE clarifying question before proceeding
- When done, summarize what changed in 3 lines max
- Flag anything that might break existing functionality before making the change
