# ADR-005 — Gobierno de evolución de NEUMA Operations

## Estado
Validada por decisión humana el 2026-08-20; publicación en `main` sujeta al flujo normal de revisión del repositorio.

## Contexto
La evolución de NEUMA Operations requiere controles explícitos para evitar que una mejora local introduzca regresiones sistémicas, contaminación entre contextos, resolución heurística de conflictos de autoridad o crecimiento normativo sin fundamento material.

## Decisión
Adoptar los siguientes controles portables para NEUMA Operations:

1. **Seguridad de regresión:** todo cambio material de la skill, del NEUMA Core transportado o de una referencia normativa identifica los invariantes y flujos afectados y aplica el conjunto mínimo de pruebas representativas suficiente para verificar que el comportamiento previsto mejora sin degradar reglas no relacionadas.
2. **Aislamiento contextual:** personas, organizaciones, clientes, asuntos y proyectos permanecen aislados por defecto. No se trasladan datos, decisiones, artefactos o conclusiones específicas entre contextos sin necesidad material, autoridad válida y autorización apropiada. El aprendizaje reusable se abstrae o anonimiza preservando confidencialidad, procedencia y límites de uso.
3. **Conflicto de autoridad:** cuando dos fuentes aparentemente autorizadas discrepan materialmente y la precedencia no puede establecerse con evidencia suficiente, el estado es `conflict`: no se elige, fusiona, sobrescribe ni propaga heurísticamente; primero se resuelve la autoridad o se escala a decisión humana cuando sea material.
4. **Gate de evolución:** una regla central solo se modifica con fundamento material, por ejemplo fallo/riesgo observado, fricción recurrente, cambio relevante de plataforma, evidencia empírica o comparativa, simplificación neta o nueva necesidad portable. No se refina por completitud, estética, novedad o anticipación especulativa.
5. **Trazabilidad mínima:** los cambios materiales conservan únicamente la evidencia durable necesaria para reconstruir qué cambió, por qué, qué comportamiento podía afectar, cómo se verificó y qué proyecciones gobernadas fueron reconciliadas. Se reutilizan ADR, PR, registro de decisión u otro mecanismo autoritativo existente en lugar de crear bitácoras duplicadas.

## Verificación y postcondición
- La skill actualizada pasó el validador de Skills sin errores.
- Se revisaron de forma proporcional los invariantes afectados: secuencia verdad → claridad → decisión → acción; verificación transversal; A/B/C; mínimo privilegio; idempotencia; idioma; Human Context; aislamiento; SoR/proyecciones; conflictos; secretos; QA de artefactos; cierre conversacional y Mensaje NEUMA.
- El Manual de Gobierno interno fue actualizado a v1.8 en su System of Record documental y verificado mediante renderizado DOCX y relectura posterior a la escritura.
- Las Instrucciones Rectoras del Proyecto ya contenían separación/confidencialidad y evolución basada en evidencia; por tanto, su reconciliación fue `no-op` para evitar duplicación.

## Arquitectura documental
El Manual de Gobierno y los originales rectores internos permanecen en su System of Record documental. GitHub conserva únicamente decisiones y artefactos deliberadamente versionables/publicables. Notion mantiene la proyección operativa de decisiones, riesgos, tareas, Gates y estado.

## Consecuencia
Un cambio material de NEUMA Operations no se considera cerrado hasta verificar su propia postcondición y reconciliar únicamente las proyecciones gobernadas que deban permanecer consistentes, respetando autorización A/B/C y evitando sincronización global o bidireccional automática.
