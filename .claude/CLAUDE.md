# Global Instructions for All Projects

These instructions override defaults and apply to ALL projects using this config.

## Language & Communication

- Responde siempre en español de España, neutro y sin expresiones estereotípicas
- Respuestas concisas: ve al grano, sin introducciones innecesarias
- NO resúmenes finales (user puede leer el diff)

## Git Conventions

- Usa siempre **Conventional Commits**: `type(scope): descripción`
- Tipos permitidos: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `perf`, `ci`, `build`, `revert`
- Usa siempre **Git Flow**: ramas `main`, `develop`, `feature/*`, `release/*`, `hotfix/*`
- Features salen de `develop` y se fusionan en `develop`
- Hotfixes salen de `main` y se fusionan en `main` y `develop`

## Technology Stack Decisions

- **Always verify LTS versions** using context7 before recommending
- Mention version explicitly: "Next.js 16.2 LTS" not just "Next.js 16"
- Update stack recommendations if newer LTS exists

### No AI-Powered Apps by Default

**Rule**: Projects are NOT "AI-powered" by default. IA is ONLY for automating the DEVELOPER'S workflow.

**Exception**: Only if user explicitly says "I want AI integrated in the app"

**Examples**:
- ✅ Blog generated/enriched with Claude (user sees clean blog, not IA)
- ❌ Live Claude agent demo in app (AI-powered feature, unless explicitly requested)
- ✅ Newsletter auto-generated (behind scenes)
- ❌ Chat widget with Claude (unless user asks)

## Agents to Use

### project-planner
- Generates strategy (NO timings, only order)
- Analyzes market, risks, evolution
- Verifies tech versions with context7

### task-breakdown
- Decomposes strategy into phases/tasks
- Identifies dependencies and parallelization
- Includes version-specific subtasks

**Workflow**: project-planner → task-breakdown

## Model Preference

All custom agents use **Haiku** by default (faster, cheaper, sufficient for planning)

## Code Quality

- No comments unless WHY is non-obvious
- Trust internal code guarantees
- Validate at system boundaries (user input, external APIs)
- No error handling for scenarios that can't happen
- No feature flags for one-shot operations
- No backwards-compatibility shims

## When NOT to Plan

Skip planning for:
- Single-line fixes
- Obvious small tweaks
- Tasks with very specific, detailed instructions

## Remember

- User iterates between LLMs (Claude Code, OpenCode, others)
- This config is portable across all tools
- Memory in `.dev/MEMORY.md` is exported from Engram
- Keep decisions documented here for future sessions
