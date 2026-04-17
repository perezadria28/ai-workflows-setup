# Memory / Decisiones Clave

Exported from Engram 2026-04-17. Shared across projects via symlinks or copies.

## Preferencias Globales

### Comunicación
- Español España neutro, sin estereotipos
- Respuestas concisas, sin resúmenes finales
- Va al grano

### Tecnología
- Verificar versiones LTS SIEMPRE con context7
- Mentionar version explícita: "Next.js 16.2 LTS"
- Actualizar recomendaciones si existe LTS más nueva

### IA en Proyectos
- **Default**: NO AI-powered en apps
- **Exception**: Solo si user dice explícitamente "quiero IA integrada"
- IA está para automatizar WORKFLOW del developer, no runtime del usuario

### Agentes & Modelos
- `project-planner` y `task-breakdown` son workflow complementario
- Todos agentes usan **Haiku** por defecto
- project-planner genera estrategia SIN timings

## Stack Decisions Validadas

### AI Engineer Portfolio (narratives / personal-app)

**Stack final (versiones LTS verificadas)**:
- Next.js 16.2 + React 19 + TypeScript 6.0
- Tailwind CSS 4.2 + shadcn/ui
- PostgreSQL 15 (Vercel Postgres)
- Resend v6 + React Email
- MDX (next-mdx-remote v6) para blog
- Prisma v7 + NextAuth v5 (admin only)

**Por qué**:
- Time-to-market crítico: Next.js 16.2 en Vercel = 1-click deploy
- Type safety: TypeScript strict + Prisma + Zod
- Performance: SSR + Edge + Tailwind = 90+ Lighthouse
- NO API Claude integrada en app final (IA solo en desarrollo)

**Mercado**:
- Diferenciador: Newsletter + narrativa (cómo aprendió CON IA)
- Target: Reclutadores + clientes buscando AI Engineer
- Crecimiento esperado: Mes 12 = 1.5k subscribers, 10k/mes blog views, 8-10 inbound leads

## Agentes Personalizados

### project-planner
**Ubicación**: `./.claude/agents/project-planner.md`
**Modelo**: Haiku
**Propósito**: Análisis estratégico de proyectos
**Output**: Arquitectura, MVP, features, mercado, riesgos, evolución (SIN timings)
**Critical**: Verifica versiones LTS con context7

### task-breakdown
**Ubicación**: `./.claude/agents/task-breakdown.md`
**Modelo**: Haiku
**Propósito**: Desglose operacional en fases/tareas
**Output**: Phases, tasks, subtasks, dependencies, parallelization
**Input**: Strategy from project-planner

## Conventions

### Git
- Conventional Commits: `type(scope): desc`
- Git Flow: main, develop, feature/*, release/*, hotfix/*
- Features: develop → develop
- Hotfixes: main → main + develop

### Code
- NO comments unless WHY is non-obvious
- Trust internal guarantees
- Validate at boundaries (user input, APIs)
- NO error handling for impossible scenarios

## Projects Using This Config

- `personal-app`: Portfolio + blog + newsletter (private)
- Others will be added as symlinks

## Last Updated

2026-04-17: Initial export from Engram
