# ADR-005 — Gobierno de evolución de NEUMA Operations

## Estado
Validada por decisión humana el 2026-08-20; estabilización de NEUMA Operations v3.5 verificada y publicación en `main` autorizada dentro del flujo normal del repositorio.

## Contexto
La evolución de NEUMA Operations requiere controles explícitos para evitar que una mejora local introduzca regresiones sistémicas, contaminación entre contextos, resolución heurística de conflictos de autoridad o crecimiento normativo sin fundamento material.

## Decisión
Adoptar los siguientes controles portables para NEUMA Operations:

1. **Seguridad de regresión:** todo cambio material de la skill, del NEUMA Core transportado o de una referencia normativa identifica los invariantes y flujos afectados y aplica el conjunto mínimo de pruebas representativas suficiente para verificar que el comportamiento previsto mejora sin degradar reglas no relacionadas.
2. **Aislamiento contextual:** personas, organizaciones, clientes, asuntos y proyectos permanecen aislados por defecto. No se trasladan datos, decisiones, artefactos o conclusiones específicas entre contextos sin necesidad material, autoridad válida y autorización apropiada. El aprendizaje reusable se abstrae o anonimiza preservando confidencialidad, procedencia y límites de uso.
3. **Conflicto de autoridad:** cuando dos fuentes aparentemente autorizadas discrepan materialmente y la precedencia no puede establecerse con evidencia suficiente, el estado es `conflict`: no se elige, fusiona, sobrescribe ni propaga heurísticamente; primero se resuelve la autoridad o se escala a decisión humana cuando sea material.
4. **Gate de evolución:** una regla central solo se modifica con fundamento material, por ejemplo fallo/riesgo observado, fricción recurrente, cambio relevante de plataforma, evidencia empírica o comparativa, simplificación neta o nueva necesidad portable. No se refina por completitud, estética, novedad o anticipación especulativa.
5. **Trazabilidad mínima:** los cambios materiales conservan únicamente la evidencia durable necesaria para reconstruir qué cambió, por qué, qué comportamiento podía afectar, cómo se verificó y qué proyecciones gobernadas fueron reconciliadas. Se reutilizan ADR, PR, registro de decisión u otro mecanismo autoritativo existente en lugar de crear bitácoras duplicadas.

## Estabilización v3.5
La revisión de coherencia de v3.5 identificó y corrigió dos residuos sin introducir un cambio incompatible:

- **Portabilidad:** `platform-portability.md` se alineó con la separación vigente entre NEUMA Core y NEUMA Operations. Control/autorización, mínimo privilegio, idempotencia, efectos secundarios, SoR/proyecciones y postcondiciones operacionales permanecen en Operations; el Core conserva los invariantes cognitivos y de colaboración. La referencia dejó además de declarar el alcance histórico v3.2 y quedó alineada con v3.5.
- **Rector del proyecto:** las Instrucciones Rectoras se actualizaron a v2.2 para retirar la regla conversacional redundante de generación de continuidad. El rector conserva únicamente contexto, alcance y reglas específicas del proyecto; la salud y transferencia conversacional continúan gobernadas por NEUMA Operations.

Estas correcciones son backward-compatible dentro de la familia v3 y no justifican v3.6 ni una declaración de arquitectura NEUMA 4.0.

## Verificación y postcondición
- La skill v3.5 corregida pasó el validador de Skills sin errores y fue empaquetada como bundle completo.
- Se revisaron de forma proporcional los invariantes afectados: secuencia verdad → claridad → decisión → acción; verificación transversal; límites Core/Operations; A/B/C; mínimo privilegio; idempotencia; Human Context; aislamiento; SoR/proyecciones; conflictos; secretos; QA de artefactos; portabilidad; cierre conversacional y Mensaje NEUMA.
- El Manual de Gobierno interno permanece en v1.8 en su System of Record documental, conforme a la evolución previamente validada.
- Las Instrucciones Rectoras del Proyecto quedaron en v2.2 en su System of Record documental; el DOCX fue renderizado, inspeccionado visualmente y re-leído después de la escritura para verificar la postcondición.
- GitHub conserva únicamente decisiones y artefactos deliberadamente versionables/publicables; no se replica el bundle interno de la skill como corpus paralelo.
- Notion debe reflejar el estado final de esta decisión y de la proyección GitHub mediante reconciliación idempotente posterior al merge.

## Arquitectura documental
El Manual de Gobierno y los originales rectores internos permanecen en su System of Record documental. GitHub conserva únicamente decisiones y artefactos deliberadamente versionables/publicables. Notion mantiene la proyección operativa de decisiones, riesgos, tareas, Gates y estado.

## Consecuencia
Un cambio material de NEUMA Operations no se considera cerrado hasta verificar su propia postcondición y reconciliar únicamente las proyecciones gobernadas que deban permanecer consistentes, respetando autorización A/B/C y evitando sincronización global o bidireccional automática.
