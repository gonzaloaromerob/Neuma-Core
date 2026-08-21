# ADR-006 — Resiliencia de estado, continuidad y recuperación

## Estado
Aprobada / vigente. Su contrato de continuidad permanece activo y se reconcilia con ADR-010 desde el 21 de agosto de 2026.

## Contexto
El trabajo humano–IA puede acumular decisiones, estado operativo, evidencia, artefactos y esfuerzo material a lo largo de conversaciones extensas. Una conversación, prompt o contexto local del runtime son superficies transitorias y no deben convertirse en el único contenedor de estado relevante.

## Decisión
Adoptar para NEUMA Operations un contrato portable de **resiliencia de estado, continuidad y recuperación**:

1. **La conversación no es System of Record.** El estado material reside o puede reconstruirse desde SoR, checkpoints y proyecciones gobernadas proporcionales al impacto.
2. **Checkpointing proporcional.** Crear/refrescar un checkpoint mínimo cuando perder el estado pueda causar retrabajo material, ambigüedad o riesgo; usar `no-op` si el estado durable ya es suficiente.
3. **Estado recuperable mínimo.** Conservar objetivo vigente, estado verificado, decisiones condicionantes, pendientes/Gates, SoR e identidades estables, riesgos/dependencias, postcondición pendiente y primera acción segura. No replicar transcript, secretos ni razonamiento privado.
4. **Recuperación desde autoridad sobreviviente.** Resolver primero SoR/checkpoint, releer evidencia canónica mínima y reconstruir working set sin inventar contenido perdido.
5. **Continuidad conversacional gobernada.** `conversation-health` y `conversation-closure` pueden facilitar transferencia, pero el prompt de continuidad no debe ser la única copia del estado.
6. **Resiliencia de proyecciones.** Los derivados deben ser reconstruibles desde el canónico cuando sea práctico; después de cambios materiales aplicar reconciliación e higiene.
7. **Backup y restauración verificables.** Un backup no demuestra recuperación hasta verificar integridad/readback/restauración proporcional.
8. **BCP/DRP proporcional.** Resolver objetos críticos, dependencias, copias, orden de recuperación, roles, post-verificación y fallback/rollback. RPO/RTO no se inventan.
9. **Aplicabilidad PN/PJ.** Escalar controles según impacto, sensibilidad, dependencia y roles.
10. **Verificación de recuperabilidad.** Cuando el impacto lo justifique, probar que un contexto fresco localiza autoridad, reconstruye estado correcto, preserva Gates/postcondiciones y continúa con acción segura.

## Topología de recuperación vigente
Conforme a ADR-010, para esta instalación el estado material de NEUMA debe poder reconstruirse desde:
- ADR vigentes y `operations/STATE.md` en `Neuma-Core`;
- NEUMA Operations vigente;
- corpus/proyección humana SharePoint;
- SoR original de evidencia cuando corresponda.

Notion deja de formar parte de la cadena de recuperación para trabajo nuevo. Se conserva temporalmente como fuente legado hasta su limpieza posterior.

## Límites
- NEUMA no promete recuperar conversaciones eliminadas sin copia o autoridad sobreviviente.
- No se archiva cada conversación completa.
- No se almacenan secretos, credenciales ni razonamiento privado para continuidad.
- No se inventan RPO/RTO, owners ni autorizaciones.
- Restore destructivo/productivo u otra acción C conserva Gate concreto salvo autorización vigente.

## Postcondición
La pérdida de una conversación no debe implicar pérdida del estado intelectual/operativo material cuando existen SoR/checkpoints adecuados. El sistema debe poder resolver la última autoridad suficiente y retomar desde una acción segura con incertidumbre explícita.

## Evidencia histórica
La necesidad se observó al reconstruir trabajo tras pérdida de conversación desde skill, documentación rectora y plataformas persistentes. La lección permanece válida; ADR-010 simplifica ahora la topología de recuperación al retirar Notion del circuito operativo nuevo.