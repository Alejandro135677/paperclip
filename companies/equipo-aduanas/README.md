# Equipo Aduanas

Equipo de tres agentes de IA para el sistema de seguimiento aduanero,
empaquetado como una compañía [Agent Companies](https://agentcompanies.io/specification)
para [Paperclip](https://github.com/paperclipai/paperclip).

## Cómo trabaja

Tú (el usuario/board) coordinas y asignas tareas. El flujo es un pipeline:

```
Usuario ──▶ Investigador ──▶ Implementador ──▶ Revisor ──▶ Usuario (aprueba)
                                   ▲               │
                                   └── riesgos ────┘
```

Si dos agentes tocan el mismo archivo, ambos se detienen (`blocked`) y te
preguntan en la issue. Ver [`skills/coordinacion-archivos`](skills/coordinacion-archivos/SKILL.md).

## Organigrama

| Agente | Rol | Reporta a | Puede editar | Skills |
| --- | --- | --- | --- | --- |
| Investigador | Investiga y documenta | — (usuario) | No | paperclip, coordinacion-archivos |
| Implementador | Implementa cambios | Investigador | **Sí** (único) | paperclip, coordinacion-archivos |
| Revisor | Revisa y reporta riesgos | Investigador | No | paperclip, coordinacion-archivos |

- **Investigador:** analiza código, datos y normativa; entrega un informe con
  archivos implicados y una recomendación, y crea la tarea del Implementador.
- **Implementador:** declara los archivos que va a modificar, implementa,
  prueba y entrega al Revisor.
- **Revisor:** reporta riesgos por severidad (datos aduaneros, normativa,
  seguridad, regresiones) y devuelve al Implementador si hay bloqueantes.

## Primeros pasos

```sh
paperclipai company import --from companies/equipo-aduanas
```

## Referencias

- Especificación: https://agentcompanies.io/specification
- Paperclip: https://github.com/paperclipai/paperclip
