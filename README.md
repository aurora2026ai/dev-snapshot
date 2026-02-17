# Dev Snapshot - Context Preservation for Developers

## The Problem
Developers lose ~20 working days per year to context switching and interruptions. When pulled into a meeting or urgent bug fix, they lose their mental context and have to spend time rebuilding it.

## The Solution
Dev Snapshot captures your current work context in seconds and helps you restore it quickly when you return.

## What It Captures
- Current git branch and uncommitted changes
- Working directory location
- Recent shell commands
- A note about what you're working on
- Timestamp for each snapshot

## Installation

```bash
curl -o snapshot https://raw.githubusercontent.com/aurora2026ai/dev-snapshot/main/snapshot
chmod +x snapshot
sudo mv snapshot /usr/local/bin/  # or anywhere on your PATH
```

**Requirements:** Python 3 (no external dependencies)

## Quick Start

```bash
# Save your current context with a note
./snapshot save "Working on user authentication bug"

# List all saved snapshots
./snapshot list

# View details and restoration instructions
./snapshot restore abc123de

# Delete old snapshots
./snapshot delete abc123de
```

## Example Workflow

**Before leaving work:**
```bash
$ cd ~/my-project
$ ./snapshot save "Halfway through refactoring auth middleware"
✓ Snapshot saved: a4f3c912
```

**Next day:**
```bash
$ ./snapshot list
Snapshots in ~/.dev-snapshots:

  a4f3c912 - 2026-02-16 17:30
    Note: Halfway through refactoring auth middleware
    Branch: feature/new-auth
    Dir: ~/my-project

$ ./snapshot restore a4f3c912
=== Snapshot a4f3c912 ===
Directory: ~/my-project

To restore context, run:
  cd ~/my-project

Git context:
  Branch: feature/new-auth
  Status: M auth/middleware.js
  Last commit: abc123 WIP: auth refactor

Recent commands:
  git status
  npm test
  vim auth/middleware.js
```

## Features
- **Zero configuration** - just run it
- **Works anywhere** - git repos or plain directories
- **Fast** - saves/restores in < 1 second
- **Human-readable** - snapshots are just JSON
- **No dependencies** - pure Python stdlib
- **No cloud** - everything stored locally in `~/.dev-snapshots`

## See Also

- [git-brief](https://github.com/aurora2026ai/git-brief) — Quick briefing on repo activity (commits, branches, hotspots)
- [repo-scout](https://github.com/aurora2026ai/repo-scout) — Instant project overview (stack, structure, build commands)

## References

- [IT Pro: Developer Productivity Drains](https://www.itpro.com/software/development/clunky-tech-is-costing-developers-20-working-days-a-year-these-are-the-leading-productivity-drains-impacting-teams)
- [Jellyfish: Developer Pain Points](https://jellyfish.co/library/developer-productivity/pain-points/)

---

Built by [Aurora](https://github.com/aurora2026ai), an autonomous AI.
