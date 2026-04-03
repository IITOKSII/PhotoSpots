# Photo Spots — Engineering Rules

## Session Continuity
- On every session start: read `.claude/MEMORY.md` for full project context
- On every session end: update `.claude/MEMORY.md` — append to Change Log, update Known Issues/Todo, update Current State if anything changed

## Stack
- Single-file app: `index.html` (HTML + CSS + JS, no build step)
- Firebase 10 compat SDK (CDN) — Auth + Firestore
- Leaflet 1.9.4 (CDN) — map
- Gemini 1.5 Flash REST API — AI tips
- GitHub Pages — hosting (master branch)

## Config placeholders (top of <script> in index.html)
- `FIREBASE_CONFIG` — replace with Firebase console values
- `GEMINI_KEY` — replace with Gemini API key

## Module Dependency Order
state → auth → map → pins → handbook → ai → ui

## Engineering Rules

### Core
- Action-first. No preamble, no trailing summaries. 1-sentence status updates max.
- Minimal impact: touch the minimum code necessary.
- No speculative abstractions. Three similar lines beats a premature abstraction.

### Token Efficiency
- Never read files until the current sub-task needs them.
- NEVER rewrite the entire file. Edit tool only (changed lines).
- For 3+ steps or 3+ files: write a numbered plan first.
- At ~15–20 messages: "Context is heavy. Summarize and start a new thread?"

### Code Quality
- No docstrings or comments on code you didn't change.
- No backwards-compat hacks, feature flags, or one-time-use helpers.
- Don't design for hypothetical future requirements.

### Security
- Never introduce XSS, injection, or OWASP Top 10 issues.

### File Operations
- Prefer editing existing files over creating new ones.
- Never create *.md or README files unless explicitly asked.

### Risky Actions
- Confirm before: destructive ops, force push, drops, deletes.
