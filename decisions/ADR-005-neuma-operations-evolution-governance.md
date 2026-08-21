# ADR-005 — Gobierno de evolución de NEUMA Operations

## Estado
Validada por decisión humana el 2026-08-20. Sus controles siguen vigentes y son complementados por ADR-009 y ADR-010.

## Contexto
La evolución de NEUMA Operations requiere controles explícitos para evitar regresiones sistémicas, contaminación entre contextos, resolución heurística de conflictos de autoridad, crecimiento normativo sin fundamento material o dependencia del usuario como recordatorio operativo.

## Decisión
Adoptar los siguientes controles portables para NEUMA Operations:

1. **Seguridad de regresión:** todo cambio material identifica invariantes y flujos afectados y aplica pruebas representativas suficientes.
2. **Aislamiento contextual:** personas, organizaciones, clientes, asuntos y proyectos permanecen aislados por defecto; aprendizaje reusable se abstrae/anonimiza.
3. **Conflicto de autoridad:** si dos fuentes autorizadas discrepan materialmente y la precedencia no puede resolverse, el estado es `conflict`; no se fusiona ni propaga heurísticamente.
4. **Gate de evolución:** una regla central sólo cambia con fundamento material: fallo/riesgo observado, fricción recurrente, cambio de plataforma, evidencia o simplificación neta.
5. **Trazabilidad mínima:** conservar únicamente evidencia durable necesaria para reconstruir qué cambió, por qué y cómo se verificó.
6. **Responsabilidad proactiva de reconciliación:** después de un cambio material, NEUMA identifica SoR, proyecciones y derivados gobernados afectados y decide `create/update/no-op/conflict` o limpieza acotada. No depende del usuario como recordatorio.
7. **Higiene gobernada proporcional:** retirar o corregir objetos verificablemente obsoletos, duplicados, reemplazados o huérfanos, preservando historia en el mecanismo adecuado. En Git, la historia del repositorio puede sustituir archivos muertos mantenidos sólo como archivo.
8. **Atención humana mínima:** completar A/B autorizado y reversible antes de escalar; la intervención humana se reserva para autoridad, criterio, aceptación de riesgo, pérdida material o acciones C no autorizadas.
9. **Topología mínima suficiente:** conforme a ADR-010, no mantener una plataforma, proyección o capa persistente por inercia si sus funciones pueden consolidarse sin pérdida material y con menor carga humana.

## Evolución posterior
v3.5 estabilizó la frontera Core/Operations y superficie decisional mínima; v3.6 incorporó reconciliación proactiva; v3.9–v3.11 añadieron no-memory execution, aprendizaje gobernado y proyección humana; v3.12 incorpora consolidación de plataformas y topología mínima suficiente.

## Verificación y postcondición vigente
- El bundle completo de cada evolución material debe validarse y empaquetarse con el mecanismo oficial.
- GitHub, SharePoint y cualquier SoR original/proyección gobernada aplicable se revisan proporcionalmente durante la misma evolución.
- Notion queda fuera de la postcondición para trabajo nuevo conforme a ADR-010; se conserva sólo como fuente legado hasta su limpieza posterior.

## Arquitectura documental vigente
SharePoint conserva corpus rector interno, estándares, plantillas y proyección humana. GitHub conserva decisiones, arquitectura, estado operacional versionable y documentación pública/técnica apropiada. Los originales de evidencia permanecen en su SoR. Notion ya no es SoR operativo para trabajo nuevo.

## Consecuencia
Un cambio material de NEUMA Operations no se considera cerrado hasta verificar su postcondición, reconciliar derivados que deban permanecer consistentes y evaluar higiene proporcional en la topología vigente.