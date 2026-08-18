# Contrato de proyección entre sistemas

## Precondiciones
- System of Record inequívoco.
- Destino autorizado.
- Sensibilidad compatible con el destino.
- Clave determinista estable.

## Resolución
La proyección debe resolver una de cuatro acciones:
- `create`: no existe derivado y debe crearse;
- `update`: existe y el canónico cambió;
- `no-op`: existe y ya converge con el canónico;
- `conflict`: la autoridad o el estado no permiten una actualización segura.

## Idempotencia
Repetir la misma operación sin cambios en el canónico debe converger al mismo objeto y evitar duplicados o escrituras materiales innecesarias.

## Divergencia
Cuando el derivado contradiga al canónico y la autoridad sea clara, compensar el derivado desde el System of Record. No modificar el canónico para acomodar una copia.

## Verificación
Después de una escritura, releer o consultar el destino cuando aporte evidencia material de la postcondición.

## Límite
Este contrato no autoriza sincronización bidireccional automática. Los flujos inversos requieren intención y gobierno explícitos.
