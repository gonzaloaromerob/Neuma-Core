# NEUMA v4 — Conformance y evolución posterior a release

## Estado
NEUMA 4.0 fue publicada como release canónica el 2026-08-20. Este documento conserva únicamente el estado de conformance y los frentes que siguen materialmente abiertos después de la release.

## Baseline vigente
- NEUMA Core 4.0: canónico.
- NEUMA Operations: **v3.12** como release interna vigente de esta instalación; su lifecycle permanece desacoplado del número de versión de Core.
- ADR-006: resiliencia de estado, continuidad y recuperación.
- ADR-007: especialización modular.
- ADR-009: aprendizaje gobernado y proyección humana.
- ADR-010: consolidación operacional en GitHub y retiro progresivo de Notion.
- Módulos Derecho, Ciberseguridad y Auditoría: `v0.2-pilot` hasta evidencia y decisión específicas.

## Conformance alcanzada
- E1: completado.
- E2 integral: Core 20/20, modular 28/30 y cero fallos críticos.
- E3 representativo: completado; M02/F02 y M13/F13 pasaron empíricamente.
- Migración v3.x → v4: documentada como transición aditiva y reversible.
- Release Candidate y liberación 4.0: completadas el 2026-08-20.

Las evidencias de piloto/conformance que siguen justificando el estado de los módulos se mantienen bajo `docs/pilots/` y `docs/neuma-v4-module-conformance-suite.md` mientras dichos módulos permanezcan en piloto.

## Frentes abiertos
1. **Módulos piloto:** no ampliar catálogo ni declarar estabilidad sin evidencia real suficiente.
2. **Activación contextual de NEUMA Operations:** validar trigger recall, falsos positivos y falsos negativos en contexto limpio; ver `operations/STATE.md`.
3. **Operación web:** mantener CI/CD, Environment production, rollback y riesgos técnicos conforme a `operations/STATE.md` y `architecture/neuma-web-operations.md`.
4. **Consolidación de plataformas:** Notion queda como fuente legado temporal; no participa en trabajo nuevo. Su limpieza se hará en una iteración separada conforme a ADR-010.
5. **Gates jurídicos:** marca, derecho de autor, titularidad/procedencia, Creative Commons, política de marca y legado patrimonial siguen separados y sólo bloquean cuando una decisión concreta dependa de ellos.
6. **PROD / efectos externos materiales:** requieren Gate C específico cuando corresponda.

## Principio operativo
No refinar por inercia. Evolucionar ante evidencia material, con verdad → claridad → decisión → acción, postcondición verificable, topología mínima suficiente y mínima carga humana.