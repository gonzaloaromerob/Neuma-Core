# NEUMA Operations v3.9 — Change note

## Estado
Candidata backward-compatible; propuesta mediante rama/PR gobernado. Empaquetar la skill no equivale a instalarla ni activarla en un runtime.

## Motivo
Corregir un fallo operativo real en el que se inició producción antes de resolver completamente el control plane: skill aplicable, System of Record, fuente vigente y plantilla canónica.

## Cambios
- Preflight NEUMA explícito antes de trabajo material.
- Memoria fuera de la cadena operacional y de continuidad.
- Resolución de plantilla/estándar canónico antes de usar artefactos comparables.
- Bootstrap transversal de proyectos sin dependencia de memoria.
- Reconciliación proactiva de GitHub/Notion/derivados después de cambios materiales, conforme a ADR-002 y ADR-005.

## Frontera arquitectónica
NEUMA Core 4.0 permanece sin cambios. El hardening pertenece a NEUMA Operations porque afecta runtime, memoria/personalización, skills, SoR, herramientas, plantillas y postcondiciones operacionales.

## Artefactos de la candidata
El bundle instalable se valida y distribuye por el mecanismo de Skills. GitHub conserva esta decisión, evidencia/versionado y documentación publicable; no se exige crear un repositorio separado `NEUMA-OPERATIONS`.

## Verificación
- bundle completo v3.9 validado con el validador oficial de Skills;
- `references/neuma-core.md` reconciliado con la baseline canónica de NEUMA 4.0, sin introducir la regla operacional dentro de Core;
- ADR-008 documenta la decisión y sus límites;
- `docs/neuma-4.0-release.md` permanece `no-op` hasta un Gate/merge que cambie la baseline publicada;
- Notion debe recibir únicamente la proyección operacional del ADR/PR/estado, no una copia canónica paralela.
