# NEUMA Web — Arquitectura operativa

Estado: baseline aprobada 2026-08-18

## Objetivo

Gobernar la evolución de `https://www.neuma.com.co` con cambios reproducibles, auditables, verificables y reversibles, reduciendo al mínimo la intervención manual sobre producción.

## System of Record

| Capa | Autoridad |
|---|---|
| Entrega histórica y documentación interna | SharePoint `R & G/- Proyectos ChatGPT -/- NEUMA -/Sitio WEB/Entrega final` |
| Código fuente web y CI/CD | repositorio GitHub dedicado `Neuma-Web` bajo control de Gonzalo (pendiente de creación/importación) |
| Backlog, releases, riesgos y Gates | Notion |
| Runtime de producción | VPS IONOS / Ubuntu / Nginx |
| Metodología/publicable y decisiones arquitectónicas | `Neuma-Core` |

La VPS no es fuente de verdad. No se editará código directamente en PROD salvo emergencia; cualquier hotfix deberá reconciliarse posteriormente hacia GitHub.

## Baseline heredada

La entrega recibida contiene un proyecto Angular 18+ con Standalone Components, SCSS, EmailJS, `src/`, `public/`, `package.json`, `package-lock.json`, `angular.json`, build histórico en `dist/neuma-web/browser/` y despliegue manual hacia Nginx en una VPS Ubuntu.

El `.git/config` recibido referencia `https://github.com/SanM2702/Neuma.git`, rama `master`. Ese origen pertenece al legado del desarrollador y no se adopta como SoR futuro.

## Flujo objetivo

`solicitud -> fuente canónica -> rama -> cambio -> npm ci -> build/tests -> QA -> PR -> autorización PROD -> merge/deploy -> smoke test -> trazabilidad`

Los cambios de contenido, assets, estilos y funcionalidad deben producirse en código fuente. `dist/`, `node_modules/`, `.angular/` y el `.git/` heredado no forman parte del baseline importado.

## CI/CD objetivo

GitHub Actions construirá el sitio y desplegará por SSH/rsync mediante un usuario dedicado de mínimo privilegio.

Estructura objetivo en la VPS:

```text
/var/www/neuma/
├── releases/
│   └── <commit-sha>/
└── current -> releases/<commit-sha>/
```

Nginx debe servir `current`. El cambio del symlink debe ser atómico. Se conservarán releases anteriores para rollback. Un cambio normal de archivos estáticos no requiere recargar Nginx; el reload se reserva para cambios de configuración.

## Seguridad

- usuario de despliegue dedicado, sin root;
- clave SSH dedicada y rotatable;
- secretos únicamente en GitHub Environment `production`;
- ningún secreto en repositorio, Notion o SharePoint;
- protección del entorno productivo y aprobación humana para despliegues;
- cambios de Nginx, DNS, TLS, firewall, secretos y permisos tratados como operaciones C;
- rollback disponible antes de cambios de infraestructura.

## Verificación

Antes de PROD: build reproducible, diff, rutas/assets, enlaces, responsive y consola cuando las herramientas estén disponibles.

Después de PROD: HTTPS, página principal y rutas críticas, assets, ausencia de errores visibles, commit desplegado y rollback identificado.

## Estado de implementación

Aprobado el diseño. Pendiente crear el repositorio dedicado `gonzaloaromerob/Neuma-Web`, importar el baseline limpio, habilitar GitHub Actions/Environment `production`, provisionar SSH de despliegue en IONOS y ejecutar el primer despliegue controlado end-to-end.