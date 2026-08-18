# Lección aprendida 003 — idempotencia antes que sincronización

## Observación
El piloto GitHub → Notion mostró que una clave determinista permite resolver el mismo objeto, evitar duplicados y compensar una divergencia sin reescribir el canónico.

## Aprendizaje
Antes de aumentar frecuencia o bidireccionalidad, una integración debe demostrar convergencia segura al repetir la misma operación.

## Regla derivada
Toda proyección reusable debe definir clave estable y comportamiento `create`, `update`, `no-op` y `conflict` antes de considerarse candidata a automatización recurrente.

## Generalización
La idempotencia reduce riesgo operacional y simplifica recuperación; es una propiedad más importante que la velocidad de sincronización.
