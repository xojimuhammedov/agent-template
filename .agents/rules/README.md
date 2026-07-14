---
trigger: always_on
---

# Agent Rules Index

Actionable guidelines for frontend agents and developers. Keep detailed explanations in `docs/` and use these rules for quick enforcement.

## Canonical Home & Sync

Every rule lives in `.agents/rules/<name>.mdc` and is the only git-tracked copy.

```bash
pnpm rules:sync           # (Re)generate the symlink trees
pnpm lint:rules:symlinks  # Verify rule trees are in sync
```

## Always Apply

* [read-agents-md.mdc](./read-agents-md.mdc) — Read `AGENTS.md` before making changes
* [doc-maintenance.mdc](./doc-maintenance.mdc) — Keep documentation, README files, and rules up to date
* [karpathy-guidelines.mdc](./karpathy-guidelines.mdc) — Reduce common AI-assisted coding mistakes

## Coding Style

* [typescript-best-practices.mdc](./typescript-best-practices.mdc) — TypeScript conventions and strict typing