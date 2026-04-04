# Crucible — IDE Setup Guide

Crucible works in any AI coding assistant that can read files and follow markdown instructions. This guide covers setup for the three most common environments.

---

## How It Works in Any IDE

The intelligence lives entirely in the markdown files. The adapter files (`CLAUDE.md`, `.cursorrules`) tell your IDE's AI where those files are and when to load them. Once the adapter is in place, the experience is the same:

- Say "I have an idea" → the ideation flow starts automatically
- The AI loads each persona file before applying its lens
- Artifacts are written to your project folders
- `/resume` restores full context from `_log.md`

---

## Antigravity

**Status: Native. No setup required.**

Antigravity reads `.agents/workflows/` automatically. Slash commands (`/ideate`, `/resume`) are built-in triggers. Everything works out of the box.

---

## Claude Code

**Adapter file:** `CLAUDE.md` (already in this repo)

`CLAUDE.md` is automatically read by Claude Code at the start of every session in this project. No additional configuration needed.

### Setup
1. Clone the repo
2. Open the project folder in Claude Code
3. That's it. `CLAUDE.md` loads automatically.

### How to trigger
```
"I have an idea..."           → starts /ideate flow
"Let's resume [project]"      → starts /resume flow
"/ideate"                     → starts /ideate flow
"/resume"                     → starts /resume flow
```

### Limitations
- **Stage 5 (Design) — Visual Inspection:** Claude Code cannot browse localhost. When the Designer persona asks to visually inspect the UI, either paste screenshots directly into the chat, or use the TEAM_PLAYBOOK.md prompt and describe the current state manually.
- Everything else works identically.

---

## Cursor

**Adapter file:** `.cursorrules` (already in this repo)

`.cursorrules` is loaded by Cursor into every AI conversation in this project. No additional configuration needed.

### Setup
1. Clone the repo
2. Open the project folder in Cursor
3. That's it. `.cursorrules` loads automatically.

### How to trigger
```
"I have an idea..."           → starts /ideate flow
"Let's resume [project]"      → starts /resume flow
"/ideate"                     → starts /ideate flow
"/resume"                     → starts /resume flow
```

> **Use Agent mode** (not Chat mode) for the full experience. Agent mode can read persona files, create project folders, and write artifact files. Chat mode can run the ideation conversation but cannot write files.

### Limitations
- **Stage 5 (Design) — Visual Inspection:** Cursor's browser access depends on your configuration. If the AI cannot access localhost, paste screenshots into the chat. The rest of the design spec will still be produced.
- **File writes:** Requires Agent mode. In Chat mode, the AI will produce the artifact content but you'll need to save it manually.

---

## Any Other AI (ChatGPT, Gemini, etc.)

**No automatic setup — use Manual Mode.**

The `TEAM_PLAYBOOK.md` contains copy-paste prompt templates for every stage. This approach works in any AI tool.

### How to use
1. Open `.antigravity/TEAM_PLAYBOOK.md`
2. Find the stage you need
3. Copy the prompt, fill in the `[bracketed]` fields
4. Paste into any AI chat

For persona depth: paste the contents of the relevant persona file at the top of your message before the stage prompt.

---

## Capability Comparison

| Feature | Antigravity | Claude Code | Cursor (Agent) | Manual (any AI) |
|---|---|---|---|---|
| Auto-triggers on "I have an idea" | ✅ | ✅ | ✅ | ❌ |
| Reads persona files automatically | ✅ | ✅ | ✅ | Manual paste |
| Writes artifact files to disk | ✅ | ✅ | ✅ | ❌ |
| `/ideate` slash command | ✅ native | ✅ trigger word | ✅ trigger word | ❌ |
| `/resume` from `_log.md` | ✅ native | ✅ trigger word | ✅ trigger word | ❌ |
| Stage 5 localhost visual inspection | ✅ | ⚠️ paste screenshots | ⚠️ paste screenshots | ⚠️ |
| Full 11-stage seamless flow | ✅ | ✅ | ✅ | Stage-by-stage |

---

## Troubleshooting

**The AI isn't following the ideation flow.**
Make sure you're using Agent mode (Cursor) or that `CLAUDE.md` exists in the project root. Try explicitly saying: *"Read `.agents/workflows/ideate.md` and follow it."*

**The AI is giving generic advice instead of persona output.**
The persona philosophy isn't loaded. Say: *"Read `.antigravity/PERSONA_PROTOCOL.md` and then read `[persona file]` in full before responding."*

**Artifact files aren't being written to disk.**
Cursor: switch to Agent mode. Claude Code: ensure you're in a project session, not a standalone chat.

**The AI stopped at Stage 5 and won't continue.**
Likely a localhost access issue. Paste a screenshot of the current UI state and say *"Use this as the visual reference for the Design audit."*
