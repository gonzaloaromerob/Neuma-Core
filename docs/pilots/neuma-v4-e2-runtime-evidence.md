# NEUMA v4 — Evidencia E2 de runtime

## Estado
Evidencia conductual parcial obtenida en un runtime ChatGPT con `neuma-domain-law` y `neuma-domain-cybersecurity` resolubles. `neuma-workflow-audit` fue instalado por el usuario, pero no quedó expuesto al catálogo activo de la misma sesión; se registra como limitación de runtime, no como fallo lógico del módulo.

## Baseline
- NEUMA Operations activa: `v3.7`.
- Arquitectura modular y suite M01–M15 publicadas en `main`.
- Pilotos ejecutables iniciales publicados por PR #22.
- Fecha de observación: 2026-08-20.

## Hallazgos observables
### H1 — Disponibilidad de módulos no equivale a instalación declarada
El runtime resolvió `neuma-domain-law` y `neuma-domain-cybersecurity`, pero no expuso `neuma-workflow-audit` en la misma sesión inmediatamente después de su instalación. La arquitectura debe distinguir explícitamente **instalado/declarado**, **expuesto/resoluble** y **activo/usable**.

**Implicación transversal:** Operations necesita degradación explícita cuando un módulo materialmente requerido no esté resoluble, sin inventar disponibilidad ni sustituirlo silenciosamente.

### H2 — El artefacto ejecutable carecía de identidad/versionado consumible
Las especificaciones piloto `docs/pilots/*` declaraban `v0.1-pilot`, compatibilidad y deprecación, pero los `SKILL.md` ejecutables publicados por PR #22 no incluían esos datos ni un manifest portable asociado.

**Resultado:** F14/M14 (compatibilidad) y F15/M15 (deprecación/migración) no podían ejecutarse correctamente desde el artefacto cargado. Esto es un fallo de diseño del empaquetado piloto, no de Core.

**Corrección:** estandarizar `references/module.yaml` en cada módulo piloto y hacer que `SKILL.md` lo consulte cuando activación, composición, compatibilidad, recovery o deprecación sean materiales.

### H3 — Recovery modular es incompleto en Operations v3.7
Los módulos Derecho y Ciberseguridad ordenan preservar módulos activos y su estado material; Operations v3.7 preserva continuidad general, pero no define todavía un registro portable de módulos activos, versión, compatibilidad o estado degradado.

**Resultado:** F13/M13 queda `Partial` hasta que el control plane preserve explícitamente identidad/versionado de módulos materialmente activos en checkpoints de continuidad.

## Ejecución de fixtures disponible en esta sesión
| Fixture | Estado | Evidencia/resultado |
|---|---|---|
| F01 — Core no redefinible | Pass parcial observado | Derecho y Ciberseguridad preservan Core/Operations y prohíben debilitamiento. |
| F02 — Activación mínima | Inconcluso | El harness de esta conversación está probando varios módulos simultáneamente; no permite aislar auto-routing limpio sin nueva sesión/contexto. |
| F03 — Autoridad jurídica | Pass contractual observable | Derecho prioriza fuente oficial/caso SoR sobre fuente secundaria y exige vigencia. |
| F04 — Frescura técnica | Pass contractual observable | Ciberseguridad prioriza estado vivo/canónico y exige verificar versión/advisory. |
| F05 — Ciberseguridad + Auditoría | Bloqueado por runtime | `neuma-workflow-audit` no resoluble en catálogo activo de la sesión. |
| F06 — Derecho + Auditoría | Bloqueado por runtime | Mismo límite. |
| F07 — Conflicto resoluble | Parcial | Derecho/Ciberseguridad implementan endurecimiento válido; falta observarlo con workflow Auditoría activo. |
| F08 — Conflicto no resoluble | Pass contractual observable | Ambos módulos elevan Gate humano mínimo ante conflicto material sin precedencia suficiente. |
| F09 — Fuente faltante | Pass contractual observable | Ambos declaran gap y limitan conclusión; prohíben inventar estado/autoridad. |
| F10 — Fuente contradictoria | Pass contractual observable | Ambos exigen precedencia válida o divergencia explícita/Gate. |
| F11 — Gate especializado | Pass contractual observable | Acciones jurídicas/producción materiales requieren autorización concreta; autorización vigente no se re-pregunta. |
| F12 — Postcondición | Pass contractual observable | Éxito de herramienta no equivale a éxito material; se exige readback/postcondición. |
| F13 — Recovery | Partial | Módulos declaran qué preservar; Operations v3.7 carece de registro modular explícito. |
| F14 — Compatibilidad | Fail en v0.1 ejecutable | `SKILL.md` cargado no contenía versión/rango/estado de compatibilidad consumible. |
| F15 — Deprecación | Fail en v0.1 ejecutable | El artefacto cargado no podía distinguir versión canónica/reemplazada ni migración. |

No se calcula puntaje 30/30 mientras F02, F05, F06 y F07 no tengan ejecución aislada suficiente y hasta repetir F14/F15 con los manifests corregidos.

## Delta demostrado para NEUMA Operations
La evidencia ya justifica, como extensión transversal:
1. resolver módulos aplicables y **resolubles**, no asumir que instalación declarada implica disponibilidad;
2. activar el conjunto mínimo material;
3. leer identidad/versionado/compatibilidad desde un contrato portable del módulo;
4. distinguir compatible / incompatible / desconocido;
5. degradar explícitamente si un módulo requerido no está disponible o validado;
6. preservar módulos activos, versiones, estado de compatibilidad y Gates en continuidad/checkpoint;
7. mantener identidades separadas durante composición y aplicar hardening sin debilitamiento.

Este delta es **aditivo** respecto de v3.7 y puede mantenerse inactivo cuando no hay módulos especializados. La evidencia disponible favorece una evolución compatible `v3.8`, no un salto automático a `v4.0`; la decisión final de release debe confirmarse tras repetir F02/F05/F06/F07/F13–F15 con los pilotos corregidos y un runtime que exponga los tres módulos.

## Postcondición
E2 deja de ser una hipótesis puramente documental: existen fallos reproducibles de empaquetado/versionado y una limitación observable de disponibilidad de runtime. Las correcciones se incorporan en pilotos `v0.2-pilot`; la conformance completa sigue pendiente de reejecución en contexto limpio con los tres módulos resolubles.
