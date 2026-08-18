# Jerarquía de fuentes de NEUMA 3.0

## Regla
La actualidad de un archivo por sí sola no determina autoridad. La prioridad combina **carácter rector, aprobación/estado, vigencia, ubicación y fecha**.

## Línea base interna actual
1. **NEUMA 3.0 — Manual de Gobierno**: documento rector e integrador del marco. Línea base interna vigente: **v1.1 — vigente interno — consolidación operativa**.
2. **NEUMA 3.0 — Anexos Operativos**: contiene, entre otros, Constitución Operativa y Arquitectura Operativa; desarrolla la aplicación del Manual y debe permanecer alineado con él.
3. **NEUMA — Prompts / continuidad consolidada**: evidencia reciente de decisiones metodológicas y configuración vigente; útil para identificar cambios posteriores que deban reconciliarse con los documentos rectores, sin sustituirlos automáticamente.
4. **Registros de decisiones y ADR**: documentan decisiones específicas y su trazabilidad dentro de su alcance.
5. **Material estratégico, presentaciones y documentos históricos**: fuentes contextuales, comparativas o de evolución; no prevalecen sobre documentos rectores vigentes.

## Fuentes históricas
Los archivos ubicados en `OLD/`, incluido **NEUMA — Estrategia 2026**, se consideran históricos salvo decisión expresa de recuperación. Pueden contener ideas valiosas —por ejemplo análisis comparativos— que deben revalidarse antes de incorporarse al marco vigente.

## Regla de conflicto
Cuando dos documentos difieran:
1. comprobar si uno es histórico o sustituido;
2. comparar estado, fecha y carácter rector;
3. identificar si existe una decisión posterior explícita;
4. no fusionar silenciosamente conceptos incompatibles;
5. elevar a decisión metodológica cuando la discrepancia cambie principios, alcance, roles o gobierno.

## SharePoint y GitHub
- SharePoint conserva el **corpus interno rector y sus originales**.
- `Neuma-Core` conserva únicamente conocimiento deliberadamente publicable/versionable y decisiones públicas o técnicas apropiadas.
- Una síntesis pública en GitHub no sustituye automáticamente el documento interno del que deriva.
- El estado o licencia de un artefacto público no debe extrapolarse al corpus interno sin una decisión explícita.
