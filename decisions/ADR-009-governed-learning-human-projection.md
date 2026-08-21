# ADR-009 — Aprendizaje gobernado y proyección humana operacional

## Estado
Aprobada / vigente. Integrada en `main` mediante PR #31, squash merge `57b7320bed66a98189a2e0e28971a47312915ba2` el 21 de agosto de 2026. ADR-010 simplifica posteriormente la topología operacional sin alterar el contrato de aprendizaje ni de proyección humana.

## Contexto
El uso real de NEUMA evidenció una falla sistémica: una corrección podía quedar incorporada en conversación, skill o plataforma técnica mientras la superficie documental que el humano usa para seguir el proyecto permanecía desactualizada. También se observaron entregables que declaraban haber resuelto plantillas/estándares sin demostrar uso técnico real y proyecciones cuyo estado divergía del canónico.

## Decisión
1. **Aprendizaje = persistencia gobernada, no memoria conversacional.** Una corrección material, fallo repetible, práctica validada o regla reusable sigue: observar → clasificar → abstraer → persistir → promover → probar → reconciliar → usar.
2. **No afirmar aprendizaje sin prueba.** Una regla escrita pero no probada sobre caso original o test representativo no se considera aprendida operacionalmente.
3. **Proyección humana operacional.** Cuando el entorno declare una vista humana documental, forma parte de la postcondición de cambios materiales.
4. **SoR técnico ≠ vista humana.** Un repositorio técnico o skill no sustituye la proyección humana requerida; el humano debe poder reconstruir estado, decisiones, riesgos/Gates, fuentes y cambios materiales desde ella.
5. **Mínima duplicación.** La proyección humana mantiene sólo el conjunto compacto necesario y no replica código, ADR completos ni datos sensibles sin necesidad.
6. **QA cruzado obligatorio.** Antes de cerrar un cambio material, comparar estado canónico, derivados gobernados y proyección humana. Contradicción material o vista humana obsoleta = `conflict/fail`.
7. **Artefactos con plantilla/linaje verificables.** Plantilla canónica debe usarse materialmente; PPTX de misma serie hereda padre visual y usa estándar ejecutivo como guardrail. Renderizar/comparar forma parte de QA.
8. **Error repetido = defecto sistémico.** Una segunda corrección sobre el mismo tipo de fallo obliga a revisar contrato, precondición, test o SoR; no basta rehacer el entregable.
9. **Privacidad.** Aprendizajes derivados de clientes se abstraen antes de promoverse; no se proyectan expedientes, precios, secretos ni contenido sensible salvo necesidad/autoridad.
10. **Frontera runtime.** Actualizar fuente/paquete de una skill no equivale a instalarla/activarla en todos los runtimes.

## Implementación vigente
- NEUMA Operations v3.12 conserva y extiende este contrato.
- SharePoint `- NEUMA -` es la proyección humana operacional principal de esta instalación.
- GitHub `Neuma-Core` conserva decisiones, arquitectura y estado operacional versionable.
- Notion queda como fuente legado temporal conforme a ADR-010 y no participa en la postcondición de trabajo nuevo.
- La regresión clave sigue siendo: estado técnico correcto + vista humana obsoleta = **FAIL**.

## Compatibilidad
Backward-compatible con ADR-001/003/005/006/008/010 y NEUMA Core 4.0. No convierte GitHub, SharePoint u Office en dependencias universales de la skill; son configuración de esta instalación.

## Consecuencia práctica
NEUMA no considera exitoso un cambio que sólo esté correcto “por detrás”: la operación debe quedar técnicamente consistente, humanamente seguible y reconstruible desde la topología vigente.