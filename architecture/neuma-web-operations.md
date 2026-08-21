# NEUMA Web — Arquitectura operativa

Estado: vigente, reconciliada 2026-08-21

## Objetivo
Gobernar la evolución de `https://www.neuma.com.co` con cambios reproducibles, auditables, verificables y reversibles, reduciendo al mínimo la intervención manual sobre producción.

## System of Record

| Capa | Autoridad |
|---|---|
| Entrega histórica y documentación interna | SharePoint `R & G/- Proyectos ChatGPT -/- NEUMA -/Sitio WEB/Entrega final` |
| Código fuente web y CI/CD | `gonzaloaromerob/Neuma-Web` |
| Estado operacional, riesgos, tareas y Gates versionables | `gonzaloaromerob/Neuma-Core` → `operations/STATE.md` y ADR vigentes |
| Runtime de producción | VPS IONOS / Ubuntu / Nginx |
| Metodología/publicable y decisiones arquitectónicas | `Neuma-Core` |

Notion dejó de ser SoR operativo para trabajo nuevo conforme a ADR-010. Se conserva temporalmente como fuente legado hasta su limpieza posterior.

La VPS no es fuente de verdad. No editar código directamente en PROD salvo emergencia; cualquier hotfix debe reconciliarse posteriormente hacia GitHub.

## Baseline vigente
El sitio productivo está gobernado por `gonzaloaromerob/Neuma-Web`, con Angular y CI/CD reproducible. La entrega histórica y los respaldos permanecen en SharePoint.

## Flujo vigente
`solicitud -> fuente canónica -> rama -> cambio -> npm ci -> build/tests -> QA -> PR -> autorización PROD -> merge/deploy -> smoke test -> trazabilidad`

Los cambios de contenido, assets, estilos y funcionalidad se producen en código fuente. `dist/`, `node_modules/`, `.angular/` y repositorios heredados no son SoR.

## CI/CD vigente
GitHub Actions construye el sitio y despliega mediante un usuario SSH dedicado de mínimo privilegio.

Estructura productiva:

```text
/var/www/neuma/
├── releases/
│   └── <commit-sha>/
└── current -> releases/<commit-sha>/
```

Nginx sirve `current`. El cambio de symlink es atómico. Se conservan releases anteriores para rollback. Un cambio normal de archivos estáticos no requiere recargar Nginx; el reload se reserva para configuración.

## Seguridad
- usuario de despliegue dedicado, sin root;
- clave SSH dedicada y rotatable;
- secretos únicamente en GitHub Environment `production`;
- ningún secreto en repositorio o documentación;
- protección del entorno productivo y aprobación humana para despliegues materiales;
- cambios de Nginx, DNS, TLS, firewall, secretos y permisos tratados como operaciones C;
- rollback disponible antes de cambios de infraestructura.

## Verificación
Antes de PROD: build reproducible, diff, rutas/assets, enlaces, responsive y consola cuando las herramientas estén disponibles.

Después de PROD: HTTPS, página principal y rutas críticas, assets, ausencia de errores visibles, commit desplegado y rollback identificado.

## Estado de implementación
El flujo productivo fue implementado y validado. La operación posterior se gobierna desde GitHub; tareas y riesgos relevantes se mantienen en `operations/STATE.md` o en Issues/Projects sólo cuando aporten valor operacional material.