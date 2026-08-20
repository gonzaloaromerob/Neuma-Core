# NEUMA v4 — Conformance y roadmap de liberación

## Objetivo
Establecer una secuencia gobernada desde la familia v3.x hasta una NEUMA v4 integralmente sólida, validada y liberable, con foco en arquitectura modular, compatibilidad, conformance, pilotos y release controlado.

## Baseline
- NEUMA Operations v3.8 es la release interna estable vigente de la familia v3 y mantiene compatibilidad gobernada con los pilotos v0.2 evaluados.
- ADR-006 formaliza resiliencia de estado, continuidad y recuperación.
- ADR-007 formaliza la especialización modular como dirección arquitectónica de v4.
- E2 integral fue publicada mediante PR #24; E3 representativo de falsación fue publicado mediante PR #25.

## Etapas
1. **Contrato modular** — completado y publicado: identidad, alcance, autoridad/SoR, riesgos, activación, composición, compatibilidad, deprecación y conformance.
2. **Resolución y composición** — completado contractualmente y validado en E2/E3: precedencia, conflictos, fallback, activación mínima y coexistencia de módulos.
3. **Compatibilidad/versionado** — validado para Operations v3.8 + pilotos v0.2 mediante regla gobernada backward-compatible; futuras combinaciones no evaluadas permanecen `unknown` hasta evidencia.
4. **Conformance v4** — suite M01–M15 publicada; E2: Core 20/20, modular 28/30 y cero fallos críticos; E3 elevó M02/F02 y M13/F13 a Pass empírico.
5. **Pilotos representativos** — Derecho, Ciberseguridad y Auditoría permanecen en v0.2-pilot; no se amplía catálogo por anticipación.
6. **Migración v3.x → v4** — preparar y verificar compatibilidad, rollback, deprecaciones y ausencia de dependencia obligatoria de módulos antes de declarar RC.
7. **Release Candidate** — validar bundle, documentación, ADR, conformance, migración, rollback y postcondiciones; congelar cambios estructurales salvo hallazgo material. Su declaración requiere Gate humano explícito.
8. **Release v4 canónica** — publicación versionada mediante Gate C explícito y reconciliación de proyecciones gobernadas.
9. **PROD** — desplegar únicamente donde aplique y con Gate C adicional si existe efecto productivo; verificar postcondición y rollback.

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

## Gates humanos previstos
- Aprobación de cambios arquitectónicos incompatibles con el contrato vigente.
- Selección de pilotos cuando implique prioridad, riesgo o exposición material.
- Aceptación de RPO/RTO cuando sean aplicables a un entorno real.
- Gates jurídicos pendientes: marca, derecho de autor, titularidad/procedencia, Creative Commons, política de marca y legado patrimonial. Estos permanecen separados y solo bloquean el alcance del release cuando una decisión de publicación/licenciamiento/marca dependa materialmente de ellos.
- Declaración de RC v4.
- Publicación de release v4 canónica.
- Despliegue a PROD cuando exista efecto productivo.

## Estado de readiness tras E3
- E1: completado.
- E2: completado; Core 20/20, modular 28/30, cero fallos críticos.
- E3 representativo: completado y publicado; M02/F02 y M13/F13 Pass.
- Cambios materiales requeridos a Core, Operations o módulos por E3: ninguno.
- Residuos técnicos antes de Gate RC: documentar bundle RC, ruta de migración v3.x → v4 y rollback verificable; reconciliar las referencias documentales afectadas.

## Principio operativo
No construir un catálogo amplio de módulos antes de validar el contrato con evidencia real. No refinar v4 por inercia: evolucionar ante evidencia material, manteniendo verdad → claridad → decisión → acción, verificación transversal y postcondición cuando corresponda.
