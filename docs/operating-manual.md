# Manual operativo — Debate Council

## 1. Preparar la tesis

Formula la tesis así:

```text
Tesis: ...
Contexto: ...
Objetivo: ...
Decisión que necesito tomar: ...
Evidencia disponible: ...
Qué tipo de respuesta necesito: ...
```

## 2. Ejecución simple

```text
/debate-council Tesis: ... Contexto: ... Objetivo: ...
```

## 3. Ejecución con workflow dinámico

```text
ultracode: usa Debate Council para debatir esta tesis: ...
```

## 4. Revisión del workflow

Durante la corrida:

```text
/workflows
```

Desde allí puedes ver fases, agentes, tokens, pausar, reiniciar agentes o guardar el workflow.

## 5. Guardar como comando reutilizable

Cuando una corrida funcione bien:

1. Ejecuta `/workflows`.
2. Selecciona la corrida.
3. Presiona `s`.
4. Guarda en `.claude/workflows/`.
5. Luego podrás invocarla como comando `/debate-council` si le asignas ese nombre.

## 6. Buenas prácticas

- Empieza con una tesis acotada.
- No pidas 100 agentes en la primera prueba.
- Para temas críticos, exige fuentes.
- Para decisiones reales, usa revisión humana.
