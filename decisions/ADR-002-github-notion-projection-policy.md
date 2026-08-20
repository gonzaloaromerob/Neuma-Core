# ADR-002 — Política de proyección GitHub → Notion

## Estado
Validada mediante piloto controlado; no constituye autorización general de automatización productiva.

## Decisión humana
Se seleccionó la opción B del Gate-002: **proyección unidireccional controlada GitHub → Notion**.

## Contexto
NEUMA Operations utiliza GitHub como System of Record para conocimiento versionable y Notion como capa operativa para proyectos, relaciones, riesgos, tareas, gates e índices. Una sincronización bidireccional automática introduciría conflictos de autoridad, duplicación, loops y efectos secundarios difíciles de compensar.

Fuente piloto: https://docs.google.com/document/d/1VKxZs1FfZvpOa5nTD8OsqcLErfIIdSIvs5B8Z3_LdSI/edit

## Política
1. **Dirección por defecto:** GitHub → Notion para proyectar metadatos, referencias o estados derivados de objetos canónicos versionados.
2. **Autoridad:** GitHub conserva autoridad sobre ADRs, metodología, código, skills, prompts, especificaciones y otros artefactos versionables alojados allí.
3. **Notion no sobrescribe GitHub automáticamente.** Cambios conceptuales originados en Notion se convierten en una solicitud explícita de cambio.
4. **Sin sincronización bidireccional oculta.** Cualquier flujo inverso requiere intención explícita y un nuevo Gate cuando sea material.
5. **Idempotencia:** usar referencias estables y evitar recrear registros cuando la proyección ya existe.
6. **Conflictos:** cuando el System of Record designado sea inequívoco, prevalece. Si dos fuentes aparentemente autorizadas discrepan materialmente y la precedencia no puede establecerse con evidencia suficiente, tratar como `conflict`: no escoger, fusionar, sobrescribir ni propagar heurísticamente; resolver primero la autoridad o escalar a decisión humana cuando sea material.
7. **Efectos secundarios:** antes de escribir se identifican CI/CD, deployments, webhooks, bots y notificaciones; después se verifican los efectos observados.
8. **Sensibilidad:** no mover contenido confidencial o restringido sin verificar autorización y permisos del destino.
9. **Pilotos:** capacidades nuevas se prueban primero con información ficticia/no sensible y aislamiento proporcional al riesgo.
10. **Reconciliación proactiva:** cuando un cambio material en GitHub pueda dejar una proyección gobernada obsoleta, NEUMA resuelve y ejecuta la reconciliación autorizada sin esperar un recordatorio humano. Si la proyección ya coincide, registra `no-op`; si diverge con autoridad clara, actualiza; si la autoridad es ambigua o existe trabajo independiente material, trata como `conflict`.
11. **Higiene proporcional:** al reconciliar una proyección, evaluar si existen registros derivados verificablemente obsoletos, duplicados, reemplazados o huérfanos. Preferir actualización, marcado, cierre o archivo reversible sobre eliminación. La limpieza destructiva o que pueda perder trabajo independiente conserva su Gate C concreto.

## Contrato mínimo de proyección
`SoR → identidad estable → resolución → create/update/no-op/conflict → verificación → trazabilidad → compensación`.

Una proyección puede incluir URL canónica, identificador, estado derivado, proyecto relacionado, versión/SHA y riesgo/tarea/gate asociado. No debe copiar contenido completo cuando una referencia al canónico satisface la necesidad operacional.

## Reversibilidad y compensación
La corrección de un registro derivado en Notion no reescribe el historial Git. Ante divergencia se corrige o marca el derivado desde el canónico. Cerrar o archivar residuos derivados preserva historia; no se borran automáticamente registros únicamente por antigüedad.

## Evidencia de validación
El 2026-08-18 se demostró idempotencia con ADR-002: dos resoluciones de la misma clave mantuvieron un único registro; una divergencia deliberada en Notion fue detectada y compensada desde GitHub sin modificar el canónico. El 2026-08-20 se reforzó el tratamiento de conflictos de autoridad conforme al ADR-005 y se añadió responsabilidad proactiva de reconciliación e higiene gobernada como parte de NEUMA Operations v3.6.