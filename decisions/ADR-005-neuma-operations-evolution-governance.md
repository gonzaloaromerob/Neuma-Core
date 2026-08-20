# ADR-005 — Gobierno de evolución de NEUMA Operations

## Estado
Validada por decisión humana el 2026-08-20. NEUMA Operations v3.6 incorpora mantenimiento gobernado proactivo como refinamiento backward-compatible de la familia v3.

## Contexto
La evolución de NEUMA Operations requiere controles explícitos para evitar que una mejora local introduzca regresiones sistémicas, contaminación entre contextos, resolución heurística de conflictos de autoridad, crecimiento normativo sin fundamento material o dependencia del usuario como recordatorio operativo para mantener consistentes los sistemas gobernados.

## Decisión
Adoptar los siguientes controles portables para NEUMA Operations:

1. **Seguridad de regresión:** todo cambio material de la skill, del NEUMA Core transportado o de una referencia normativa identifica los invariantes y flujos afectados y aplica el conjunto mínimo de pruebas representativas suficiente para verificar que el comportamiento previsto mejora sin degradar reglas no relacionadas.
2. **Aislamiento contextual:** personas, organizaciones, clientes, asuntos y proyectos permanecen aislados por defecto. No se trasladan datos, decisiones, artefactos o conclusiones específicas entre contextos sin necesidad material, autoridad válida y autorización apropiada. El aprendizaje reusable se abstrae o anonimiza preservando confidencialidad, procedencia y límites de uso.
3. **Conflicto de autoridad:** cuando dos fuentes aparentemente autorizadas discrepan materialmente y la precedencia no puede establecerse con evidencia suficiente, el estado es `conflict`: no se elige, fusiona, sobrescribe ni propaga heurísticamente; primero se resuelve la autoridad o se escala a decisión humana cuando sea material.
4. **Gate de evolución:** una regla central solo se modifica con fundamento material, por ejemplo fallo/riesgo observado, fricción recurrente, cambio relevante de plataforma, evidencia empírica o comparativa, simplificación neta o nueva necesidad portable. No se refina por completitud, estética, novedad o anticipación especulativa.
5. **Trazabilidad mínima:** los cambios materiales conservan únicamente la evidencia durable necesaria para reconstruir qué cambió, por qué, qué comportamiento podía afectar, cómo se verificó y qué proyecciones gobernadas fueron reconciliadas. Se reutilizan ADR, PR, registro de decisión u otro mecanismo autoritativo existente en lugar de crear bitácoras duplicadas.
6. **Responsabilidad proactiva de reconciliación:** después de un cambio material, NEUMA identifica autónomamente los SoR, proyecciones y derivados gobernados potencialmente afectados y decide cuáles requieren `create`, `update`, `no-op`, `conflict` o limpieza acotada. No espera a que el usuario recuerde solicitar actualizaciones en GitHub, Notion u otros sistemas gobernados.
7. **Higiene gobernada proporcional:** cuando un objeto sea verificablemente obsoleto, duplicado, reemplazado, huérfano o ya no aporte valor operativo, aplicar la corrección mínima segura y reversible que preserve historia y trazabilidad. Cerrar, marcar, actualizar o archivar es preferible a borrar. Una eliminación, sobrescritura material u otra acción C destructiva conserva su Gate concreto.
8. **Atención humana mínima:** completar todo el trabajo A/B autorizado y reversible antes de escalar. La intervención humana se reserva para autoridad, criterio, aceptación de riesgo, pérdida material o acciones C no ya autorizadas de manera concreta.

## Evolución v3.5 → v3.6
v3.5 estabilizó la frontera Core/Operations y la superficie decisional mínima. v3.6 corrige una fricción operativa observada: el usuario no debe actuar como memoria externa del sistema para recordar reconciliaciones o higiene entre plataformas. La responsabilidad se desplaza al operador NEUMA dentro de los límites de autorización existentes.

La evolución es backward-compatible: mantiene la autoridad de los SoR, la dirección controlada de proyecciones, mínimo privilegio, idempotencia y gates C; no introduce sincronización global, bidireccional automática ni permiso general de borrado.

## Verificación y postcondición
- La skill NEUMA Operations v3.6 fue actualizada en `SKILL.md`, `projection-contract.md`, `delegated-autonomy.md`, `conformance.md` y `versioning.md`.
- El bundle completo pasó el validador oficial de Skills sin errores y fue empaquetado como `skill.zip`.
- Se verificó que el contrato conserva verdad → claridad → decisión → acción, verificación transversal, A/B/C, mínimo privilegio, idempotencia, aislamiento contextual, conflicto de autoridad, superficie decisional mínima y postcondición.
- GitHub y Notion se revisan proporcionalmente durante esta misma evolución para identificar residuos reales; no se ejecuta housekeeping global por defecto.

## Arquitectura documental
El Manual de Gobierno y los originales rectores internos permanecen en su System of Record documental. GitHub conserva únicamente decisiones y artefactos deliberadamente versionables/publicables. Notion mantiene la proyección operativa de decisiones, riesgos, tareas, Gates y estado.

## Consecuencia
Un cambio material de NEUMA Operations no se considera cerrado hasta verificar su propia postcondición, reconciliar los derivados que deban permanecer consistentes y evaluar proporcionalmente si existe higiene gobernada pendiente. La ausencia de una solicitud explícita del usuario para “actualizar GitHub/Notion” no exime esta obligación.