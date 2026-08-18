# ADR-001 — NEUMA Knowledge & Operations Pilot

## Estado
Propuesto / piloto controlado

## Contexto
Una fuente ficticia y no sensible en Google Drive describe un modelo federado para NEUMA Operations. La evidencia fuente permanece en Drive; GitHub conserva la decisión versionada; Notion gestiona seguimiento operativo.

Fuente: https://docs.google.com/document/d/1BMk0qKFpSzwey6NafRE07cmMLkBa-06Eh8mWj6OQMOU/edit

## Decisión
Adoptar una arquitectura federada con System of Record explícito por tipo de objeto:

- Evidencia y documentos fuente: Google Drive.
- Decisiones técnicas y metodológicas versionables: GitHub.
- Estado operativo, riesgos, tareas y seguimiento: Notion.

Evitar sincronización bidireccional automática y duplicación innecesaria. Preferir referencias cruzadas verificables.

## Riesgos
- Divergencia entre copias.
- Escrituras en repositorio o rama equivocados.
- Exposición de información sensible en destinos no autorizados.
- Efectos secundarios automáticos de CI/CD, deployments, webhooks o bots.

## Controles
- Resolver destino exacto antes de escribir.
- Clasificar sensibilidad antes de mover información.
- Verificar cada postcondición.
- Registrar fuente, destino, estado y efectos secundarios materiales.

## Piloto
Rama: `neuma-pilot-integral`.

Este ADR es parte de un piloto integral y no debe fusionarse a `main` sin autorización explícita.
