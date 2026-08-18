# NEUMA Core

Repositorio canónico versionado del marco NEUMA y sus componentes metodológicos, operativos y técnicos.

## Propósito
Conservar y evolucionar conocimiento de NEUMA que requiere control de versiones, trazabilidad y revisión explícita. GitHub actúa como **System of Record** para decisiones, arquitectura, metodología, skills, especificaciones y otros artefactos versionables.

## Estructura objetivo
- `decisions/` — Architecture Decision Records (ADR) y decisiones versionadas.
- `architecture/` — arquitectura conceptual y operativa.
- `docs/` — documentación consolidada y guías.
- `skills/` — especificaciones y artefactos relacionados con skills NEUMA.
- `research/` — investigación y análisis bajo control de versiones.
- `archive/legacy-website/` — clasificación histórica del antiguo sitio estático; sus archivos siguen preservados en el historial Git mientras se completa la migración.

## Gobierno
- Mantener un System of Record explícito por objeto.
- Evitar sincronización bidireccional automática con Notion u otros sistemas.
- Los cambios materiales deben pasar por rama/PR y revisión proporcional al riesgo.
- No almacenar secretos ni información sensible innecesaria en este repositorio público.
- GitHub no sustituye los repositorios documentales de evidencia u originales cuando estos tengan otro System of Record.

## Estado
`Neuma-Core` reemplaza el propósito histórico de `Neuma-WebSite`. El sitio web productivo actual se gestiona separadamente. La reestructuración del repositorio se realiza mediante PR antes de modificar `main`.
