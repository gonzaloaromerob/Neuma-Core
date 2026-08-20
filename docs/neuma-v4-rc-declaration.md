# NEUMA v4 — Declaración de Release Candidate

## Estado

**NEUMA v4 queda declarado Release Candidate (RC)** con fecha 2026-08-20, conforme al Gate humano explícitamente autorizado después de completar y publicar la preparación pre-RC mediante PR #26.

Esta declaración corresponde al **marco NEUMA v4**. No implica sincronización nominal de versiones entre sus componentes, no publica todavía una release v4 canónica y no autoriza cambios PROD.

## Baseline del candidato

- NEUMA Core vigente, deliberadamente pequeño y no enciclopédico.
- NEUMA Operations v3.8 como release interna estable y control plane transversal.
- ADR-007 y contrato modular v4 publicados.
- Suite de conformance M01–M15 / F01–F15.
- E2 integral publicada mediante PR #24.
- E3 representativo de falsación publicado mediante PR #25.
- Readiness, bundle, migración y rollback pre-RC publicados mediante PR #26 / merge SHA `e376ee508c95d24e96089e2cf338a86357ea1135`.
- `neuma-domain-law` v0.2-pilot.
- `neuma-domain-cybersecurity` v0.2-pilot.
- `neuma-workflow-audit` v0.2-pilot.

## Alcance de la declaración

La declaración RC significa que la arquitectura, composición, compatibilidad evaluada, activación mínima, recovery, postcondición, migración y rollback cuentan con evidencia suficiente para congelar el candidato y someterlo a observación final previa a una eventual release v4 canónica.

Durante RC:

1. no se amplía Core por conveniencia;
2. no se promueven automáticamente los módulos piloto;
3. no se fuerza NEUMA Operations a v4.0 por sincronización nominal;
4. no se amplía el catálogo de módulos sin evidencia material;
5. cambios estructurales solo proceden ante hallazgo material que invalide o debilite el candidato;
6. cualquier incompatibilidad futura no evaluada permanece `unknown` hasta evidencia gobernada;
7. release v4 canónica y PROD siguen sujetos a Gates humanos independientes.

## Evidencia que sustenta el RC

La declaración se apoya en:

- E1 completado;
- E2 con Core 20/20, modular 28/30 y cero fallos críticos;
- E3 con M02/F02 y M13/F13 elevados a Pass empírico;
- composición Derecho+Auditoría, Ciberseguridad+Auditoría y Derecho+Ciberseguridad validada;
- conflictos/hardening, fuente ausente/contradictoria, Gate especializado y postcondición validados;
- ausencia de evidencia material que exija modificar Core, Operations v3.8 o los pilotos v0.2;
- bundle, migración aditiva/reversible y rollback documentados y publicados.

## Congelación del candidato

A partir de esta declaración, el candidato queda funcionalmente congelado para fines de evaluación previa a release. Se permiten:

- correcciones documentales no materiales;
- reconciliaciones de proyecciones;
- evidencia adicional que no altere el contrato;
- fixes requeridos por hallazgos materiales debidamente trazados.

Cualquier cambio que altere contrato modular, precedencia, modelo de autoridad, compatibilidad, Core, Operations o estado de los módulos deberá reevaluar explícitamente la validez del RC.

## Exclusiones

Esta declaración **no**:

- publica una release v4 canónica;
- certifica ni estabiliza los módulos v0.2-pilot;
- concede licencias nuevas ni adopta Creative Commons;
- resuelve marca, derecho de autor, titularidad/procedencia, política de marca o legado patrimonial;
- modifica PROD ni autoriza despliegues;
- sustituye los Gates jurídicos o productivos aplicables.

## Rollback del RC

Ante un hallazgo crítico que invalide el candidato, aplicar `docs/neuma-v4-rc-rollback.md`. El punto pre-RC documentado permanece el merge SHA `5b0f97dae190351613a270c97bd7d255aba7bc6b`; la preparación pre-RC publicada por PR #26 permanece como evidencia histórica y no debe eliminarse.

## Próximo Gate

El siguiente Gate humano material es **publicar o no la release v4 canónica**. Antes de solicitarlo deben verificarse las postcondiciones del RC y confirmar que no surgieron hallazgos materiales que obliguen a reabrir arquitectura, compatibilidad, migración o rollback.
