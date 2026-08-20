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

**NEUMA v4 todavía no debe declararse RC.** La evidencia E1/E2/E3 satisface la parte arquitectónica y conductual del readiness, pero quedan tres precondiciones documentales/operativas concretas antes del Gate RC:

1. definir el **bundle RC** con identidades/versiones exactas;
2. documentar la **migración v3.x → v4** sin asumir que Operations deba saltar a v4.0 ni que los módulos piloto deban estabilizarse;
3. documentar un **rollback verificable** para revertir la adopción del bundle RC sin perder estado material, Gates o compatibilidad.

No se identifica evidencia que justifique modificar Core, Operations v3.8 o los módulos piloto para cerrar estas precondiciones.

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
| Bundle RC | Pendiente | Debe fijar componentes, versiones, documentos y evidencia exacta. |
| Migración v3.x → v4 | Pendiente | Debe documentarse como evolución del marco, no como sincronización forzada de números de versión. |
| Rollback RC | Pendiente | Debe preservar baseline previa, estado material, Gates y compatibilidad. |
| Documentación/proyecciones | En cierre | Se corrigen en esta rama referencias pre-E3/pre-v3.8; Notion ya refleja E3. |

## Bundle RC propuesto — alcance mínimo

El bundle RC debería contener únicamente artefactos necesarios para representar la arquitectura v4 validada:

1. NEUMA Core vigente — invariantes universales sin expansión disciplinar.
2. NEUMA Operations v3.8 — control plane estable y backward-compatible de la familia v3.
3. ADR-007 — arquitectura de especialización modular.
4. Contrato de especialización modular v4.
5. Suite formal M01–M15 y fixtures F01–F15.
6. Evidencia E2 integral.
7. Evidencia E3 de falsación representativa.
8. Contratos/manifests de los tres pilotos v0.2, **como pilotos**, no como módulos certificados o estables.
9. Documento de migración v3.x → v4.
10. Documento de rollback del bundle RC.

No se incluye un catálogo adicional de módulos ni conocimiento disciplinar enciclopédico.

## Principios de migración v3.x → v4

La migración debe ser **aditiva y reversible** para la baseline observada:

- NEUMA v4 describe la arquitectura integral del marco; no obliga a renombrar Operations v3.8 como Operations v4.0.
- Operations v3.8 permanece válida mientras el contrato transversal siga backward-compatible.
- Los módulos piloto siguen desacoplados del versionado de Core/Operations.
- Un runtime sin módulos especializados debe seguir pudiendo operar NEUMA genérico; la especialización es resoluble y degradable, no una dependencia universal obligatoria.
- Al adoptar el bundle RC, preservar IDs/versiones de módulos, compatibilidad, SoR, Gates y siguiente acción en checkpoints materiales.
- Versiones futuras no evaluadas no heredan compatibilidad por similitud nominal.

## Rollback propuesto

Rollback del bundle RC significa volver a la baseline pre-RC sin pérdida de autoridad ni estado:

1. conservar como punto de retorno el `main` previo al eventual merge RC;
2. no sobrescribir ni eliminar Operations v3.8 ni los manifests piloto al preparar RC;
3. si la adopción RC revela incompatibilidad material, restaurar el conjunto documental/contractual anterior y marcar el RC como no promovible;
4. preservar checkpoints de módulos activos, SoR, Gates y decisiones tomadas durante la evaluación;
5. re-resolver disponibilidad/compatibilidad tras rollback en vez de asumir que el runtime conserva el mismo estado;
6. verificar postcondición: baseline previa resoluble, sin doble autoridad canónica y sin proyecciones divergentes.

No se define rollback PROD en este documento; PROD requiere Gate separado y su propio plan operativo cuando aplique.

## Gates jurídicos

Marca, derecho de autor, titularidad/procedencia, Creative Commons, política de marca y legado patrimonial permanecen separados. No se cierran ni reinterpretan por esta evaluación.

Para un RC técnico/metodológico interno, estos Gates no bloquean por sí solos si el RC no concede nuevas licencias, no adopta una política de marca y no formula una nueva posición jurídica. Sí deben resolverse antes de cualquier acción de release cuyo alcance dependa materialmente de esas decisiones.

## Decisión preparada

Una vez que bundle, migración y rollback estén documentados y verificados, el siguiente Gate humano podrá formularse de forma mínima:

> **Declarar o no NEUMA v4 como Release Candidate**, manteniendo Operations v3.8 estable y los tres módulos en v0.2-pilot, sin publicación de release v4 ni cambio PROD.

Hasta entonces, el estado correcto es **pre-RC / readiness en preparación**.
