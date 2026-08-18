# Lección aprendida 001 — efectos secundarios invisibles

## Observación
Durante las primeras pruebas GitHub, una escritura en una rama/PR activó una preview externa de Vercel aunque la intención primaria era validar el conector GitHub.

## Aprendizaje
La reversibilidad del cambio primario no determina por sí sola el riesgo total. Una acción reversible puede disparar efectos externos persistentes o visibles.

## Regla derivada
Antes de una escritura, identificar cuando sea razonable CI/CD, deployments, webhooks, bots, notificaciones u otras integraciones. Después de escribir, verificar efectos secundarios materiales observables.

## Generalización
El control debe considerar el sistema de consecuencias, no solo el sistema directamente modificado.
