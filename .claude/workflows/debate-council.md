# Saved workflow prompt — debate-council

Este archivo NO intenta fijar una API JavaScript interna de Claude Code, porque Anthropic indica que Claude Code escribe el script de workflow según la versión instalada y puede guardarlo desde `/workflows`.

Úsalo como especificación para que Claude Code genere el workflow dinámico real:

```text
ultracode: escribe y ejecuta un workflow dinámico reutilizable llamado debate-council.

Input del workflow: args debe contener thesis, context, objective, evidence_paths opcional, require_web opcional, max_agents opcional.

Fases:
1. thesis framing
2. evidence collection en paralelo
3. independent positions en paralelo
4. cross examination
5. evidence audit
6. logic critique
7. bias detection
8. final arbitration
9. write markdown and json outputs

Usa los subagents definidos en .claude/agents/ y la skill .claude/skills/debate-council/SKILL.md.

Aplica las restricciones de dynamic workflows: el script solo coordina; los agentes leen/escriben/ejecutan herramientas. Mantén concurrencia moderada y permite al usuario aprobar el plan antes de correr.
```

Cuando el workflow corra correctamente, abre `/workflows`, selecciona la corrida y presiona `s` para guardarla como comando real en `.claude/workflows/`.
