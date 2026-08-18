# Mapa del corpus NEUMA 3.0

## Propósito
Este mapa separa autoridad metodológica, operación vigente, estrategia histórica y publicación pública. La ubicación o fecha de un archivo no basta por sí sola para determinar autoridad.

## Corpus interno rector — SharePoint

| Artefacto | Estado / función | Prioridad |
|---|---|---|
| `NEUMA 3.0 - Manual de Gobierno.DocX` | Documento rector e integrador; **v1.1, vigente interno, consolidación operativa** | 1 |
| `NEUMA 3.0 - Anexos Operativos.DocX` | Constitución Operativa, Arquitectura Operativa e instrumentos de aplicación; subordinado al Manual | 2 |
| `NEUMA - Prompts.DocX` | Continuidad consolidada reciente; identifica decisiones posteriores y configuración vigente sin sustituir automáticamente al corpus rector | 3 |
| `NEUMA - Runbook Integraciones.DocX` | Referencia operativa de integraciones; debe mantenerse alineada con NEUMA Operations y revalidarse por capacidad | Operativa |
| ADR / registros de decisión | Evidencia de decisiones específicas y trazabilidad dentro de su alcance | Por decisión |

## Corpus complementario vigente

Incluye personalizaciones, instrucciones de Projects, plantillas, catálogos, checklists y materiales operativos cuya autoridad es contextual. No deben modificar silenciosamente los principios rectores.

## Corpus histórico

Los materiales bajo `OLD/`, incluidas versiones previas de presentaciones y `NEUMA - Estrategia 2026`, son fuentes históricas y contextuales. Pueden contener propuestas, comparaciones o lenguaje valioso, pero cualquier recuperación exige revalidación contra el corpus rector y fuentes externas actuales.

### Elemento histórico especialmente rescatable

`NEUMA - Estrategia 2026` contiene una comparación útil con marcos adyacentes (NIST AI RMF, ISO/IEC 42001, UNESCO, OECD y enfoques de alineación de modelos). Esa sección debe actualizarse antes de reutilizarse y no debe presentarse como prueba de singularidad o superioridad de NEUMA.

## Corpus público — GitHub

`Neuma-Core` debe contener únicamente:
- síntesis metodológicas deliberadamente publicables;
- ADR apropiados para publicación;
- arquitectura y documentación técnica no sensible;
- materiales cuya licencia, procedencia y sensibilidad estén claras.

La versión pública nunca sustituye automáticamente al corpus interno rector. El licenciamiento de un activo público tampoco se extrapola al corpus interno ni a otros tipos de activo.

## Regla de reconciliación

Ante discrepancias:
1. identificar versión, estado, fecha, ubicación y carácter rector;
2. buscar una decisión posterior explícita;
3. preservar la discrepancia si aporta evidencia histórica;
4. no mezclar silenciosamente conceptos incompatibles;
5. elevar cambios de principios, propósito, roles o gobierno a decisión metodológica formal.
