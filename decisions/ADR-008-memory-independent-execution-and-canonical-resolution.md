# ADR-008 — Ejecución independiente de memoria y resolución canónica

## Estado
Aprobada / vigente. Integrada en `main` mediante PR #30, squash merge `e3284686575cf7c5f800df9faa92195496604e3e` el 21 de agosto de 2026. La baseline operacional resultante fue NEUMA Operations v3.9; las evoluciones posteriores pueden fortalecer esta decisión sin modificar su alcance fundamental.

## Contexto
Un fallo operativo real mostró dos riesgos relacionados: (1) sustituir una plantilla explícitamente pedida por un artefacto "similar" sin resolver primero el estándar canónico; y (2) omitir el preflight de skills/autoridad/fuentes antes de producir un entregable. El usuario no debe actuar como recordatorio externo para que NEUMA resuelva skills, Systems of Record, proyecciones o derivados afectados.

La corrección debe ser transversal y portable, sin depender de memoria de ChatGPT, campos de personalización ni de que cada proyecto replique manualmente reglas metodológicas.

## Decisión
1. **Memoria fuera de la cadena operacional:** la memoria del usuario o del asistente no se utiliza como fuente, autoridad, fallback, continuidad, autorización, estado, configuración, selección de skills/herramientas, identificación de plantillas ni razón para omitir verificación. La conversación actual sí puede aportar contexto explícito; la continuidad entre conversaciones se resuelve desde SoR, checkpoints o fuentes recuperables.
2. **Preflight obligatorio para trabajo material:** antes de ejecutar, resolver objetivo/resultado, skill más específica aplicable, autoridad/SoR, fuente vigente y plantilla/estándar canónico cuando el formato sea material. Preguntar solo si una ambigüedad material no puede resolverse desde evidencia autorizada.
3. **Plantilla canónica, no similitud:** expresiones como “mi plantilla”, “la plantilla”, “plantilla oficial” o equivalente obligan a resolver el estándar designado. Un documento comparable puede servir como referencia editorial, pero nunca sustituye silenciosamente a la plantilla autorizada.
4. **Transversalidad de proyecto:** `project-bootstrap` debe asegurar que todo proyecto gobernado por NEUMA opere sin dependencia de memoria para estado crítico y resuelva sus estándares/plantillas desde el SoR correspondiente. Las Project Instructions pueden incluir una cláusula mínima de independencia de memoria cuando la plataforma lo requiera; el rector no debe duplicar NEUMA Core.
5. **Frontera Core/Operations:** esta regla se implementa en NEUMA Operations y sus referencias operativas. NEUMA Core 4.0 no se modifica por este cambio, porque memoria, personalización, tooling, SoR y resolución de artefactos pertenecen a la capa operacional.
6. **Reconciliación proactiva:** después de una evolución material de la skill, revisar autónomamente GitHub, Notion y demás proyecciones gobernadas conforme a ADR-002/ADR-005; ejecutar `create/update/no-op/conflict` según autoridad y no esperar solicitud explícita del usuario.
7. **Sin propagación de contenido privado:** los rectores, plantillas internas o contenido de proyectos permanecen en su SoR documental. GitHub conserva la decisión/versionado publicable y Notion únicamente la proyección operacional necesaria.

## Cambios introducidos por NEUMA Operations v3.9
- `SKILL.md`: preflight explícito, no-memory execution y resolución canónica de plantillas/estándares.
- `references/project-bootstrap.md`: independencia de memoria transversal y bootstrap de proyectos.
- `references/personalization-independence.md`: memoria/personalización fuera de autoridad operacional.
- `references/neuma-core.md` se preservó sin cambios respecto de la baseline Core de NEUMA 4.0.

## Compatibilidad
La evolución es backward-compatible con NEUMA 4.0 y Operations v3.8: fortalece resolución, verificación y postcondición sin cambiar A/B/C, mínimo privilegio, idempotencia, aislamiento contextual, autoridad de SoR ni Gates humanos. No autoriza sincronización bidireccional, publicación PROD ni modificación automática de todos los proyectos existentes.

## Postcondición verificada
1. bundle completo v3.9 validado y empaquetado;
2. diff y compatibilidad con NEUMA 4.0 revisados;
3. PR #30 fusionado a `main`;
4. decisión/estado proyectados en Notion;
5. `docs/neuma-4.0-release.md` permaneció sin cambios;
6. se mantuvo explícita la limitación: empaquetar una skill no equivale a activarla en todos los runtimes.

## Relación con decisiones posteriores
ADR-009 extiende esta decisión con aprendizaje gobernado, proyección humana operacional y QA cruzado entre SoR/proyecciones. No altera la exclusión de memoria ni la frontera Core/Operations.

## Relación con decisiones previas
Extiende ADR-002 (proyección GitHub → Notion), ADR-003 (bootstrap y artefactos), ADR-005 (gobierno de evolución y reconciliación proactiva) y ADR-006 (continuidad/recuperación). No sustituye ADR-007 ni modifica la arquitectura modular de NEUMA 4.0.
