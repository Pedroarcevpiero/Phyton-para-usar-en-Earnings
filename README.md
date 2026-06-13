# Debate Council — Dynamic Workflow para Claude Code

Sistema agéntico de debate deliberativo basado en evidencia para Claude Code.

## Qué es

`Debate Council` no es un debate teatral PRO/CON. Es un workflow dinámico que fuerza este ciclo:

1. formular tesis;
2. definir criterios;
3. buscar o revisar evidencia;
4. generar posiciones independientes;
5. cruzar objeciones;
6. auditar evidencia;
7. criticar lógica;
8. detectar sesgos;
9. sintetizar un veredicto trazable.

## Requisitos

- Claude Code v2.1.154 o superior.
- Dynamic workflows habilitados en `/config`.
- Plan compatible con dynamic workflows.
- Para usar web, WebSearch/WebFetch deben estar disponibles.

## Instalación

Copia todo este contenido en la raíz de tu proyecto Claude Code.

Luego abre Claude Code en esa carpeta y ejecuta:

```bash
claude --version
```

Verifica dynamic workflows:

```text
/config
```

Activa `Dynamic workflows` si aparece disponible.

## Uso recomendado

Invoca la skill:

```text
/debate-council Evalúa esta tesis: <tu tesis o decisión>. Contexto: <contexto>. Objetivo: <objetivo>.
```

Para forzar workflow dinámico:

```text
ultracode: usa Debate Council para evaluar esta tesis: <tesis>. Ejecuta el debate con evidencia, crítica cruzada, auditoría de evidencia y veredicto final.
```

También puedes pedir:

```text
Usa un workflow dinámico siguiendo docs/debate-workflow-spec.md para debatir esta tesis: <tesis>
```

## Outputs

El sistema debe generar:

```text
outputs/reports/YYYY-MM-DD_debate-council_<slug>.md
outputs/json/YYYY-MM-DD_debate-council_<slug>.json
```

## Seguridad

- No inventar fuentes.
- No convertir un argumento persuasivo en hecho.
- Separar hechos, supuestos, inferencias y opiniones.
- Marcar afirmaciones sin evidencia.
- Exigir revisión humana para decisiones financieras, legales, laborales, médicas o de alto impacto.
