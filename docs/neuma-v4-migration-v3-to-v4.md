# NEUMA v4 — Migración desde la familia v3.x

## Estado

Plan de migración **pre-RC**. Describe la transición del marco NEUMA hacia la arquitectura v4 validada sin asumir sincronización forzada de números de versión. No declara RC, no publica una release v4 y no autoriza PROD.

## Principio

NEUMA v4 es una evolución de la arquitectura integral del marco. No implica por sí misma que cada componente deba adoptar versión mayor `v4.0`.

La evidencia E2/E3 muestra que NEUMA Operations v3.8 puede actuar como control plane transversal de la arquitectura modular v4 de forma backward-compatible dentro de la familia v3. Por tanto, la migración observada es **aditiva y reversible**, no una sustitución disruptiva de Operations.

## Baseline de origen

- NEUMA Operations v3.8 estable.
- Core vigente transportado por Operations.
- Pilotos `neuma-domain-law`, `neuma-domain-cybersecurity` y `neuma-workflow-audit` en `v0.2-pilot`.
- Arquitectura modular, ADR-007, contrato, suite M01–M15 y evidencia E2/E3 publicadas en Neuma-Core.

## Estado objetivo del RC

- misma Operations v3.8 estable;
- mismo Core sin expansión disciplinar;
- arquitectura modular v4 reconocida como contrato del marco;
- módulos piloto conservados como pilotos, desacoplados del versionado de Operations;
- bundle RC explícito y verificable;
- migración y rollback documentados;
- ningún cambio PROD implícito.

## Pasos de migración

1. **Resolver baseline viva.** Confirmar Operations, Core, módulos instalados/resolubles y autoridad de los artefactos del bundle.
2. **Fijar bundle.** Usar `docs/neuma-v4-rc-bundle.md` como inventario mínimo de componentes del candidato.
3. **Revalidar compatibilidad.** Tratar como compatibles únicamente las combinaciones cubiertas por evidencia gobernada; futuras versiones no evaluadas quedan `unknown`.
4. **Preservar estado modular.** Para trabajo material, conservar IDs/versiones, compatibilidad, SoR, Gates, autorizaciones, hallazgos y siguiente acción.
5. **Adoptar contrato modular.** Permitir resolución/activación mínima de módulos sin convertirlos en dependencias universales.
6. **Mantener degradación segura.** Un runtime sin un módulo especializado materialmente requerido debe limitar/degradar la conclusión; un runtime sin necesidad de especialización debe seguir operando NEUMA genérico.
7. **Congelar cambios estructurales durante RC.** Tras declarar RC, aceptar únicamente correcciones justificadas por hallazgo material hasta promoción o descarte del candidato.
8. **Verificar postcondición.** Confirmar ausencia de doble autoridad, versiones ambiguas, cambios de licencia implícitos o promoción accidental de pilotos.

## Compatibilidad y versionado

- `NEUMA v4` identifica la arquitectura integral del marco.
- `NEUMA Operations v3.8` conserva su identidad y lifecycle propio.
- `v0.2-pilot` conserva el estado experimental de cada módulo.
- No existe obligación de publicar Operations v4.0 para declarar un RC del marco si no hay cambio incompatible en Operations.
- Una futura incompatibilidad contractual sí deberá evaluarse bajo la política de versionado y podrá exigir major correspondiente.

## Datos y estado que deben preservarse

La migración no debe perder:

- autoridad/SoR y fuentes materiales;
- decisiones y ADR aplicables;
- IDs y versiones de módulos;
- compatibilidad resoluble;
- Gates abiertos;
- autorizaciones y límites;
- hallazgos/remediaciones de auditoría;
- rollback state y siguiente acción segura.

## Gates jurídicos

Los Gates de marca, derecho de autor, titularidad/procedencia, Creative Commons, política de marca y legado patrimonial permanecen separados. Esta migración no concede licencias, no resuelve titularidad ni crea política de marca.

## Criterio de éxito

La migración es satisfactoria cuando un runtime puede operar el bundle RC manteniendo Core pequeño, Operations transversal, módulos desacoplados y activación mínima; y puede regresar a la baseline pre-RC sin pérdida material de autoridad, estado o trazabilidad.
