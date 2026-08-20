# NEUMA v4 — Conformance y roadmap de liberación

## Objetivo
Establecer una secuencia gobernada desde la baseline v3.7 hasta una NEUMA v4 integralmente sólida, validada y liberable, con foco en arquitectura modular, compatibilidad, conformance, pilotos y release controlado.

## Baseline
- NEUMA Operations v3.7 es la baseline canónica.
- ADR-006 formaliza resiliencia de estado, continuidad y recuperación.
- ADR-007 formaliza la especialización modular como dirección arquitectónica de v4.

## Etapas
1. **Contrato modular** — formalizar identidad, alcance, autoridad/SoR, riesgos, activación, composición, compatibilidad, deprecación y conformance.
2. **Resolución y composición** — definir precedencia, conflictos, fallback, activación mínima y coexistencia de módulos.
3. **Compatibilidad/versionado** — separar ciclos de Core, Operations y módulos; definir ranges de compatibilidad y criterios de major/minor.
4. **Conformance v4** — ampliar casos para composición, conflicto, fuentes faltantes/contradictorias, Gate humano, continuity/recovery y postcondición.
5. **Pilotos representativos** — validar el contrato con pocos módulos antes de ampliar catálogo. Criterio sugerido: un dominio de alta criticidad, uno técnico y un workflow transversal.
6. **Migración v3.x → v4** — documentar compatibilidad, rollback, deprecaciones y ausencia de dependencia obligatoria de módulos.
7. **Release Candidate** — validar bundle, documentación, ADR, conformance y postcondiciones; congelar cambios estructurales salvo hallazgo material.
8. **Release v4 canónica** — promover a `main` mediante Gate C explícito y reconciliar proyecciones gobernadas.
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
- Gates jurídicos pendientes: marca, derecho de autor, titularidad/procedencia, Creative Commons, política de marca y legado patrimonial.
- Merge de RC/release a `main`.
- Despliegue a PROD cuando exista efecto productivo.

## Principio operativo
No construir un catálogo amplio de módulos antes de validar el contrato con evidencia real. No refinar v4 por inercia: evolucionar ante evidencia material, manteniendo verdad → claridad → decisión → acción, verificación transversal y postcondición cuando corresponda.
