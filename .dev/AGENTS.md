# Agentes Personalizados

Documentación operacional de agentes reutilizables.

## project-planner

**Ubicación**: `./.claude/agents/project-planner.md`  
**Modelo**: Haiku (fast, cost-effective)  
**Autoinvocación**: Automática cuando user pide help para elegir stack o estrategia

### Propósito
Analizar idea + stack para generar:
1. Arquitectura general (diagrama ASCII)
2. MVP features (qué es obligatorio)
3. Features diferenciadores originales
4. Análisis de mercado (competencia real)
5. Riesgos + mitigación
6. Estrategia evolución (orden de construcción)

### Características Clave
- **SIN timings**: Solo estrategia, no "semana 1", "mes 3"
- **Context7 integration**: Verifica TODAS las tecnologías por versión LTS
- **Análisis exhaustivo**: Tablas comparativas, trade-offs concretos
- **Mercado real**: No inventa números, busca datos

### Cómo Invocar

```
@agent-project-planner

Idea: [descripción del proyecto]
Stack: [tecnologías elegidas]
Target: [audiencia/mercado]
```

### Output Esperado

```markdown
# PROJECT STRATEGY: [Nombre]

## 1. Arquitectura General
[Diagrama ASCII + componentes]

## 2. MVP Features
[Features core obligatorias]

## 3. Features Diferenciadores Originales
[Ideas creativas]

## 4. Análisis de Mercado
[Competencia real, diferenciadores]

## 5. Riesgos & Mitigación
[Técnico, comercial, operacional]

## 6. Estrategia Evolución
[Orden de construcción, no timings]
```

### Notas
- Si necesita aclaraciones, hará 5 preguntas clave
- Siempre verifica versiones LTS con context7
- NO incluye features AI-powered a menos que user indique
- Enfoque en viabilidad real, no hype

---

## task-breakdown

**Ubicación**: `./.claude/agents/task-breakdown.md`  
**Modelo**: Haiku  
**Entrada**: Estrategia de project-planner

### Propósito
Desglose operacional:
1. Fases (grupos coherentes de trabajo)
2. Tareas (desglose concreto)
3. Subtareas (nivel de detalle operacional)
4. Complejidad relativa (Simple/Media/Compleja)
5. Dependencias (qué bloquea qué)
6. Paralelización (qué puede hacerse simultáneamente)

### Características Clave
- **SIN timings**: Solo complejidad relativa
- **Operacional**: Alguien que lea las subtareas sabe exactamente qué hacer
- **Dependencias explícitas**: Cada tarea dice qué necesita antes
- **Versiones LTS específicas**: "Prisma v7.x" no solo "Prisma"

### Cómo Invocar

```
@agent-task-breakdown

[Pega estrategia de project-planner aquí]

---

Regenera task breakdown basándote en esta estrategia
```

### Output Esperado

```markdown
# TASK BREAKDOWN: [Nombre Proyecto]

## Fase 1: [Nombre Fase]
**Justificación**: [Por qué esta fase primero]
**Dependencias**: [Qué debe estar done antes]

### Tarea 1.1: [Nombre]
**Complejidad**: Simple/Media/Compleja
**Descripción**: [Qué se entrega]
- Subtarea 1.1.1: [Detail]
- Subtarea 1.1.2: [Detail]
**Dependencias**: [Tareas que bloquean]

[Continúa...]

## MATRIZ DE DEPENDENCIAS
[Muestra flujo de bloques]
```

### Notas
- Verifica versiones LTS en subtareas específicas
- Identifica paralelización (crucial para MVP rápido)
- Señala "dead ends" a evitar
- Propone validación gates entre fases

---

## Workflow Recomendado

1. **project-planner** → genera estrategia
2. **task-breakdown** → desglose operacional
3. **GitHub Issues** → crear issues desde breakdown
4. **Implementar** → seguir dependencias

---

## Customización

Si necesitas agente específico para otro dominio:
1. Copia template de alguno de arriba
2. Define propósito claro
3. Especifica output esperado
4. Agrega al `.claude/agents/`
5. Documenta aquí
6. Commit: `feat(agents): add [agent-name]`

## Últimas Adiciones

- 2026-04-17: project-planner + task-breakdown iniciales
