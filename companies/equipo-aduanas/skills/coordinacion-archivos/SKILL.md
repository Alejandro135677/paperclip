---
name: coordinacion-archivos
description: Protocolo de reserva de archivos del Equipo Aduanas. Úsalo antes de leer en profundidad, modificar o revisar archivos para detectar choques entre agentes y detenerse a preguntar al usuario.
---

# Coordinación de archivos

Objetivo: que nunca dos agentes trabajen sobre el mismo archivo sin que el
usuario lo haya autorizado.

## 1. Declarar antes de tocar

Antes de trabajar sobre archivos, publica en la issue un comentario con esta
forma exacta:

```
ARCHIVOS: <lectura|escritura>
- ruta/relativa/archivo1
- ruta/relativa/archivo2
```

- El Investigador y el Revisor declaran siempre `lectura`.
- El Implementador declara `escritura` con la lista completa de archivos que
  va a crear, modificar o borrar. Si durante el trabajo necesita otro archivo,
  lo declara en un comentario nuevo **antes** de tocarlo.

## 2. Comprobar choques

Antes de empezar, revisa las issues abiertas del equipo (`in_progress`,
`in_review`, `blocked`) y sus comentarios `ARCHIVOS:`. Hay **choque** cuando:

- otro agente tiene declarada `escritura` sobre un archivo que tú vas a tocar, o
- tú vas a declarar `escritura` sobre un archivo que otro agente tiene
  declarado (en lectura o escritura) en una issue que no está cerrada.

Las tareas que forman parte del mismo pipeline (la issue del Implementador que
proviene del informe del Investigador, y su revisión) **no** chocan entre sí
mientras se ejecutan en orden: el Investigador termina antes de que empiece el
Implementador, y el Revisor empieza cuando el Implementador entrega.

## 3. Si hay choque: detenerse y preguntar

1. No toques el archivo. No intentes resolverlo por tu cuenta ni esperar en
   bucle.
2. Pasa tu issue a `blocked`.
3. Comenta en tu issue, mencionando al usuario:

```
CHOQUE DE ARCHIVOS — detenido
- Archivo(s): ruta/...
- Otra tarea/agente: <issue> / <agente>
- Lo que necesito hacer: ...
- Pregunta: ¿continúo, espero a que termine la otra tarea o se reasigna?
Desbloquea: el usuario (board), respondiendo en esta issue.
```

4. Comenta también en la otra issue avisando del choque, para que el otro
   agente se detenga y quede igualmente en `blocked` hasta que el usuario
   decida.
5. Retoma solo cuando el usuario responda. Su respuesta manda.

## 4. Liberar

Al cerrar o entregar la tarea, comenta `ARCHIVOS: liberados`.
