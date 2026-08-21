# NEUMA Core

Repositorio público y versionado para conocimiento de NEUMA deliberadamente apto para control de versiones y publicación.

## Propósito
Conservar decisiones públicas o técnicas, arquitectura publicable, documentación metodológica seleccionada, estado operacional versionable, investigación, especificaciones y artefactos técnicos cuya procedencia y sensibilidad permitan alojarlos aquí.

**GitHub no es el System of Record del corpus rector interno de NEUMA.** El corpus interno rector y sus originales permanecen en SharePoint. Una síntesis pública o un artefacto versionado en este repositorio no sustituye automáticamente al documento interno del que deriva.

## Estructura
- `decisions/` — Architecture Decision Records (ADR) y decisiones versionadas apropiadas para publicación.
- `architecture/` — arquitectura conceptual y operativa publicable.
- `operations/` — estado operacional consolidado apto para GitHub: proyectos/workstreams, riesgos, tareas, Gates y referencias de evidencia.
- `docs/` — documentación consolidada vigente.
- `skills/` — especificaciones y artefactos técnicos de skills cuando sean publicables.
- `research/` — investigación y análisis bajo control de versiones.

## Gobierno
- Mantener un único System of Record explícito por objeto.
- **GitHub / Neuma-Core** es el SoR de decisiones, arquitectura y estado operacional versionable apto para publicación.
- **SharePoint** conserva el corpus rector interno de NEUMA, estándares/plantillas canónicos, Office, entregables e históricos, y funciona como proyección humana operacional.
- La skill NEUMA Operations transporta el contrato transversal de NEUMA Core y la operación portable; los rectores de proyecto no lo duplican ni congelan.
- Los rectores `<Proyecto> - Inst Proyecto.DocX` permanecen en SharePoint y contienen únicamente contexto, alcance y reglas específicas.
- Para DOCX, XLSX, PPTX y PDF, resolver estándar/plantilla organizacional desde su SoR antes de generar o reformatear; los defaults portables sólo aplican sin override gobernado.
- Los originales de evidencia permanecen en sus repositorios autorizados; GitHub guarda referencias y estado sólo cuando aportan continuidad o trazabilidad.
- **Notion deja de ser SoR operativo para trabajo nuevo.** Durante la transición se conserva como fuente legado sin proyecciones nuevas; su limpieza se gobierna aparte.
- Evitar sincronización bidireccional automática y capas persistentes sin valor material.
- Los cambios materiales pasan por rama/PR y revisión proporcional al riesgo.
- No almacenar secretos ni información sensible innecesaria en este repositorio público.

## Licenciamiento
El licenciamiento se gobierna por tipo de activo y no debe inferirse por proximidad dentro del repositorio.

- El archivo raíz `LICENSE` es un aviso de alcance y estado de licenciamiento del repositorio; no concede por sí mismo una licencia abierta general sobre toda la documentación metodológica.
- El texto de la licencia MIT se conserva separadamente en `LICENSES/MIT.txt` para software o código que se identifique expresamente como cubierto por MIT.
- La documentación metodológica pública no se considera licenciada bajo Creative Commons hasta que exista una decisión explícita, revisión de titularidad/procedencia y delimitación del corpus aplicable.
- Las marcas y signos distintivos, incluido el nombre NEUMA cuando corresponda, no quedan licenciadas por MIT ni por una eventual licencia Creative Commons salvo autorización expresa.

## Estado
**NEUMA 4.0 es la release canónica vigente del marco**, publicada el 2026-08-20. Su declaración y alcance están documentados en `docs/neuma-4.0-release.md`.

NEUMA Operations conserva identidad y lifecycle propios; la release del marco no fuerza sincronización nominal de sus componentes. La topología operativa vigente está definida por ADR-010 y `operations/STATE.md`.

Los módulos Derecho, Ciberseguridad y Auditoría permanecen en `v0.2-pilot` hasta evidencia y decisión específicas.

El sitio web productivo se gestiona separadamente en `gonzaloaromerob/Neuma-Web`.

NEUMA es un marco vivo. Una release estable representa una versión gobernada, no una declaración de perfección ni una cesión implícita de derechos.