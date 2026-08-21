# NEUMA — Estado operacional consolidado

**Fecha de corte:** 2026-08-21

Este archivo es la superficie operacional persistente para estado, riesgos, tareas, Gates y referencias de evidencia aptas para GitHub. Los originales documentales siguen en sus respectivos Systems of Record.

## 1. Proyectos / workstreams

### Piloto integral NEUMA Operations
- Estado: `Cerrado`.
- Objetivo: validar gobierno, trazabilidad y verificación de un flujo multiapp federado sin duplicación indiscriminada.
- Resultado operativo: la arquitectura federada, los Decision Gates y la política de proyección fueron validados; posteriormente la topología se simplificó mediante ADR-010 y Notion fue retirado completamente de NEUMA.
- Fuente histórica pública de piloto: https://docs.google.com/document/d/1BMk0qKFpSzwey6NafRE07cmMLkBa-06Eh8mWj6OQMOU/edit

### NEUMA Web — Operación productiva
- Estado: `Activo`.
- Repositorio: https://github.com/gonzaloaromerob/Neuma-Web
- Objetivo: operar NEUMA Web con CI/CD reproducible, despliegue gobernado, rollback verificable, continuidad y mínima intervención manual en PROD.
- Arquitectura vigente: GitHub `main` → GitHub Actions → Environment `production` → SSH dedicado → releases inmutables → symlink `current` → smoke tests → rollback.
- SharePoint conserva documentación interna, históricos y evidencia.

## 2. Riesgos vigentes

### RISK-001 — Divergencia y sobrescritura entre múltiples SoR
- Estado: `Cerrado` para el escenario que lo originó.
- Impacto residual: `Bajo` como riesgo genérico de cualquier arquitectura multi-SoR.
- Contexto histórico: nació de la posibilidad de sincronización bidireccional Notion ↔ GitHub.
- Cierre: Notion fue retirado; no existen proyecciones bidireccionales ni dependencia operacional allí. La topología vigente es GitHub + SharePoint + SoR original aplicable.
- Control permanente: un SoR único por objeto, idempotencia, detección de conflicto y Gate ante flujos inversos materiales.

### RISK-002 — Efectos secundarios de escrituras GitHub
- Estado: `Mitigado`.
- Impacto: `Bajo`.
- Contexto histórico: una escritura GitHub disparó preview de Vercel durante el piloto.
- Control vigente: GitHub es el canal gobernado; efectos productivos pasan por workflows explícitos, Environment `production`, confirmaciones, releases inmutables, smoke tests y rollback probado. Vercel ya no forma parte de la arquitectura vigente.

## 3. Tareas abiertas

### TASK-001 — Validar activación contextual de NEUMA Operations
- Estado: `Pendiente`.
- Prioridad: `Alta`.
- Resultado esperado: ejecutar una matriz de prompts materialmente pertinentes y no pertinentes en una cuenta limpia; medir trigger recall, falsos negativos y falsos positivos. Ajustar triggers sólo si la evidencia muestra fricción material.

### TASK-002 — Evaluar protecciones y reviewers de Environment production
- Estado: `Pendiente`.
- Prioridad: `Media`.
- Resultado esperado: determinar si reglas adicionales aumentan control sin degradar ni romper el flujo CI/CD ya validado.

### TASK-003 — Observar migración de Node.js 20 en actions @v4
- Estado: `Pendiente`.
- Prioridad: `Baja`.
- Resultado esperado: revisar y migrar únicamente cuando GitHub/actions publique una ruta relevante o la deprecación empiece a afectar workflows. No hacer trabajo preventivo sin impacto material.

### TASK-004 — Limpiar residuo temporal `/var/www/neuma/dr-export`
- Estado: `Pendiente`.
- Prioridad: `Baja`.
- Resultado esperado: eliminar la copia temporal en una intervención administrativa controlada y verificar que CI/CD, releases y DR externo permanezcan íntegros.
- No bloquea CI/CD ni DR.

## 4. Tareas cerradas relevantes para trazabilidad

- Definir política de efectos secundarios para escrituras GitHub — `Hecha`.
- Diseñar política de sincronización controlada Notion–GitHub — `Hecha`; superada por ADR-010.
- Migrar conocimiento operacional necesario desde Notion a GitHub — `Hecha`.
- Ejecutar higiene POST del árbol activo de GitHub — `Hecha`.
- Retirar completamente NEUMA de Notion — `Hecha`; el usuario completó manualmente el residuo que el conector no podía purgar.

## 5. Decision Gates preservados

### Gate-002 — Validación humana de política Notion ↔ GitHub
- Nivel: `C`.
- Estado histórico: `Aprobado`.
- Decisión: no habilitar sincronización bidireccional automática; preferir flujo gobernado por System of Record y eventos explícitos.
- Vigencia: histórico. ADR-010 retiró posteriormente Notion de la topología NEUMA.

## 6. Evidencias referenciadas

Las siguientes referencias se preservan sin copiar sus originales:

- Fuente piloto — Arquitectura federada NEUMA: https://docs.google.com/document/d/1BMk0qKFpSzwey6NafRE07cmMLkBa-06Eh8mWj6OQMOU/edit
- Evidencia ficticia/no sensible de sincronización bidireccional propuesta: https://docs.google.com/document/d/1VKxZs1FfZvpOa5nTD8OsqcLErfIIdSIvs5B8Z3_LdSI/edit
- NEUMA — Estrategia 2026: evidencia `Interna`; original en Google Drive. **No copiar a GitHub**.
- NEUMA Web — recuperación de 23 assets históricos: evidencia verificada; el original/histórico permanece en SharePoint y el resultado productivo vive en https://www.neuma.com.co

## 7. Topología vigente de Systems of Record

- **GitHub / Neuma-Core:** decisiones, arquitectura, estado operacional versionable, riesgos/tareas/Gates aptos para publicación y evolución de NEUMA Operations.
- **GitHub / Neuma-Web:** código, CI/CD y operación técnica del sitio.
- **SharePoint:** corpus interno rector, estándares, plantillas, Office, entregables, históricos y proyección humana operacional.
- **Otros SoR originales:** evidencias/documentos fuente permanecen donde nacieron cuando trasladarlos no sea necesario.
- **Notion:** retirado de NEUMA; no es SoR, proyección, dependencia ni destino operativo.

## 8. Regla de continuidad

Una conversación no es SoR. Para reconstruir NEUMA después de pérdida de contexto: resolver ADR vigentes, este `operations/STATE.md`, la skill NEUMA Operations vigente y la proyección humana SharePoint; luego resolver únicamente los SoR originales que sean necesarios para la evidencia del caso. La reconstrucción no depende de Notion.

## 9. Prueba de reconstrucción post-Notion

Criterio: desde una conversación nueva y sin Notion debe poder resolverse la release vigente, decisiones, topología, estado operacional, riesgos/tareas/Gates, skill gobernante, corpus interno y fuentes originales aplicables.

Resultado de cierre: **PASS**. La información material necesaria está distribuida entre GitHub, SharePoint, NEUMA Operations y los SoR originales aplicables, sin dependencia de Notion.