# NEUMA Core

Repositorio público y versionado para conocimiento de NEUMA deliberadamente apto para control de versiones y publicación.

## Propósito
Conservar decisiones públicas o técnicas, arquitectura publicable, documentación metodológica seleccionada, investigación, especificaciones y artefactos técnicos cuya procedencia y sensibilidad permitan alojarlos aquí.

**GitHub no es el System of Record del corpus rector interno de NEUMA 3.0.** El corpus interno rector y sus originales permanecen en SharePoint. Una síntesis pública o un artefacto versionado en este repositorio no sustituye automáticamente al documento interno del que deriva.

## Estructura
- `decisions/` — Architecture Decision Records (ADR) y decisiones versionadas apropiadas para publicación.
- `architecture/` — arquitectura conceptual y operativa publicable.
- `docs/` — documentación consolidada, guías y síntesis públicas.
- `skills/` — especificaciones y artefactos técnicos de skills cuando sean publicables.
- `research/` — investigación y análisis bajo control de versiones.
- `archive/legacy-website/` — archivo histórico del antiguo sitio estático, preservado sin función operativa actual.

## Gobierno
- Mantener un único System of Record explícito por objeto.
- SharePoint conserva el corpus rector interno de NEUMA 3.0.
- GitHub conserva únicamente conocimiento deliberadamente versionable/publicable y artefactos técnicos apropiados.
- Notion conserva proyectos, relaciones, riesgos, tareas, Decision Gates y seguimiento operativo.
- Los repositorios documentales autorizados conservan evidencia u originales cuando corresponda.
- Evitar sincronización bidireccional automática; preferir referencias cruzadas y proyecciones idempotentes.
- Los cambios materiales deben pasar por rama/PR y revisión proporcional al riesgo.
- No almacenar secretos ni información sensible innecesaria en este repositorio público.

## Licenciamiento
El licenciamiento se gobierna por tipo de activo y no debe inferirse por proximidad dentro del repositorio.

- El archivo raíz `LICENSE` es un aviso de alcance y estado de licenciamiento del repositorio; no concede por sí mismo una licencia abierta general sobre toda la documentación metodológica.
- El texto de la licencia MIT se conserva separadamente en `LICENSES/MIT.txt` para software o código que se identifique expresamente como cubierto por MIT.
- La documentación metodológica pública no se considera licenciada bajo Creative Commons hasta que exista una decisión explícita, revisión de titularidad/procedencia y delimitación del corpus aplicable.
- Las marcas y signos distintivos, incluido el nombre NEUMA cuando corresponda, no quedan licenciados por MIT ni por una eventual licencia Creative Commons salvo autorización expresa.

## Estado
`Neuma-Core` reemplazó el propósito histórico de `Neuma-WebSite`. El sitio web productivo se gestiona separadamente y el legado del sitio anterior está archivado bajo `archive/legacy-website/`.

NEUMA es un marco vivo. Una release estable representa una versión gobernada, no una declaración de perfección ni una cesión implícita de derechos.