---
name: Equipo Aduanas
description: Equipo de tres agentes de IA (investigación, implementación y revisión) que trabaja sobre el sistema de seguimiento aduanero
slug: equipo-aduanas
schema: agentcompanies/v1
version: 0.1.0
license: MIT
goals:
  - Investigar, implementar y revisar cambios en el sistema de seguimiento aduanero con roles estrictamente separados
  - Evitar que dos agentes modifiquen el mismo archivo sin autorización humana
---

Equipo Aduanas trabaja sobre el sistema de seguimiento aduanero (declaraciones,
estados de despacho, documentos y alertas de envíos).

El coordinador es el usuario (board). Él crea y asigna las tareas. El trabajo
fluye en pipeline:

1. **Investigador** — analiza y documenta. Nunca edita archivos.
2. **Implementador** — es el único agente que modifica archivos.
3. **Revisor** — revisa los cambios y reporta riesgos. Nunca edita archivos.

Regla de oro: si dos agentes tocan (o van a tocar) el mismo archivo, ambos se
detienen y preguntan al usuario antes de continuar. Ver la skill
`coordinacion-archivos`.
