# ADR-008 — Ejecución independiente de memoria y resolución canónica

## Estado
Aprobada / vigente. Integrada en `main` mediante PR #30, squash merge `e3284686575cf7c5f800df9faa92195496604e3e` el 21 de agosto de 2026. Las evoluciones posteriores fortalecen esta decisión sin modificar su alcance fundamental.

## Contexto
Un fallo operativo real mostró dos riesgos: sustituir una plantilla explícita por un artefacto “similar” sin resolver el estándar canónico y omitir el preflight de skills/autoridad/fuentes. El usuario no debe actuar como recordatorio externo para que NEUMA resuelva skills, SoR, proyecciones o derivados.

## Decisión
1. **Memoria fuera de la cadena operacional:** memoria del usuario/asistente no es fuente, autoridad, fallback, continuidad, autorización, estado, configuración, selector de skills/herramientas ni razón para omitir verificación. La conversación actual sí puede aportar contexto explícito; continuidad entre conversaciones se resuelve desde SoR/checkpoints.
2. **Preflight obligatorio:** antes de trabajo material resolver objetivo/resultado, skill específica, autoridad/SoR, fuente vigente y plantilla/estándar cuando el formato sea material.
3. **Plantilla canónica, no similitud:** “mi plantilla”, “plantilla oficial” o equivalente obliga a resolver y usar el estándar designado; un documento comparable no lo sustituye silenciosamente.
4. **Transversalidad de proyecto:** `project-bootstrap` debe operar sin memoria para estado crítico y resolver estándares/plantillas desde SoR. El rector no duplica NEUMA Core.
5. **Frontera Core/Operations:** memoria, personalización, tooling, SoR y resolución de artefactos pertenecen a Operations; NEUMA Core 4.0 no se modifica por esta regla.
6. **Reconciliación proactiva:** después de evolución material, revisar autónomamente los SoR/proyecciones gobernados de la topología vigente y ejecutar `create/update/no-op/conflict` según autoridad. Conforme a ADR-010, en esta instalación la postcondición nueva se centra en GitHub + SharePoint + SoR original aplicable; Notion queda legado.
7. **Sin propagación de contenido privado:** rectores, plantillas internas y contenido de proyectos permanecen en su SoR documental. GitHub recibe sólo conocimiento/estado versionable apto; SharePoint mantiene la proyección humana/documental.

## Cambios introducidos originalmente por NEUMA Operations v3.9
- preflight explícito;
- no-memory execution;
- resolución canónica de plantillas/estándares;
- bootstrap de proyectos independiente de memoria;
- preservación de `references/neuma-core.md` respecto de Core 4.0.

## Compatibilidad
Backward-compatible con NEUMA 4.0 y la familia Operations v3. Mantiene A/B/C, mínimo privilegio, idempotencia, aislamiento contextual, autoridad de SoR y Gates humanos.

## Postcondición histórica verificada
El bundle v3.9 fue validado, PR #30 fusionado y la limitación runtime quedó explícita: empaquetar una skill no equivale a activarla en todos los runtimes.

## Relación con decisiones posteriores
ADR-009 añade aprendizaje gobernado y proyección humana. ADR-010 simplifica la topología persistente y reemplaza la obligación de proyectar estado nuevo hacia Notion. Ninguna altera la exclusión de memoria ni la frontera Core/Operations.