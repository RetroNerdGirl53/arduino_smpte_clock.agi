# AGENTS.md — stuff and things (.agi envelope)

You are working inside a **`.agi` envelope**: an Aionima project monorepo.
`CLAUDE.md` is a symlink to this file.

## Structure

- `repos/<name>/` — code repositories, each a git **submodule** pinned to
  a commit. Do code work INSIDE these: commit/push in the repo, then the
  envelope's submodule pointer is advanced separately.
- `.ai/` — shared knowledge, writable by humans and agents:
  - `.ai/knowledge/` — notes, docs, references
  - `.ai/plans/` — plans and design docs
  - `.ai/pm/` — project management
  - `.ai/chat/` — saved conversations
  - `.ai/memory/` — long-lived memory
  - `.ai/issues/` — issue notes
- `sandbox/` — scratch space, gitignored. Use freely; never relied upon.
- `.trash/` — soft-delete buffer, gitignored.
- `project.json` — the envelope manifest (repo registry + metadata).

## Rules

- The envelope never commits code that belongs to a submodule. Code lives
  in `repos/<name>`; the envelope only tracks the submodule pointer.
- `.ai/`, `sandbox/`, `.trash/` are envelope-owned — never submoduled.
- After cloning: `git submodule update --init --recursive`.
- Submodule pins advance deliberately
  (`git submodule update --remote repos/<name>`), not automatically.
