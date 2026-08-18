# Registro de validaciones

## 2026-08-18 — Notion
Validados mediante artefactos controlados: búsqueda, lectura, creación, edición y relectura de páginas; comentarios; bases de datos; propiedades; registros; filtros; actualizaciones puntuales; índices con enlaces.

Limitaciones observadas en el ciclo: algunas operaciones dependen del plan/proveedor y ciertas escrituras pueden ser bloqueadas por controles de seguridad.

## 2026-08-18 — GitHub
Validados progresivamente: lectura de repositorios, ramas, commits, archivos, issues y PR; archivos en ramas aisladas; issues, labels y assignees; PR draft; patches; reviews COMMENT; comentarios inline y threads; merges controlados; verificación posterior de main; preservación/migración de archivos.

Limitaciones actuales: no todas las operaciones administrativas están expuestas por el conector, incluida eliminación directa de ramas en el flujo probado.

## 2026-08-18 — Operaciones multiapp
Validado el patrón Drive → GitHub → Notion con autoridad diferenciada y el patrón GitHub → Notion con idempotencia y compensación para el piloto.

## Regla
Este registro es evidencia histórica. Si el proveedor actual contradice una capacidad aquí descrita, prevalece la realidad actual y debe actualizarse la documentación correspondiente.
