# ADR-010 — Consolidación operacional en GitHub y retiro de Notion

## Estado
Aprobada por autorización humana explícita `GO-GO-GO` el 21 de agosto de 2026. **Cerrada operacionalmente el 21 de agosto de 2026 tras la limpieza completa de Notion y la verificación de reconstrucción sin esa plataforma.** Sustituye, en lo relativo al rol operativo de Notion, la arquitectura definida por ADR-001 y ADR-002. No modifica NEUMA Core 4.0.

## Contexto
NEUMA operaba con tres superficies persistentes principales: SharePoint para corpus interno y artefactos Office, GitHub para decisiones/versionado y Notion para proyectos, riesgos, tareas, Gates, evidencias referenciadas y seguimiento. La experiencia real mostró que mantener proyecciones entre tres plataformas aumenta deriva, QA cruzado y esfuerzo humano sin aportar valor proporcional cuando GitHub puede absorber el estado operativo versionable y SharePoint ya funciona como proyección humana documental.

## Decisión
1. **GitHub es el SoR operacional versionable de NEUMA** para decisiones, arquitectura, estado operativo, proyectos/workstreams, riesgos, tareas, Gates y referencias de evidencia que sean aptas para este repositorio.
2. **SharePoint permanece como SoR documental interno y proyección humana operacional** para rectores, estándares, plantillas, DOCX/XLSX/PPTX, entregables y material no apropiado para un repositorio público/versionable.
3. **Los originales de evidencia permanecen en su SoR de origen**. GitHub guarda solamente referencia, clasificación y estado cuando sea necesario; no copia material interno/confidencial.
4. **Notion queda retirado de la topología NEUMA.** No es SoR, proyección, dependencia, destino operativo ni postcondición. No se crean nuevos objetos NEUMA allí.
5. El estado operativo consolidado reside en `operations/STATE.md` para minimizar objetos y mantenimiento. Issues/Projects sólo se usarán cuando aporten una ventaja operacional material, no por defecto.
6. Las ADR históricas conservan su valor como registro de decisiones; cuando una regla anterior dependa de Notion, ADR-010 prevalece para el estado vigente.
7. La postcondición de cambios materiales se simplifica a **GitHub + SharePoint + SoR original aplicable**, con QA cruzado proporcional.
8. La skill NEUMA Operations trata conectores/plataformas como configuración del entorno y prefiere la topología mínima suficiente. Si dos SoR cubren autoridad y trazabilidad sin pérdida material, no mantener una tercera plataforma por inercia.

## Migración completada
Se preservó en GitHub el conocimiento único necesario del antiguo estado en Notion: proyectos relevantes, riesgos, tareas abiertas, Gate-002, referencias verificadas de evidencia y estado de transición. Decisiones ya canónicas en ADR no se duplicaron; tareas cerradas se conservaron sólo como trazabilidad mínima cuando explican un control vigente.

## Higiene completada
Tras verificar que GitHub puede reconstruir el estado sin Notion, se ejecutó higiene del repositorio: retiro de residuos obsoletos/redundantes del árbol activo, corrección de referencias vigentes y preservación de historia mediante Git en vez de mantener copias muertas en `main`.

Posteriormente se ejecutó la retirada completa de contenido NEUMA en Notion. El usuario completó manualmente el residuo de plataforma que el conector no podía purgar. La topología final ya no contempla Notion en ninguna función NEUMA.

## Postcondición final
La arquitectura operativa queda reducida a **GitHub como cerebro versionado/operacional + SharePoint como superficie documental humana**, coordinados por NEUMA Operations y complementados por los SoR originales aplicables.

La prueba de reconstrucción debe poder resolver, sin conversación previa ni Notion:
- qué es NEUMA y su release vigente;
- qué decisiones/ADR gobiernan;
- qué estado, riesgos, tareas y Gates siguen abiertos;
- qué skill operacional gobierna la ejecución;
- qué documentos/estándares/plantillas internos viven en SharePoint;
- qué SoR originales conservan evidencia no trasladable.

Resultado: **PASS**.