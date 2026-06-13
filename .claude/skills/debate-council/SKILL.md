---
name: debate-council
description: Ejecuta un sistema agéntico de debate deliberativo con evidencia, posturas independientes, crítica adversarial, auditoría de evidencia, crítica lógica, detección de sesgos y veredicto final. Úsalo para evaluar tesis, decisiones, hipótesis, planes, argumentos o estrategias.
allowed-tools:
  - Read
  - Write
  - Edit
  - Glob
  - Grep
  - WebSearch
  - WebFetch
  - Task
---

# Debate Council

## Propósito

Convierte una tesis o decisión en un debate agéntico serio, trazable y basado en evidencia. El objetivo no es ganar un argumento, sino mejorar la calidad de la decisión.

## Activación

Usar cuando el usuario diga algo como:

- “debate esta tesis”;
- “evalúa esta idea”;
- “haz un sistema de debate”;
- “contrasta argumentos”;
- “qué diría un crítico”;
- “somete esta decisión a debate”;
- “haz un análisis PRO/CON con árbitro”.

## Decisión de ejecución

Antes de ejecutar, clasifica el caso:

### Debate simple

Usar conversación normal si:

- hay una tesis corta;
- no requiere evidencia externa;
- el riesgo es bajo;
- bastan 2-3 perspectivas.

### Debate con subagentes

Usar subagentes normales si:

- hay 3-6 perspectivas;
- se requiere aislamiento de contexto;
- no hace falta una orquestación repetible.

### Debate con dynamic workflow

Usar dynamic workflow si:

- hay múltiples perspectivas independientes;
- se necesita evidencia cruzada;
- se requiere revisión adversarial;
- el problema es importante;
- el usuario quiere una salida formal;
- el trabajo debe quedar codificado y repetible;
- el usuario usa “ultracode”, “workflow dinámico” o “dynamic workflow”.

## Flujo obligatorio del debate

### Fase 0 — Intake

Extraer:

- tesis;
- contexto;
- objetivo de la decisión;
- audiencia;
- restricciones;
- horizonte temporal;
- criterios de evaluación;
- evidencia disponible;
- evidencia faltante;
- nivel de riesgo.

Si falta la tesis o el objetivo, preguntar antes de continuar.

### Fase 1 — Mapa de tesis

Reformular la tesis en forma evaluable:

```text
Tesis: ...
Decisión implícita: ...
Criterios para aceptarla: ...
Criterios para rechazarla: ...
Qué evidencia sería decisiva: ...
```

### Fase 2 — Evidencia

El Evidence Scout reúne evidencia y la etiqueta por calidad.

No debe opinar.

### Fase 3 — Posiciones independientes

Crear posiciones independientes, como mínimo:

- Proponent;
- Opponent;
- Pragmatist;
- Risk Critic;
- Alternative Builder.

Cada posición debe emitir su análisis sin copiar a las demás.

### Fase 4 — Contraexamen

El Cross Examiner hace preguntas duras y detecta huecos.

### Fase 5 — Auditoría de evidencia

El Evidence Auditor revisa afirmaciones importantes.

### Fase 6 — Crítica lógica

El Logic Critic detecta falacias, saltos causales y exceso de confianza.

### Fase 7 — Detección de sesgos

El Bias Detector busca sesgos cognitivos, organizacionales o de preferencia del usuario.

### Fase 8 — Árbitro final

El Final Arbiter emite veredicto.

No debe promediar opiniones. Debe decidir por calidad de evidencia, fuerza lógica, severidad del riesgo, reversibilidad, alternativas y costo de equivocarse.

## Veredictos permitidos

Usar uno de estos:

```text
ACEPTAR TESIS
ACEPTAR TESIS CON CONDICIONES
RECHAZAR TESIS
TESIS PLAUSIBLE PERO NO DEMOSTRADA
TESIS DÉBIL
TESIS CONTRADICHA
NECESITA MÁS EVIDENCIA
DIVIDIR EN SUBTESIS
ESCALAR A HUMANO
```

## Reporte Markdown

Generar:

```text
outputs/reports/YYYY-MM-DD_debate-council_<slug>.md
```

Con estructura:

```markdown
# Debate Council Report: <título>

## 1. Resumen ejecutivo

## 2. Tesis evaluada

## 3. Reformulación neutral

## 4. Criterios de evaluación

## 5. Evidencia revisada

| Fuente | Tipo | Calidad | Hallazgo | Limitación |
|---|---|---|---|---|

## 6. Hechos, supuestos e inferencias

### Hechos

### Supuestos

### Inferencias

### Opiniones

## 7. Posturas independientes

### 7.1 Proponent

### 7.2 Opponent

### 7.3 Pragmatist

### 7.4 Risk Critic

### 7.5 Alternative Builder

## 8. Contraexamen

## 9. Auditoría de evidencia

| Afirmación | Estado | Evidencia | Comentario |
|---|---|---|---|

## 10. Crítica lógica

## 11. Sesgos detectados

## 12. Mejores argumentos a favor

## 13. Mejores argumentos en contra

## 14. Alternativas superiores o híbridas

## 15. Veredicto final

## 16. Nivel de confianza

## 17. Qué cambiaría el veredicto

## 18. Próximos pasos

## 19. Revisión humana requerida
```

## JSON obligatorio

Generar:

```text
outputs/json/YYYY-MM-DD_debate-council_<slug>.json
```

Con estructura mínima:

```json
{
  "title": "",
  "date": "",
  "thesis": "",
  "neutral_reformulation": "",
  "decision_context": "",
  "criteria": [],
  "evidence": [],
  "facts": [],
  "assumptions": [],
  "inferences": [],
  "opinions": [],
  "positions": [],
  "cross_examination": [],
  "evidence_audit": [],
  "logic_critique": [],
  "biases": [],
  "best_arguments_for": [],
  "best_arguments_against": [],
  "alternatives": [],
  "verdict": "",
  "confidence": "",
  "what_would_change_verdict": [],
  "next_steps": [],
  "human_review_required": true
}
```

## Regla anti-alucinación

Si no hay evidencia suficiente, el veredicto debe ser `NECESITA MÁS EVIDENCIA`, `TESIS PLAUSIBLE PERO NO DEMOSTRADA` o `DIVIDIR EN SUBTESIS`.

## Regla de cierre

Antes de cerrar, verifica:

- ¿La tesis fue reformulada neutralmente?
- ¿Las posturas fueron independientes?
- ¿Hay crítica adversarial?
- ¿Las afirmaciones críticas tienen evidencia?
- ¿Se separaron hechos, supuestos e inferencias?
- ¿El veredicto no sobrepasa la evidencia?
