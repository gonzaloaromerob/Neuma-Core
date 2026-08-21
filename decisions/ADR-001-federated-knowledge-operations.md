# ADR-001 — Arquitectura federada de conocimiento y operaciones NEUMA

## Estado
**Parcialmente reemplazada por ADR-010** desde el 21 de agosto de 2026. Sigue vigente como antecedente arquitectónico y para los principios de System of Record explícito, mínima duplicación y referencias verificables; deja de gobernar el rol operativo de Notion.

## Contexto histórico
Una fuente ficticia y no sensible en Google Drive fue utilizada para validar un modelo federado para NEUMA Operations. La evidencia fuente permanecía en Drive; GitHub conservaba decisiones versionables; Notion gestionaba seguimiento operativo.

Fuente piloto: https://docs.google.com/document/d/1BMk0qKFpSzwey6NafRE07cmMLkBa-06Eh8mWj6OQMOU/edit

## Decisión histórica
Adoptar una arquitectura federada con System of Record explícito por tipo de objeto:

- Evidencia y documentos fuente: repositorio documental autorizado.
- Decisiones técnicas y metodológicas versionables: GitHub.
- Estado operativo, riesgos, tareas, relaciones y seguimiento: Notion.

Evitar sincronización bidireccional automática y duplicación innecesaria. Preferir referencias cruzadas verificables.

## Evolución posterior
ADR-010 simplifica la topología y traslada a GitHub el estado operacional versionable apto para publicación. SharePoint permanece como SoR documental interno y proyección humana. Notion se conserva temporalmente como fuente legado hasta su limpieza posterior, pero ya no es SoR para trabajo nuevo.

## Riesgos históricos
- Divergencia entre copias.
- Escrituras en repositorio o rama equivocados.
- Exposición de información sensible en destinos no autorizados.
- Efectos secundarios automáticos de CI/CD, deployments, webhooks o bots.

## Controles que permanecen vigentes
- Resolver destino exacto antes de escribir.
- Clasificar sensibilidad antes de mover información.
- Verificar cada postcondición.
- Registrar fuente, destino, estado y efectos secundarios materiales.

## Evidencia de validación
El piloto integral Drive → GitHub → Notion fue ejecutado y verificado el 2026-08-18. El PR de control se cerró sin merge después de completar la prueba. La integración Vercel legado fue posteriormente retirada y el repositorio fue renombrado a `Neuma-Core`.