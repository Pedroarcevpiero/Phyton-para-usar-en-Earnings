# Especificación del workflow dinámico — Debate Council

Usa esta especificación para pedir a Claude Code que escriba y ejecute un dynamic workflow.

## Prompt recomendado para Claude Code

```text
ultracode: Crea y ejecuta un workflow dinámico llamado debate-council para evaluar la siguiente tesis:

<TESIS>

Contexto:
<CONTEXTO>

Objetivo del debate:
<OBJETIVO>

Sigue estrictamente docs/debate-workflow-spec.md y la skill .claude/skills/debate-council/SKILL.md.

El workflow debe orquestar subagentes independientes para evidencia, postura pro, postura contra, postura pragmática, riesgos, alternativas, contraexamen, auditoría de evidencia, crítica lógica, sesgos y arbitraje final.

No ejecutes un debate retórico. Separa hechos, supuestos, inferencias y opiniones. Marca toda afirmación crítica como soportada, parcialmente soportada, no soportada, contradicha o pendiente de validación humana.

Genera outputs Markdown y JSON en outputs/reports y outputs/json.
```

## Fases del workflow

### 0. Intake

Validar que existan tesis, contexto y objetivo. Si no hay tesis evaluable, detener y pedir aclaración.

### 1. Thesis Framing

Un agente `thesis-framer` reformula neutralmente la tesis, identifica subtesis y define criterios de evaluación.

### 2. Evidence Collection

Lanzar 2-4 agentes `evidence-scout` en paralelo, según el caso:

- evidencia a favor;
- evidencia en contra;
- evidencia contextual;
- evidencia faltante.

### 3. Independent Positions

Lanzar en paralelo:

- proponent-agent;
- opponent-agent;
- pragmatist-agent;
- risk-critic;
- alternative-builder.

Cada agente trabaja con la tesis y evidencia disponible, pero debe producir su posición en formato estructurado.

### 4. Cross Examination

El `cross-examiner` recibe las posiciones y formula objeciones duras.

### 5. Evidence Audit

El `evidence-auditor` verifica claims críticos.

### 6. Logic Critique

El `logic-critic` detecta falacias y debilidades del razonamiento.

### 7. Bias Detection

El `bias-detector` detecta sesgos.

### 8. Final Arbitration

El `final-arbiter` emite veredicto y confianza.

### 9. Output

Un agente o fase final escribe Markdown y JSON.

## Límite de escala

Para una primera corrida, usar pocos agentes:

- 2 Evidence Scouts;
- 5 Position Agents;
- 4 Review Agents;
- 1 Final Arbiter.

No superar 12 agentes salvo que el usuario lo apruebe.

## Reglas de calidad

- Las posiciones deben ser independientes.
- El árbitro no debe usar claims marcados como no soportados salvo para indicar incertidumbre.
- El veredicto debe ser más conservador si la evidencia es débil.
- Para temas sensibles, incluir revisión humana.
