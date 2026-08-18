# Gobierno de cambios

## Flujo recomendado
1. Identificar el System of Record y la sensibilidad del contenido.
2. Trabajar en rama separada para cambios no triviales.
3. Mantener el cambio mínimo necesario y evitar mezclar objetivos no relacionados.
4. Revisar diff, referencias y efectos secundarios.
5. Abrir pull request con contexto, alcance, riesgos y verificaciones.
6. Usar Decision Gate C antes del merge cuando el cambio sea material.
7. Verificar `main` después del merge y actualizar proyecciones operativas cuando corresponda.

## Calidad
Todo artefacto canónico debe indicar con suficiente claridad su propósito, estado, alcance y relación con otras fuentes. Las afirmaciones dependientes de capacidades actuales de herramientas deben revisarse cuando cambien versiones o conectores.

## Separación
No convertir conversaciones, notas internas o documentos fuente en contenido público por defecto. La canonización es una decisión editorial y de gobierno, no una consecuencia automática de que el contenido sea accesible a la IA.
