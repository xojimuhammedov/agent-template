# Agents — Project Name

Welcome to the data/application layer. This file serves as the main entry point for AI agents.

## Start Here
- [Docs Index](docs/README.md) — How the documentation is organized
<!-- - [Architecture Overview](docs/architecture/overview.md) — High-level design and layering -->
- [Rules Index](.agents/rules/README.md) — All agent rules organized by topic

## Project Overview
**[Project Name]** is a [short description of your project].
- **Core Technology**: [e.g., Next.js, Node.js, TypeScript, React.js, JavaScript]
- **Key Feature 1**: [Description]
- **Key Feature 2**: [Description]

## Where Skills and Rules Live
- **Rules — canonical home:** `.agents/rules/<name>.mdc` (the only git-tracked copy). The 
`.codex/rules/` trees are gitignored presentation mirrors containing relative symlinks back to `.agents/rules/`.
<!-- - **Skills — canonical home:** `skills-contrib/<skill-name>/SKILL.md`. `.codex/skills/` and `.agents/skills/` are symlink mirrors. -->
- **Rule/Skill edits:** Always edit the files at their canonical path, not via the symlink.

## Golden Rules
- Use `yarn`, or `npm`.
- Build with `yarn build` or `npm run build`.
- Never use `any` in TypeScript.
- Always write tests before creating or modifying implementation.
- Don't add comments if avoidable; prefer code that clearly expresses its intent.
- Keep documentation and rules current when changing features.

## Common Commands
```bash
pnpm dev            # Frontend loyihani development rejimida ishga tushirish
pnpm build          # Production uchun frontend build yaratish
pnpm preview        # Production buildni lokal ko‘rib chiqish
pnpm test           # Unit va integration testlarni ishga tushirish
pnpm lint           # ESLint qoidalari bo‘yicha kodni tekshirish
pnpm typecheck      # TypeScript xatolarini build qilmasdan tekshirish
```

## Core Concepts
### [Concept 1, e.g., ExecutionContext]
[Description of the pattern/concept and how it's passed or structured.]

### [Concept 2, e.g., Data Access Seam]
[Description of the database access layer, repository pattern, etc.]

## Ask First
- Major architectural changes or refactoring.
- Modifying core database schemas.
- Changes affecting CI pipelines.
EOF