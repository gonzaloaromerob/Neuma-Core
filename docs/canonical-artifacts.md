# Artefactos canónicos de NEUMA

## Objetivo
Definir qué contenido pertenece al repositorio público Neuma-Core y qué material debe permanecer en su sistema de origen.

## Canónicos actuales
- docs/neuma-3.0-core.md: núcleo conceptual de NEUMA 3.0.
- architecture/knowledge-governance.md: gobierno federado del conocimiento.
- decisions/ADR-001-federated-knowledge-operations.md: arquitectura federada.
- decisions/ADR-002-github-notion-projection-policy.md: política GitHub a Notion.

## Criterios de promoción
Un artefacto puede convertirse en canónico cuando su contenido sea estable, publicable, tenga procedencia clara, no duplique innecesariamente otro System of Record y su versionado aporte valor.

## Material no canónico por defecto
Documentos fuente, evidencias, propuestas comerciales, información de clientes, notas de reuniones, documentos legales o periciales, experimentos y borradores permanecen en su sistema de origen o en áreas de trabajo apropiadas.

## Ciclo recomendado
experimental -> candidate -> canonical -> superseded -> archived

Los cambios materiales hacia estado canonical deben conservar trazabilidad mediante pull request o ADR, según corresponda.
