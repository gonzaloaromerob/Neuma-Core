# NEUMA Operations v3.12 — Change Note

Fecha: 2026-08-21

## Propósito
Incorporar como capacidad reusable la simplificación de topología operacional demostrada en NEUMA: consolidar una plataforma intermedia cuando otros SoR pueden cubrir sus funciones con menos carga humana y sin pérdida material.

## Cambios
- Nueva regla **Topología mínima de plataformas** en `SKILL.md`.
- Nueva referencia `platform-consolidation.md` con secuencia obligatoria: clasificar conocimiento → migrar sólo lo necesario → cortar nuevas dependencias → verificar reconstrucción → higiene POST → limpieza de legado en iteración separada.
- Nueva regresión de conformidad para evitar bulk-copy de plataformas, PRE-limpiezas innecesarias y residuos activos mantenidos sólo como archivo cuando Git ya conserva historia.
- Mantiene aprendizaje gobernado, proyección humana, QA cruzado, no-memory execution y gobierno A/B/C de v3.11.

## Aplicación en esta instalación
- GitHub `Neuma-Core` pasa a SoR operacional versionable.
- SharePoint permanece SoR documental interno y proyección humana.
- Notion queda como fuente legado temporal; no recibe nuevas proyecciones ni escrituras operativas.
- `operations/STATE.md` concentra el estado mínimo necesario para reconstrucción.

## Compatibilidad
Backward-compatible con NEUMA Core 4.0. La consolidación de plataformas es configuración del entorno; no convierte GitHub o SharePoint en dependencias universales de la skill.

## Limitación runtime
Fuente/paquete v3.12 validado y publicado no equivale a instalación/activación automática en todos los runtimes de ChatGPT.