# NEUMA v4 — Rollback del Release Candidate

## Estado

Plan de rollback **pre-RC** para el bundle NEUMA v4. No declara RC, no publica release v4 y no define rollback PROD.

## Objetivo

Permitir abandonar un eventual RC v4 y volver a la baseline pre-RC sin pérdida material de autoridad, estado, trazabilidad o capacidad de operación bajo NEUMA Operations v3.8.

## Punto de retorno

Baseline Git de referencia previa a la preparación RC: `5b0f97dae190351613a270c97bd7d255aba7bc6b`.

Ese SHA contiene E3 publicada mediante PR #25 y representa el punto de retorno documental/técnico previo a los artefactos de readiness RC preparados posteriormente.

## Qué se revierte

El rollback RC revierte únicamente la **adopción del bundle candidato** como estado RC. No implica:

- downgrade destructivo de Operations;
- eliminación de evidencia E1/E2/E3;
- desinstalación automática de módulos piloto;
- reversión de decisiones jurídicas;
- rollback de PROD.

## Procedimiento

1. **Detener promoción.** No promover el candidato a release v4 ni iniciar adopción PROD.
2. **Identificar causa.** Registrar el hallazgo material que invalida o suspende el RC.
3. **Restaurar autoridad pre-RC.** Volver a considerar el estado de `main` en `5b0f97dae190351613a270c97bd7d255aba7bc6b` como baseline de referencia para el marco previo al RC.
4. **Preservar evidencia.** Mantener el branch/PR/artefactos fallidos como evidencia histórica; no reescribir E2/E3 para hacerlos coincidir con el rollback.
5. **Preservar estado modular.** Mantener IDs/versiones, SoR, Gates, autorizaciones, hallazgos, decisiones y siguiente acción segura que sigan siendo válidos.
6. **Re-resolver runtime.** Tras rollback, volver a comprobar qué módulos están instalados, resolubles, compatibles y activos; no asumir que el runtime conserva exactamente el estado previo.
7. **Reconciliar proyecciones.** Marcar el RC como descartado/suspendido donde corresponda y asegurar que Notion u otros derivados no lo sigan presentando como vigente.
8. **Verificar postcondición.** Confirmar baseline pre-RC resoluble, Operations v3.8 vigente, módulos piloto sin promoción accidental y ausencia de doble autoridad canónica.

## Triggers de rollback

Rollback o suspensión del RC procede si aparece cualquiera de los siguientes eventos materiales:

- fallo crítico de Core o de frontera de autorización;
- incompatibilidad no gobernada entre Operations y módulos necesarios;
- pérdida o ambigüedad de autoridad/SoR;
- recovery no reproducible para estado material;
- weakening de controles por composición;
- migración no reversible;
- documentación del bundle que produzca doble autoridad o promoción accidental de pilotos;
- conflicto jurídico material que afecte directamente el alcance del RC y no pueda aislarse.

## Verificación del rollback

Resultado esperado:

- `main` pre-RC sigue siendo resoluble;
- E3 permanece publicada como evidencia válida;
- Operations v3.8 sigue estable;
- Law/Cybersecurity/Audit siguen `v0.2-pilot`;
- no existe una release v4 canónica activa derivada del candidato descartado;
- las proyecciones operativas reflejan el estado real;
- cualquier Gate abierto conserva dueño y siguiente acción.

## Límite

Este documento gobierna rollback **del candidato metodológico/documental v4**. Un futuro deploy PROD requiere un plan operativo específico, smoke tests y rollback propios bajo Gate C separado.
