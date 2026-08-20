# NEUMA v4 — Evaluación de readiness previa a Release Candidate

## Estado

Evaluación interna que sustentó el Gate humano de declaración RC v4. El Gate fue autorizado y **NEUMA v4 fue declarado Release Candidate el 2026-08-20**.

Este documento conserva la evidencia pre-RC y su conclusión histórica. La declaración canónica está en `docs/neuma-v4-rc-declaration.md`.

La declaración RC no publica una release v4 canónica, no certifica los módulos piloto y no autoriza cambios PROD.

Fecha de evaluación: 2026-08-20.

Baseline evaluada:

- NEUMA Operations v3.8 — release interna estable de la familia v3;
- `neuma-domain-law` v0.2-pilot;
- `neuma-domain-cybersecurity` v0.2-pilot;
- `neuma-workflow-audit` v0.2-pilot;
- ADR-007 y contrato modular publicados;
- E2 publicada mediante PR #24;
- E3 publicada mediante PR #25 / merge SHA `5b0f97dae190351613a270c97bd7d255aba7bc6b`;
- preparación pre-RC publicada mediante PR #26 / merge SHA `e376ee508c95d24e96089e2cf338a86357ea1135`.

## Conclusión ejecutiva

La evidencia E1/E2/E3 satisfizo la parte arquitectónica y conductual del readiness. Las tres precondiciones documentales/operativas identificadas para el Gate RC quedaron publicadas:

1. **bundle RC** definido en `docs/neuma-v4-rc-bundle.md`;
2. **migración v3.x → v4** documentada en `docs/neuma-v4-migration-v3-to-v4.md`;
3. **rollback RC** documentado en `docs/neuma-v4-rc-rollback.md`.

No se identificó evidencia que justificara modificar Core, Operations v3.8 o los módulos piloto. Tras verificar la integridad de PR #26 y reconciliar sus proyecciones, el Gate humano fue autorizado y el marco pasó de **pre-RC** a **Release Candidate**.

## Readiness por criterio

| Criterio | Estado | Evidencia / límite |
|---|---|---|
| Core pequeño y no enciclopédico | Satisfecho | ADR-007, contrato modular, E2/E3; no surgió evidencia para ampliar Core. |
| Operations transversal | Satisfecho | v3.8 estable; composición modular añadida sin forks por dominio. |
| Contrato modular versionado | Satisfecho | Arquitectura/contrato publicados en `main`. |
| Activación mínima | Satisfecho | M02/F02 Pass en E3 por routing activo mínimo. |
| Composición dominio + workflow | Satisfecho | Derecho+Auditoría y Ciberseguridad+Auditoría validados; Derecho+Ciberseguridad probado en E3. |
| Conflictos / hardening | Satisfecho | Hardening permitido, weakening prohibido, conflicto material no resoluble → Gate humano. |
| Autoridad / SoR / frescura | Satisfecho proporcionalmente | Validado contractual y conductualmente; E3 mostró degradación ante fuente ausente/contradictoria. |
| Continuidad / recovery | Satisfecho | M13/F13 Pass empírico desde GitHub/Notion. |
| Postcondición | Satisfecho | E2 contractual y E3 con write → readback → postcondition. |
| Compatibilidad | Satisfecho para baseline evaluada | Pilotos v0.2 + Operations v3.8 compatibles por regla gobernada backward-compatible; futuras combinaciones no evaluadas siguen `unknown`. |
| Pilotos | Satisfecho para validación; no certificados | Los tres pilotos permanecen `v0.2-pilot`. |
| Bundle RC | Satisfecho | `docs/neuma-v4-rc-bundle.md` fija alcance, componentes, versiones y exclusiones. |
| Migración v3.x → v4 | Satisfecho | `docs/neuma-v4-migration-v3-to-v4.md` define migración aditiva, reversible y desacoplada del versionado de Operations/módulos. |
| Rollback RC | Satisfecho | `docs/neuma-v4-rc-rollback.md` fija punto de retorno, triggers, procedimiento y postcondición. |
| Documentación/proyecciones | Satisfecho para entrada a RC | PR #26 fue publicado y reconciliado antes del Gate. |
| Gate RC | Completado | Autorización humana explícita el 2026-08-20; declaración canónica en `docs/neuma-v4-rc-declaration.md`. |

## Bundle RC

La especificación canónica está en `docs/neuma-v4-rc-bundle.md`. El bundle incluye únicamente Core vigente, Operations v3.8, ADR-007, contrato modular, suite M01–M15/F01–F15, evidencia E2/E3, evaluación pre-RC, migración, rollback y los tres pilotos v0.2 como evidencia experimental.

Se excluyen deliberadamente módulos adicionales, promoción automática de pilotos, Operations v4.0 por sincronización nominal, nuevas licencias Creative Commons, política de marca, decisiones de titularidad/procedencia y cualquier cambio PROD.

## Migración v3.x → v4

La ruta documentada en `docs/neuma-v4-migration-v3-to-v4.md` mantiene:

- Operations v3.8 como release estable mientras el contrato transversal siga backward-compatible;
- módulos piloto desacoplados del lifecycle de Operations;
- especialización como capacidad resoluble/degradable, no dependencia universal;
- preservación de IDs/versiones, SoR, Gates, autorizaciones y siguiente acción;
- verificación de compatibilidad en vez de herencia nominal.

## Rollback RC

`docs/neuma-v4-rc-rollback.md` fija como punto de retorno pre-RC el SHA `5b0f97dae190351613a270c97bd7d255aba7bc6b` y exige preservar E2/E3, estado modular, Gates y proyecciones. El rollback del candidato no equivale a rollback PROD.

## Gates jurídicos

Marca, derecho de autor, titularidad/procedencia, Creative Commons, política de marca y legado patrimonial permanecen separados. No se cierran ni reinterpretan por esta evaluación ni por la declaración RC.

Para un RC técnico/metodológico interno, estos Gates no bloquean por sí solos si el RC no concede nuevas licencias, no adopta política de marca y no formula una nueva posición jurídica. Sí deben resolverse antes de cualquier acción de release cuyo alcance dependa materialmente de esas decisiones.

## Decisión resultante

El Gate humano de declaración RC fue aprobado. El estado correcto pasa a ser:

> **NEUMA v4 — Release Candidate**, con Operations v3.8 estable y los tres módulos especializados en v0.2-pilot, sin release v4 canónica y sin cambios PROD.

El siguiente Gate humano material es **publicar o no la release v4 canónica**, sujeto a verificar las postcondiciones del RC y la ausencia de hallazgos materiales nuevos.
