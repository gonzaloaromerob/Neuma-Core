# ADR-008 — Ejecución independiente de memoria y resolución canónica

## Estado
Propuesta de evolución backward-compatible de NEUMA Operations v3.8 hacia v3.9. Requiere revisión/merge gobernado antes de considerarse baseline canónica en `main`.

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

## Cambios de NEUMA Operations v3.9 candidatos
- `SKILL.md`: preflight explícito, no-memory execution y resolución canónica de plantillas/estándares.
- `references/project-bootstrap.md`: independencia de memoria transversal y bootstrap de proyectos.
- `references/personalization-independence.md`: memoria/personalización fuera de autoridad operacional.
- Se preserva `references/neuma-core.md` sin cambios respecto de la baseline Core de NEUMA 4.0.

## Compatibilidad
La evolución es backward-compatible con NEUMA 4.0 y Operations v3.8: fortalece resolución, verificación y postcondición sin cambiar A/B/C, mínimo privilegio, idempotencia, aislamiento contextual, autoridad de SoR ni Gates humanos. No autoriza sincronización bidireccional, publicación PROD ni modificación automática de todos los proyectos existentes.

## Postcondición requerida
Antes de cerrar esta evolución:
1. validar y empaquetar el bundle completo de NEUMA Operations v3.9;
2. revisar diff y compatibilidad con NEUMA 4.0;
3. abrir PR gobernado en `Neuma-Core`;
4. proyectar en Notion solo decisión/estado/PR y derivados operativos necesarios;
5. mantener `docs/neuma-4.0-release.md` sin cambios hasta que exista una decisión canónica que modifique la baseline publicada;
6. registrar cualquier limitación de instalación/despliegue de la skill: empaquetar no equivale a activar la nueva versión en el runtime.

## Relación con decisiones previas
Extiende ADR-002 (proyección GitHub → Notion), ADR-003 (bootstrap y artefactos), ADR-005 (gobierno de evolución y reconciliación proactiva) y ADR-006 (continuidad/recuperación). No sustituye ADR-007 ni modifica la arquitectura modular de NEUMA 4.0.
