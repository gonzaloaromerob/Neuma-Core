# ADR-010 — Consolidación operacional en GitHub y retiro progresivo de Notion

## Estado
Aprobada por autorización humana explícita `GO-GO-GO` el 21 de agosto de 2026. Sustituye, en lo relativo al rol operativo de Notion, la arquitectura definida por ADR-001 y ADR-002. No modifica NEUMA Core 4.0.

## Contexto
NEUMA operaba con tres superficies persistentes principales: SharePoint para corpus interno y artefactos Office, GitHub para decisiones/versionado y Notion para proyectos, riesgos, tareas, Gates, evidencias referenciadas y seguimiento. La experiencia real mostró que mantener proyecciones entre tres plataformas aumenta deriva, QA cruzado y esfuerzo humano sin aportar valor proporcional cuando GitHub puede absorber el estado operativo versionable y SharePoint ya funciona como proyección humana documental.

## Decisión
1. **GitHub pasa a ser el SoR operacional versionable de NEUMA** para decisiones, arquitectura, estado operativo, proyectos/workstreams, riesgos, tareas, Gates y referencias de evidencia que sean aptas para este repositorio.
2. **SharePoint permanece como SoR documental interno y proyección humana operacional** para rectores, estándares, plantillas, DOCX/XLSX/PPTX, entregables y material no apropiado para un repositorio público/versionable.
3. **Los originales de evidencia permanecen en su SoR de origen**. GitHub guarda solamente referencia, clasificación y estado cuando sea necesario; no copia material interno/confidencial.
4. **Notion deja de ser SoR operativo de destino.** Durante la transición se conserva intacto como fuente legado hasta una iteración posterior de limpieza. No se requiere proyección GitHub → Notion ni sincronización bidireccional.
5. El estado operativo migrado se consolida en `operations/STATE.md` para minimizar objetos y mantenimiento. Issues/Projects sólo se usarán cuando aporten una ventaja operacional material, no por defecto.
6. Las ADR históricas conservan su valor como registro de decisiones; cuando una regla anterior dependa de Notion, ADR-010 prevalece para el estado vigente.
7. La postcondición de cambios materiales se simplifica a **GitHub + SharePoint + SoR original aplicable**, con QA cruzado proporcional. Notion no participa en cierres nuevos.
8. La skill NEUMA Operations debe tratar conectores/plataformas como configuración del entorno y preferir la topología mínima suficiente. Si dos SoR cubren autoridad y trazabilidad sin pérdida material, no mantener una tercera plataforma por inercia.

## Migración inicial
Se preserva en GitHub el conocimiento único necesario de Notion: proyectos relevantes, riesgos, tareas abiertas, Gate-002, referencias verificadas de evidencia y estado de transición. Decisiones ya canónicas en ADR no se duplican; tareas cerradas se conservan sólo como trazabilidad mínima cuando explican un control vigente.

## Higiene posterior
Tras verificar que GitHub puede reconstruir el estado sin Notion, se ejecuta higiene del repositorio: retirar residuos obsoletos/redundantes del árbol activo, corregir referencias vigentes y preservar historia mediante Git en vez de mantener copias muertas en `main`.

## Frontera de esta iteración
- No se elimina ni modifica contenido de Notion.
- No se copian fuentes internas/confidenciales a GitHub.
- La limpieza de Notion queda explícitamente diferida a otra iteración.

## Consecuencia práctica
La arquitectura operativa objetivo queda reducida a **GitHub como cerebro versionado/operacional + SharePoint como superficie documental humana**, coordinados por NEUMA Operations.