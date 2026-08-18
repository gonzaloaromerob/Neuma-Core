# Línea base de seguridad de Neuma-Core

## Contexto
Neuma-Core es un repositorio público. La publicación debe ser deliberada.

## Controles mínimos
1. No almacenar secretos, tokens, credenciales, claves privadas ni archivos de entorno con valores reales.
2. No publicar información confidencial, restringida, de clientes, legal, pericial o personal sin una decisión explícita y justificada.
3. Usar ramas y pull requests para cambios materiales.
4. Revisar el diff completo antes de merge.
5. Considerar integraciones externas y efectos automáticos antes de escribir.
6. Mantener evidencias y originales en su repositorio documental autorizado.
7. Tratar enlaces a fuentes internas como metadatos sensibles cuando revelen información que no deba ser pública.
8. Archivar material histórico sin presentarlo como vigente.

## Revisión recomendada
Cuando GitHub exponga las capacidades administrativas necesarias, revisar branch protection/rulesets, secret scanning, Dependabot cuando aplique, permisos de GitHub Apps, webhooks y ramas históricas.
