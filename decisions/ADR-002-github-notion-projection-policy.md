# ADR-002 — Política de proyección GitHub → Notion

## Estado
**Reemplazada por ADR-010** desde el 21 de agosto de 2026 para trabajo nuevo. Se conserva como registro histórico de la política validada durante el piloto.

## Decisión humana histórica
Se seleccionó la opción B del Gate-002: **proyección unidireccional controlada GitHub → Notion**.

## Contexto histórico
NEUMA Operations utilizaba GitHub como System of Record para conocimiento versionable y Notion como capa operativa para proyectos, relaciones, riesgos, tareas, Gates e índices. Una sincronización bidireccional automática introducía conflictos de autoridad, duplicación, loops y efectos secundarios difíciles de compensar.

Fuente piloto: https://docs.google.com/document/d/1VKxZs1FfZvpOa5nTD8OsqcLErfIIdSIvs5B8Z3_LdSI/edit

## Política histórica
1. Dirección por defecto GitHub → Notion para metadatos y estados derivados.
2. GitHub conservaba autoridad sobre ADR, metodología, código, skills y especificaciones alojadas allí.
3. Notion no sobrescribía GitHub automáticamente.
4. Flujo inverso material requería intención explícita y Gate.
5. Idempotencia, resolución explícita de conflictos, control de efectos secundarios y sensibilidad eran obligatorios.
6. Cambios materiales requerían reconciliación proactiva de proyecciones.

## Evolución posterior
ADR-010 elimina la necesidad de proyección GitHub → Notion como operación futura. El estado operacional versionable se consolida directamente en GitHub; SharePoint conserva la superficie documental humana y los originales internos. Notion queda como fuente legado temporal hasta una limpieza posterior.

Por tanto:
- no crear nuevas proyecciones GitHub → Notion;
- no mantener sincronización bidireccional;
- no tratar Notion como postcondición de cambios nuevos;
- preservar este ADR únicamente como evidencia histórica de una decisión válida para la topología anterior.

## Contrato que permanece vigente
`SoR → identidad estable → resolución → create/update/no-op/conflict → verificación → trazabilidad → compensación` sigue siendo válido para cualquier proyección o integración futura.

## Evidencia de validación histórica
El 2026-08-18 se demostró idempotencia con ADR-002 y se detectó/compensó una divergencia deliberada en Notion sin modificar el canónico. Esa evidencia motivó posteriormente la simplificación de arquitectura formalizada en ADR-010.