# ADR-001 — Arquitectura federada de conocimiento y operaciones NEUMA

## Estado
Validada mediante piloto controlado.

## Contexto
Una fuente ficticia y no sensible en Google Drive fue utilizada para validar un modelo federado para NEUMA Operations. La evidencia fuente permanece en Drive; GitHub conserva decisiones versionables; Notion gestiona seguimiento operativo.

Fuente piloto: https://docs.google.com/document/d/1BMk0qKFpSzwey6NafRE07cmMLkBa-06Eh8mWj6OQMOU/edit

## Decisión
Adoptar una arquitectura federada con System of Record explícito por tipo de objeto:

- Evidencia y documentos fuente: repositorio documental autorizado, inicialmente Google Drive en el piloto.
- Decisiones técnicas y metodológicas versionables: GitHub.
- Estado operativo, riesgos, tareas, relaciones y seguimiento: Notion.

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

## Evidencia de validación
El piloto integral Drive → GitHub → Notion fue ejecutado y verificado el 2026-08-18. El PR de control se cerró sin merge después de completar la prueba. La integración Vercel legado fue posteriormente retirada y el repositorio fue renombrado a `Neuma-Core`.
