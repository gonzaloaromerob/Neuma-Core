# Revisión operacional — 2026-08-18

## Alcance
Revisión del primer ciclo real de NEUMA Operations aplicado a la consolidación de Neuma-Core, Notion y Google Drive.

## Funcionó bien
- Separación explícita de System of Record por tipo de objeto.
- Uso de ramas y pull requests para cambios materiales en GitHub.
- Verificación posterior de escrituras y merges.
- Preservación de evidencia en Drive sin copiar automáticamente material interno al repositorio público.
- Registro de evidencias, riesgos, decisiones y tareas en Notion.
- Idempotencia y compensación demostradas previamente para la proyección GitHub a Notion.
- Human Decision Gates para acciones de impacto material.

## Fricciones observadas
- Algunas operaciones administrativas no están expuestas por los conectores, por ejemplo eliminación de ramas o ciertos cambios de cuenta.
- Los proveedores pueden bloquear escrituras por políticas de seguridad o límites de plan; esos bloqueos deben tratarse como evidencia y no sortearse ciegamente.
- Las operaciones de contenido de GitHub requieren distinguir create de update mediante SHA; una escritura aparentemente simple puede fallar si el path ya existe.
- Las integraciones externas pueden producir efectos de segundo orden, como deployments automáticos, aunque el cambio Git sea reversible.

## Controles que se mantienen
- No publicar material interno solo porque sea técnicamente accesible.
- No considerar una autorización general como renuncia permanente a Decision Gates materiales.
- Verificar destino, rama, sensibilidad y efectos secundarios antes de escribir.
- Preferir no-op frente a escrituras redundantes.
- Preservar originales y registrar compensación cuando una proyección diverja.

## Automatización candidata
Pueden automatizarse progresivamente las lecturas, clasificación preliminar, resolución de objetos, creación de borradores, proyecciones idempotentes y verificaciones de bajo riesgo.

Deben mantenerse bajo control reforzado los merges materiales, publicación pública de nuevo contenido, eliminación significativa, cambios productivos, movimientos de información sensible y modificaciones de autoridad entre sistemas.

## Próxima hipótesis de trabajo
La madurez de NEUMA Operations debe medirse por calidad de decisiones, trazabilidad, reducción de errores y capacidad de recuperación, no por cantidad de endpoints o automatizaciones disponibles.
