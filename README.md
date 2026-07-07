# stuff and things

This is a **`.agi` envelope** — an Aionima project monorepo that bundles
one or more code repositories together with shared knowledge, planning,
and scratch space. Created with Genie.

## Layout

```
arduino-=smpte clock.agi/
├── project.json     Envelope manifest — repo registry + metadata
├── .gitmodules      Submodule registry (the repos below)
├── repos/           Code repositories, each a git submodule
├── .ai/             Shared knowledge (humans + agents)
│   ├── knowledge/   Notes, docs, references
│   ├── plans/       Plans and design docs
│   ├── pm/          Project management
│   ├── chat/        Saved conversations
│   ├── memory/      Long-lived agent memory
│   └── issues/      Issue notes
├── sandbox/         Scratch space (gitignored)
└── .trash/          Soft-delete buffer (gitignored)
```

## Working with it

Clone with submodules:

```
git clone --recurse-submodules <url>
# or, after a plain clone:
git submodule update --init --recursive
```

Each folder under `repos/` is an independent repository pinned to a
specific commit. The envelope tracks `project.json`, `.ai/`, and the
submodule pointers — never the code inside the submodules (that lives in
each repo). Advance a pin with `git submodule update --remote repos/<name>`.

For the agent-oriented version of this guide, see `AGENTS.md`
(`CLAUDE.md` is a symlink to it).
