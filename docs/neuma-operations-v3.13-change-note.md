# NEUMA Operations v3.13 — Change Note

Fecha: 2026-08-21

## Propósito
Reducir desgaste humano evitable en conversaciones largas y multi-fase, haciendo que NEUMA detecte antes presión de contexto, repetición, recapitulaciones extensas y ciclos manuales de prueba/relay, y recomiende transferencia proactiva antes de que el usuario tenga que pedirla.

## Hallazgo que origina el cambio
Una conversación NEUMA acumuló múltiples fases, pruebas y reconciliaciones. Aunque existía una referencia de salud conversacional, el sistema no escaló a handoff con suficiente anticipación y siguió produciendo respuestas largas y rondas manuales adicionales. El usuario tuvo que señalar explícitamente que la conversación era demasiado larga y desgastante.

## Cambios en v3.13
- Refuerza `conversation-health.md` para tratar el esfuerzo humano como señal material de salud.
- Añade señales explícitas: crecimiento de respuestas por recapitulación, repetición de contexto cerrado, relay manual entre conversaciones, ciclos de aceptación redundantes y reporte de agotamiento.
- En estado `Watch`, obliga a comprimir respuesta/contexto y colapsar pruebas al conjunto representativo mínimo.
- El reporte explícito de desgaste humano pasa a ser señal fuerte de `Handoff recommended` una vez estabilizada la operación atómica en curso.
- Añade guardrail de esfuerzo humano: antes de otra ronda de validación, preferir una prueba representativa, persistencia/lectura directa desde SoR y transferencia cuando cueste menos al humano.
- Endurece `conversation-closure.md`: transportar estado mínimo suficiente, no historia; no repetir rondas de prueba ya absorbidas por una conclusión vigente.
- Añade regresión de conformance para conversación larga + repetición + desgaste humano.

## Regla operativa resultante
La corrección técnica de una respuesta no compensa una carga humana innecesaria. Cuando longitud, repetición, fase cerrada, relay manual o reporte de desgaste hacen que continuar sea materialmente peor, NEUMA debe reducir contexto y longitud de inmediato y recomendar handoff antes de otra recapitulación amplia.

## Compatibilidad
Backward-compatible con NEUMA 4.0. No modifica NEUMA Core ni las versiones de módulos especializados. Cambia el comportamiento operativo de continuidad y economía de esfuerzo humano.

## Runtime
La publicación del paquete v3.13 no implica instalación o activación automática en todos los runtimes.