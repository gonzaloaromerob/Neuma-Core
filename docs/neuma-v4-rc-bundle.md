# NEUMA v4 — Bundle propuesto para Release Candidate

## Estado

Especificación de bundle **pre-RC**. No declara Release Candidate, no publica una release v4, no estabiliza los módulos piloto y no autoriza cambios PROD.

Fecha de preparación: 2026-08-20.
Baseline Git de referencia previa a esta preparación: `5b0f97dae190351613a270c97bd7d255aba7bc6b`.

## Objetivo

Fijar el conjunto mínimo de componentes y evidencia que representarían NEUMA v4 en un eventual Release Candidate, evitando incluir artefactos no necesarios, catálogo anticipado de módulos o cambios de versionado sin evidencia.

## Componentes del bundle

### Control plane y arquitectura

1. **NEUMA Core vigente** — invariantes universales transportados por NEUMA Operations; no se amplía con conocimiento disciplinar.
2. **NEUMA Operations v3.8** — release interna estable de la familia v3 y control plane transversal usado en E2/E3.
3. **ADR-007** — `decisions/ADR-007-modular-specialization-architecture.md`.
4. **Contrato modular v4** — `architecture/neuma-v4-modular-specialization.md`.
5. **Roadmap/conformance** — `docs/neuma-v4-conformance-and-release-roadmap.md`.

### Conformance y evidencia

6. **Suite M01–M15 / F01–F15** — `docs/neuma-v4-module-conformance-suite.md`.
7. **Plan de validación de pilotos** — `docs/pilots/neuma-v4-pilot-validation-plan.md`.
8. **E2 integral** — `docs/pilots/neuma-v4-e2-integral-conformance-results.md`.
9. **E3 de falsación representativa** — `docs/pilots/neuma-v4-e3-falsification-results.md`.
10. **Evaluación pre-RC** — `docs/neuma-v4-rc-readiness-assessment.md`.
11. **Migración v3.x → v4** — `docs/neuma-v4-migration-v3-to-v4.md`.
12. **Rollback RC** — `docs/neuma-v4-rc-rollback.md`.

### Módulos piloto incluidos como evidencia experimental

13. **Derecho** — `neuma-domain-law` `v0.2-pilot`; manifest `skills/neuma-domain-law/references/module.yaml`.
14. **Ciberseguridad** — `neuma-domain-cybersecurity` `v0.2-pilot`; manifest `skills/neuma-domain-cybersecurity/references/module.yaml`.
15. **Auditoría** — `neuma-workflow-audit` `v0.2-pilot`; manifest `skills/neuma-workflow-audit/references/module.yaml`.

Los tres módulos se incluyen para demostrar la arquitectura validada. Su inclusión **no** los convierte en módulos estables ni certificados.

## Compatibilidad fijada por el bundle

Para el alcance evaluado:

- Operations v3.8 + Law v0.2-pilot: compatible por regla gobernada backward-compatible documentada en E2.
- Operations v3.8 + Cybersecurity v0.2-pilot: compatible por la misma regla.
- Operations v3.8 + Audit v0.2-pilot: compatible por la misma regla.

Los manifests piloto enumeran literalmente `v3.7`; el bundle no reescribe esa evidencia histórica ni convierte la regla gobernada en compatibilidad universal. Cualquier combinación futura no evaluada permanece `unknown` hasta nueva evidencia.

## Exclusiones deliberadas

No forman parte del bundle RC:

- módulos adicionales;
- promoción automática de pilotos a stable;
- Operations v4.0 por sincronización nominal;
- nuevas licencias Creative Commons;
- política de marca;
- decisiones de titularidad/procedencia;
- deploy o configuración PROD;
- conocimiento jurídico, técnico o de auditoría enciclopédico embebido en Core.

## Criterio de integridad

Un bundle RC es íntegro si cada componente listado es resoluble, sus identidades/versiones no son ambiguas, las referencias internas no contradicen el estado E3 y la migración/rollback mantienen una ruta reversible hacia la baseline pre-RC.

## Postcondición requerida antes del Gate RC

Antes de declarar RC debe verificarse que:

1. todos los paths versionados del bundle existen en la rama candidata;
2. Operations v3.8 y los tres módulos piloto conservan el estado/versionado declarado;
3. E2 y E3 son resolubles y no contienen fallos críticos no tratados;
4. migración y rollback son consistentes con el bundle;
5. no existe una afirmación de release v4, certificación de pilotos o cambio PROD implícita en el bundle.
