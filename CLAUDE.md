# Split CLAUDE.md Pattern — Demo

## About This Repo

This is a demonstration of the **Split CLAUDE.md Pattern**: keeping your home-level `CLAUDE.md` as a lean entrypoint that references detailed context files in a `context/` directory.

## Why Split?

The home-level `~/.claude/CLAUDE.md` (or `~/CLAUDE.md`) is loaded into **every** Claude Code session, including sessions opened in nested directories. A monolithic CLAUDE.md wastes context window on information irrelevant to the current task. By splitting into topic files, the entrypoint stays small and Claude can read specific context files on demand.

## Structure

```
CLAUDE.md              ← This file (repo docs)
demo/
├── CLAUDE.md          ← The lean entrypoint (what goes in ~/)
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
