# Instrucciones del proyecto — Debate Council

Este proyecto implementa un sistema de debate agéntico basado en Claude Code dynamic workflows.

## Comando principal

Usa la skill `/debate-council` cuando el usuario pida evaluar, debatir, refutar, contrastar o someter a crítica una tesis, decisión, hipótesis, plan o argumento.

## Regla central

No hagas debate retórico. Ejecuta deliberación basada en evidencia:

**tesis → evidencia → posiciones independientes → contraexamen → auditoría → crítica lógica → sesgos → veredicto**

## Cuándo usar dynamic workflow

Usa dynamic workflow si la tesis requiere varias perspectivas independientes, evidencia cruzada, revisión adversarial o alto nivel de confianza. Para temas simples, usa la skill sin workflow.

## Calidad de evidencia

Toda afirmación crítica debe etiquetarse como:

- soportada;
- parcialmente soportada;
- no soportada;
- contradicha;
- requiere validación humana.

## Salidas

Guarda reportes en:

- `outputs/reports/`
- `outputs/json/`

## Límites

No inventes fuentes, datos, citas ni documentos. Cuando falte información, dilo claramente. En decisiones sensibles, incluye revisión humana obligatoria.
