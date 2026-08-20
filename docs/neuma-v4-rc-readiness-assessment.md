# NEUMA v4 — Evaluación de readiness previa a Release Candidate

## Estado

Evaluación interna previa al Gate humano de declaración RC v4. Este documento **no declara RC**, no publica una release v4, no certifica los módulos piloto y no autoriza cambios PROD.

Fecha: 2026-08-20.

Baseline evaluada:

- NEUMA Operations v3.8 — release interna estable de la familia v3;
- `neuma-domain-law` v0.2-pilot;
- `neuma-domain-cybersecurity` v0.2-pilot;
- `neuma-workflow-audit` v0.2-pilot;
- ADR-007 y contrato modular publicados;
- E2 publicada mediante PR #24;
- E3 publicada mediante PR #25 / merge SHA `5b0f97dae190351613a270c97bd7d255aba7bc6b`.

## Conclusión ejecutiva

La evidencia E1/E2/E3 satisface la parte arquitectónica y conductual del readiness. Las tres precondiciones documentales/operativas identificadas para el Gate RC quedaron preparadas en esta misma rama:

1. **bundle RC** definido en `docs/neuma-v4-rc-bundle.md`;
2. **migración v3.x → v4** documentada en `docs/neuma-v4-migration-v3-to-v4.md`;
3. **rollback RC** documentado en `docs/neuma-v4-rc-rollback.md`.

No se identifica evidencia que justifique modificar Core, Operations v3.8 o los módulos piloto. Una vez verificada la integridad del PR y reconciliadas sus proyecciones, el siguiente paso material es el **Gate humano de declaración RC v4**.

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
| Bundle RC | Satisfecho documentalmente | `docs/neuma-v4-rc-bundle.md` fija alcance, componentes, versiones y exclusiones. |
| Migración v3.x → v4 | Satisfecho documentalmente | `docs/neuma-v4-migration-v3-to-v4.md` define migración aditiva, reversible y desacoplada del versionado de Operations/módulos. |
| Rollback RC | Satisfecho documentalmente | `docs/neuma-v4-rc-rollback.md` fija punto de retorno, triggers, procedimiento y postcondición. |
| Documentación/proyecciones | En verificación final | La rama corrige referencias pre-E3/pre-v3.8; PR #26 está proyectado en Notion como draft pre-RC. |

## Bundle RC

La especificación canónica propuesta está en `docs/neuma-v4-rc-bundle.md`. El bundle incluye únicamente Core vigente, Operations v3.8, ADR-007, contrato modular, suite M01–M15/F01–F15, evidencia E2/E3, evaluación pre-RC, migración, rollback y los tres pilotos v0.2 como evidencia experimental.

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

Marca, derecho de autor, titularidad/procedencia, Creative Commons, política de marca y legado patrimonial permanecen separados. No se cierran ni reinterpretan por esta evaluación.

Para un RC técnico/metodológico interno, estos Gates no bloquean por sí solos si el RC no concede nuevas licencias, no adopta política de marca y no formula una nueva posición jurídica. Sí deben resolverse antes de cualquier acción de release cuyo alcance dependa materialmente de esas decisiones.

## Decisión preparada

Tras verificar el contenido de PR #26 y reconciliar su proyección, el siguiente Gate humano puede formularse de manera mínima:

> **Declarar o no NEUMA v4 como Release Candidate**, manteniendo Operations v3.8 estable y los tres módulos en v0.2-pilot, sin publicar todavía una release v4 canónica ni ejecutar cambios PROD.

Hasta que ese Gate sea decidido, el estado correcto sigue siendo **pre-RC / readiness completado, declaración pendiente**.
