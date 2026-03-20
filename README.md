[![Part of the Claude Agent Blueprints Index](https://img.shields.io/badge/Claude%20Agent%20Blueprints-Index-blue?style=flat-square&logo=github)](https://github.com/danielrosehill/Claude-Code-Repos-Index)

# Split CLAUDE.md Pattern

A template for structuring your Claude Code persistent configuration (`~/.claude/CLAUDE.md`) as a lean entrypoint that references detailed context files in a `context/` directory.

## Background

For an excellent overview of how the Claude Code memory system and `CLAUDE.md` files work, see:
**[Deep Dive: Claude Code Memory System & CLAUDE.md](https://institute.sfeir.com/en/claude-code/claude-code-memory-system-claude-md/deep-dive/)**

## The Problem

Claude Code loads `~/.claude/CLAUDE.md` into **every session**, including sessions opened in nested directories like `~/repos/my-project/`. The loading is **additive** — if you also have a project-level `CLAUDE.md` in `~/repos/my-project/`, both files are read and injected as system-level context. This is by design: the user-level file carries your persistent identity and preferences, while project-level files carry project-specific instructions.

A monolithic `~/.claude/CLAUDE.md` that contains every detail about your hardware, network topology, contacts, troubleshooting patterns, and tool configurations wastes context window on information that's irrelevant to most sessions. If you're working on a Node.js project, you don't need your full LAN map and GPU troubleshooting notes loaded into context.

## The Pattern

Keep `~/.claude/CLAUDE.md` as a **compact entrypoint** (~30-50 lines) that contains:

- Who you are (name, location, role — the basics)
- How Claude should behave (autonomy level, communication style)
- Key filesystem paths
- A pointer to `context/` for everything else

Detailed context lives in **topic-specific files** under a `context/` directory. Claude reads these on demand when the task requires it.

```
~/.claude/
├── CLAUDE.md                          ← Lean entrypoint (loaded every session)
└── context/
    ├── system-environment.md          ← OS, hardware, network, LAN map
    ├── development-environment.md     ← Languages, tools, containers, CI/CD
    ├── file-organization.md           ← Directory structure, repo conventions
    ├── mcp-usage.md                   ← MCP server guidelines
    ├── media-tools.md                 ← Audio, video, AI/ML tools
    ├── troubleshooting.md             ← Common fix patterns
    ├── contacts.md                    ← People and email addresses
    └── auth-and-security.md           ← SSH, API keys, credentials policy
```

## Important: Use `~/.claude/CLAUDE.md`, Not `~/CLAUDE.md`

Claude Code resolves `CLAUDE.md` files at multiple levels. There are two places a "user-level" config can live:

- **`~/.claude/CLAUDE.md`** — The canonical user-level config inside Claude's own config directory
- **`~/CLAUDE.md`** — A file in your home directory (also picked up by Claude Code)

**My strong recommendation: only use `~/.claude/CLAUDE.md`.** Do not create a `~/CLAUDE.md`.

It's easy to end up with both files and not realize it. When that happens, you get dual overlapping user-level contexts — which defeats the entire purpose of pruning context for efficiency. You end up with redundant or conflicting instructions loaded into every session, and debugging which file is saying what becomes a headache.

Pick one location. `~/.claude/CLAUDE.md` is the right one — it lives inside Claude's own config directory where it belongs.

## How Loading Works (Additive Model)

Claude Code's `CLAUDE.md` loading is **additive across directory levels**:

| File | Scope | Loaded When |
|------|-------|-------------|
| `~/.claude/CLAUDE.md` | User-level (persistent) | **Every session**, regardless of working directory |
| `~/repos/CLAUDE.md` | Directory-level | Sessions opened at or below `~/repos/` |
| `~/repos/my-project/CLAUDE.md` | Project-level | Sessions opened at or below `~/repos/my-project/` |

If you open Claude Code in `~/repos/my-project/`, **all three** are loaded and combined. This is the intended design — user-level carries your identity and preferences, project-level carries project-specific instructions.

The split pattern optimizes the **user-level** file specifically, because it's the one loaded into every session regardless of context.

## Demo

The `demo/` directory contains a complete synthetic example modeled after a real-world setup (fictional persona "Alex Chen", a DevOps engineer in Portland). Use it as a starting point for your own configuration.

```
demo/
├── CLAUDE.md              ← Example lean entrypoint
└── context/
    ├── system-environment.md
    ├── development-environment.md
    ├── file-organization.md
    ├── mcp-usage.md
    ├── media-tools.md
    ├── troubleshooting.md
    ├── contacts.md
    └── auth-and-security.md
```

## Adapting This Template

1. Copy `demo/CLAUDE.md` to `~/.claude/CLAUDE.md`
2. Copy `demo/context/` to `~/.claude/context/`
3. Replace the synthetic data with your own details
4. Add or remove context files as needed for your workflow

The file categories in the demo are a starting point. Your setup might need different splits — the principle is simply: keep the entrypoint lean, put details in topic files.

---

For more Claude Code projects, visit [my index](https://github.com/danielrosehill/Claude-Code-Repos-Index).
