# ADR-006 — Resiliencia de estado, continuidad y recuperación

## Estado
Propuesta preparada para revisión; publicación en `main` pendiente de Gate C.

## Contexto
El trabajo humano–IA puede acumular decisiones, estado operativo, evidencia, artefactos y esfuerzo material a lo largo de conversaciones extensas. Una conversación, un prompt o el contexto local del runtime son superficies de trabajo transitorias y no deben convertirse en el único contenedor de estado relevante.

La pérdida, eliminación, truncación o indisponibilidad de una conversación o mensaje no siempre permite recuperar el transcript original. Sin embargo, NEUMA debe reducir el impacto de ese evento garantizando que el estado intelectual y operativo material pueda reconstruirse desde autoridad y evidencia sobrevivientes cuando el trabajo lo justifique.

## Decisión
Adoptar para NEUMA Operations un contrato portable de **resiliencia de estado, continuidad y recuperación** con los siguientes principios:

1. **La conversación no es System of Record.** El estado material de un trabajo debe residir o poder reconstruirse desde SoR, checkpoints y proyecciones gobernadas proporcionales al riesgo e impacto.
2. **Checkpointing proporcional.** Crear o refrescar un checkpoint mínimo cuando perder el estado actual pueda causar retrabajo material, ambigüedad, acción sobre el objeto equivocado, pérdida de una decisión relevante o interrupción riesgosa. Usar `no-op` cuando el estado durable vigente ya sea suficiente.
3. **Estado recuperable mínimo.** Un checkpoint conserva únicamente objetivo vigente, estado verificado, decisiones cerradas aún condicionantes, pendientes/Gates activos, SoR e identidades estables, riesgos/dependencias materiales, postcondición/evidencia pendiente y primera acción segura. No replica transcripts completos, razonamiento oculto, secretos ni ruido conversacional.
4. **Recuperación desde autoridad sobreviviente.** Ante pérdida de conversación, prompt, runtime o derivado, resolver primero SoR/checkpoint, releer solo evidencia canónica mínima, clasificar divergencias y reconstruir el working set sin inventar contenido eliminado que no pueda verificarse.
5. **Continuidad conversacional gobernada.** `conversation-health` determina cuándo una transferencia a conversación nueva tiene beneficio material; `conversation-closure` genera el artefacto mínimo de transferencia; el checkpoint durable evita que ese prompt sea la única copia del estado.
6. **Resiliencia de proyecciones.** Los derivados deben ser reconstruibles desde el canónico cuando sea práctico. Después de cambios materiales se aplica reconciliación proactiva e higiene gobernada.
7. **Backup y restauración verificables.** Para objetos o sistemas de alto impacto, la existencia de un backup no constituye evidencia suficiente de recuperación: debe verificarse proporcionalmente mediante integridad, readback o restauración real/controlada.
8. **BCP/DRP proporcional.** Cuando la indisponibilidad de un sistema pueda afectar materialmente a una persona u organización, resolver servicios/objetos críticos, dependencias, fuente autorizada, copias independientes, orden de recuperación, roles, verificación posterior y fallback/rollback. RPO y RTO se tratan como objetivos de negocio/operación y no se inventan: requieren definición o aceptación humana cuando sean materiales.
9. **Aplicabilidad PN/PJ.** En una persona natural, escalar controles según impacto, esfuerzo, sensibilidad y dependencia de trabajo asistido por IA. En una persona jurídica, incorporar además continuidad de roles, auditabilidad, segregación de funciones, concentración de proveedor e impacto de negocio.
10. **Verificación de recuperabilidad.** Una capacidad de continuidad no se considera demostrada solo porque exista un template. Cuando el impacto lo justifique, probar que un contexto fresco puede localizar la autoridad, reconstruir el estado correcto, preservar Gates/postcondiciones y continuar con una siguiente acción segura.

## Relación con NEUMA Operations v3.7
NEUMA Operations v3.7 incorpora este contrato mediante una nueva referencia portable de resiliencia/continuidad/recuperación, integración con `conversation-health`, `conversation-closure`, `conformance` y el flujo operativo mínimo.

Es un refinamiento backward-compatible de la familia v3. No introduce una arquitectura incompatible ni justifica NEUMA 4.0.

## Límites
- NEUMA no promete recuperar conversaciones eliminadas por un proveedor cuando no exista una copia o autoridad sobreviviente accesible.
- No se convierte cada conversación en un archivo o backup completo.
- No se crean checkpoints después de cada mensaje; se aplica materialidad.
- No se almacenan secretos, credenciales ni razonamiento privado para fines de continuidad.
- No se inventan RPO/RTO, owners ni autorizaciones.
- La ejecución de una recuperación destructiva, restore productivo u otra acción C conserva Gate concreto salvo autorización vigente.

## Postcondición esperada
Después de trabajo material, la pérdida de una conversación no debe implicar necesariamente pérdida del estado intelectual/operativo vigente. El sistema debe poder resolver la última autoridad/checkpoint suficiente, reconstruir un contexto mínimo fiable y retomar desde una acción segura con incertidumbre residual explícita.

## Evidencia inicial
La necesidad fue observada durante la evolución de NEUMA Operations: una conversación eliminada obligó a reconstruir trabajo reciente desde la skill vigente, documentación rectora, GitHub y Notion. La recuperación fue posible, pero el evento evidenció que la recuperabilidad no debía depender de rastros accidentales. v3.7 convierte esa lección en un contrato operativo explícito.
