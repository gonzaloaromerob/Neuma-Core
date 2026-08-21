# ADR-009 — Aprendizaje gobernado y proyección humana operacional

## Estado
Propuesta para aprobación mediante PR gobernado. Evolución backward-compatible de NEUMA Operations; no modifica NEUMA Core 4.0.

## Contexto
El uso real de NEUMA evidenció una falla sistémica: una corrección podía quedar incorporada en la conversación, en un paquete de skill, en GitHub o en Notion, mientras la superficie documental que el humano usa para seguir el proyecto —por ejemplo una carpeta SharePoint con DOCX/XLSX/PPTX— permanecía desactualizada. También se observaron entregables que declaraban haber resuelto plantillas/estándares sin demostrar que el archivo canónico hubiera sido usado técnicamente, y proyecciones cuyo estado no coincidía con cambios ya fusionados.

Esto produce retrabajo, prueba y error, falsa sensación de cierre y dependencia del humano como auditor manual. La solución debe ser portable: no imponer SharePoint a todos los entornos, sino gobernar cualquier proyección humana operacional que el entorno declare.

## Decisión
1. **Aprendizaje = persistencia gobernada, no memoria conversacional.** Una corrección material, fallo repetible, práctica validada o nueva regla reusable sigue el ciclo: observar → clasificar → abstraer → persistir → promover → probar → reconciliar → usar.
2. **No afirmar aprendizaje sin prueba.** Una regla escrita pero no probada sobre el caso original o un test representativo no se considera aprendida operacionalmente.
3. **Proyección humana operacional.** Cuando el entorno declare una vista humana —por ejemplo una carpeta documental con Office artifacts— esa vista es una proyección gobernada y parte de la postcondición de cambios materiales.
4. **SoR técnico ≠ vista humana.** GitHub, Notion, una skill o un repositorio técnico no sustituyen la proyección humana requerida. El humano debe poder reconstruir estado actual, decisiones, riesgos/Gates, fuentes autoritativas y cambios materiales desde esa vista sin leer diffs o internals de otras plataformas.
5. **Mínima duplicación.** La proyección humana mantiene solo el conjunto compacto necesario: un artefacto de estado/navegación y los artefactos de propósito específico ya existentes. No replica código, ADR completos ni datos sensibles salvo necesidad justificada.
6. **QA cruzado obligatorio.** Antes de cerrar un cambio material, comparar el estado canónico, las proyecciones operacionales y la proyección humana declarada. Si existe contradicción material o la vista humana está obsoleta, el cierre es `conflict/fail`, aunque las escrituras técnicas hayan sido exitosas.
7. **Artefactos con plantilla/linaje verificables.** Cuando exista una plantilla canónica, su uso debe ser una precondición verificable; cuando un PPTX pertenezca a una serie establecida, el deck anterior es fuente de linaje visual y el estándar ejecutivo actúa como control de calidad. Renderizar y comparar forma parte de la QA.
8. **Error repetido = defecto sistémico.** Una segunda corrección humana sobre el mismo tipo de fallo obliga a revisar contrato, precondición, test o SoR; no basta rehacer el entregable.
9. **Privacidad.** Aprendizajes derivados de clientes deben abstraerse antes de promoverse. No se proyectan expedientes, precios, secretos ni información sensible del caso salvo que el SoR/destino correspondiente lo requiera y esté autorizado.
10. **Frontera runtime.** Actualizar fuente/paquete de una skill no equivale a instalarla/activarla en todos los runtimes; el estado debe distinguirse explícitamente.

## Implementación inicial
- NEUMA Operations v3.11 incorpora la proyección humana operacional, el ciclo de aprendizaje y el QA cruzado.
- La instalación actual declara la carpeta documental NEUMA en SharePoint como proyección humana operacional principal.
- Notion conserva estado operativo/proyecciones; GitHub conserva decisiones publicables/versionadas; SharePoint conserva rectoría interna, estándares/plantillas y la vista humana Office.
- El test de regresión falla si GitHub/Notion están actualizados pero la proyección humana requerida queda obsoleta.

## Compatibilidad
Backward-compatible con ADR-001/002/003/005/006/008 y con NEUMA Core 4.0. No convierte Office/SharePoint en dependencia universal; la proyección humana es configuración de entorno. No autoriza sincronización global, publicación externa ni pérdida de trabajo humano independiente.

## Postcondición para aprobación
1. skill v3.11 validada y empaquetada;
2. proyección humana SharePoint reconciliada;
3. Notion actualizado con decisión y estado;
4. Mapa Maestro y Roadmap humanos actualizados;
5. prueba cruzada documentada sin contradicciones materiales abiertas;
6. PR revisado y fusionado.

## Consecuencia práctica
NEUMA deja de considerar exitoso un cambio que solo está correcto “por detrás”. La operación debe quedar técnicamente consistente y humanamente seguible.
