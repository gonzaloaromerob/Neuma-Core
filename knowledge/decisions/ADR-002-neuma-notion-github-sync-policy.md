# ADR-002 — Política de sincronización Notion ↔ GitHub

## Estado
Aprobada para piloto controlado; no autorizada para producción.

## Decisión humana
Se selecciona la opción B del Gate-002: **sincronización unidireccional controlada**.

## Contexto
NEUMA Operations utiliza GitHub como System of Record para conocimiento versionable y Notion como capa operativa para proyectos, relaciones, riesgos, tareas, gates e índices. Una sincronización bidireccional automática introduciría conflictos de autoridad, duplicación, loops y efectos secundarios difíciles de compensar.

Fuente de evidencia: https://docs.google.com/document/d/1VKxZs1FfZvpOa5nTD8OsqcLErfIIdSIvs5B8Z3_LdSI/edit

Gate operativo: Gate-002 — Validación humana de política Notion ↔ GitHub.

## Política aprobada
1. **Dirección por defecto:** GitHub → Notion para proyectar hacia la capa operativa metadatos, referencias o estados derivados de objetos canónicos versionados.
2. **Autoridad:** GitHub conserva la autoridad sobre ADRs, metodología, código, skills, prompts, especificaciones y otros artefactos versionables.
3. **Notion no sobrescribe GitHub automáticamente.** Cambios conceptuales originados en Notion deben convertirse en una solicitud explícita de cambio: issue, propuesta, rama/PR o nuevo ADR.
4. **Sin sincronización bidireccional oculta.** Cualquier flujo inverso requiere intención explícita, trazabilidad y un nuevo Gate cuando sea material.
5. **Idempotencia:** identificar objetos mediante referencias estables y evitar recrear registros cuando la proyección ya existe.
6. **Conflictos:** ante discrepancias, prevalece el System of Record designado; la divergencia se reporta y no se resuelve por sobrescritura automática.
7. **Efectos secundarios:** antes de escribir en GitHub se deben identificar CI/CD, deployments, webhooks, bots, notificaciones y otros disparadores; después de escribir se deben verificar los efectos observados.
8. **Sensibilidad:** no mover contenido confidencial o restringido a un nuevo sistema sin verificar autorización y permisos del destino.
9. **Pilotos:** cualquier automatización nueva debe probarse primero con información ficticia/no sensible, rama aislada y sin merge a `main` salvo autorización específica.

## Modelo mínimo de proyección GitHub → Notion
Una proyección puede incluir:
- URL canónica de GitHub;
- identificador del objeto (ADR, issue, PR, commit o archivo);
- estado operativo derivado;
- proyecto relacionado;
- fecha/versión cuando sea útil;
- riesgo, tarea o gate asociado.

No debe copiar automáticamente el contenido completo si una referencia al canónico satisface la necesidad operacional.

## Reversibilidad y compensación
La eliminación o corrección de un registro derivado en Notion no borra el historial Git. Si una proyección falla, se corrige o marca el objeto derivado; no se reescribe el canónico para forzar consistencia.

## Alcance actual
Esta decisión autoriza diseñar y ejecutar un **piloto aislado** de proyección unidireccional GitHub → Notion. No autoriza:
- merge a `main`;
- despliegue productivo;
- sincronización bidireccional;
- modificaciones automáticas de GitHub originadas desde Notion;
- movimientos de información sensible.

## Criterios de éxito del piloto
- autoridad de fuente inequívoca;
- proyección idempotente;
- relaciones Notion correctas;
- ausencia de sobrescritura del canónico;
- efectos secundarios detectados y registrados;
- verificación posterior de cada escritura;
- rollback/compensación definido para objetos derivados.
