# NEUMA v4 — Conformance y roadmap de liberación

## Objetivo
Establecer una secuencia gobernada desde la familia v3.x hasta una NEUMA v4 integralmente sólida, validada y liberable, con foco en arquitectura modular, compatibilidad, conformance, pilotos y release controlado.

## Baseline
- NEUMA Operations v3.8 es la release interna estable vigente de la familia v3 y mantiene compatibilidad gobernada con los pilotos v0.2 evaluados.
- ADR-006 formaliza resiliencia de estado, continuidad y recuperación.
- ADR-007 formaliza la especialización modular como dirección arquitectónica de v4.
- E2 integral fue publicada mediante PR #24; E3 representativo de falsación fue publicado mediante PR #25.
- La preparación pre-RC fue publicada mediante PR #26 / merge SHA `e376ee508c95d24e96089e2cf338a86357ea1135`.
- El Release Candidate fue declarado mediante PR #27 / merge SHA `b0585e2e030e8cd65163686409ce6f47e598729b` y sus postcondiciones fueron verificadas mediante Issue #28.

## Etapas
1. **Contrato modular** — completado y publicado: identidad, alcance, autoridad/SoR, riesgos, activación, composición, compatibilidad, deprecación y conformance.
2. **Resolución y composición** — completado contractualmente y validado en E2/E3: precedencia, conflictos, fallback, activación mínima y coexistencia de módulos.
3. **Compatibilidad/versionado** — validado para Operations v3.8 + pilotos v0.2 mediante regla gobernada backward-compatible; futuras combinaciones no evaluadas permanecen `unknown` hasta evidencia.
4. **Conformance v4** — suite M01–M15 publicada; E2: Core 20/20, modular 28/30 y cero fallos críticos; E3 elevó M02/F02 y M13/F13 a Pass empírico.
5. **Pilotos representativos** — Derecho, Ciberseguridad y Auditoría permanecen en v0.2-pilot; no se amplía catálogo por anticipación.
6. **Migración v3.x → v4** — documentada como transición aditiva, reversible y desacoplada del versionado nominal de Operations/módulos.
7. **Release Candidate** — completado el 2026-08-20 mediante Gate humano explícito; postcondiciones verificadas y sin bloqueadores materiales nuevos.
8. **NEUMA 4.0 — release canónica** — **publicada el 2026-08-20 mediante Gate humano explícito**, manteniendo Operations v3.8 estable y los tres módulos en v0.2-pilot.
9. **PROD** — pendiente y separado; cualquier adopción, comunicación o despliegue con efecto externo material requiere Gate C adicional, postcondición y rollback aplicable.

## Criterios mínimos de liberación v4
NEUMA v4 no debe declararse liberable hasta demostrar, proporcionalmente:
- Core deliberadamente pequeño y no enciclopédico;
- Operations transversal sin forks por dominio;
- contrato modular versionado;
- composición de módulos sin ambigüedad material;
- precedencia/conflictos definidos;
- autoridad/SoR y frescura explícitos;
- conformance suficiente para módulos y composición;
- continuidad/recovery del estado material;
- compatibilidad y migración desde v3.x;
- ausencia de Gates humanos materiales no resueltos para el alcance del release;
- documentación y proyecciones gobernadas reconciliadas.

Estos criterios fueron satisfechos para el alcance de **NEUMA 4.0** mediante E1/E2/E3, preparación pre-RC, RC y verificación post-RC.

## Gates humanos previstos
- Aprobación de cambios arquitectónicos incompatibles con el contrato vigente.
- Selección de pilotos cuando implique prioridad, riesgo o exposición material.
- Aceptación de RPO/RTO cuando sean aplicables a un entorno real.
- Gates jurídicos pendientes: marca, derecho de autor, titularidad/procedencia, Creative Commons, política de marca y legado patrimonial. Estos permanecen separados y solo bloquean un alcance cuando una decisión de publicación/licenciamiento/marca dependa materialmente de ellos.
- Declaración de RC v4 — **completada el 2026-08-20**.
- Publicación de NEUMA 4.0 como release canónica — **completada el 2026-08-20**.
- Adopción/comunicación/despliegue PROD con efecto externo material — **pendiente y separado**.

## Estado de NEUMA 4.0
- E1: completado.
- E2: completado; Core 20/20, modular 28/30, cero fallos críticos.
- E3 representativo: completado y publicado; M02/F02 y M13/F13 Pass.
- Cambios materiales requeridos a Core, Operations o módulos por E3: ninguno.
- Bundle RC, migración y rollback: documentados y publicados mediante PR #26.
- Release Candidate: declarado mediante PR #27 y verificado mediante Issue #28.
- **NEUMA 4.0: release canónica publicada.**
- Operations: v3.8 estable.
- Módulos Derecho, Ciberseguridad y Auditoría: v0.2-pilot.
- Gates jurídicos: permanecen separados y abiertos según corresponda.
- PROD: sin cambios; pendiente de Gate específico.

## Principio operativo
No construir un catálogo amplio de módulos antes de validar el contrato con evidencia real. No refinar v4 por inercia: evolucionar ante evidencia material, manteniendo verdad → claridad → decisión → acción, verificación transversal y postcondición cuando corresponda.
