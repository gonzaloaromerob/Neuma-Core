# ADR-004 — SoR y CI/CD del sitio web NEUMA

- Estado: Aceptada
- Fecha: 2026-08-18

## Contexto

El sitio público NEUMA fue entregado como un proyecto Angular y actualmente se opera sobre una VPS IONOS/Ubuntu/Nginx. La entrega histórica reside en SharePoint e incluye metadatos Git que apuntan al repositorio del desarrollador. El procedimiento heredado de publicación es manual y depende de transferencia de archivos y acceso interactivo al servidor.

Este modelo dificulta trazabilidad, reproducibilidad, rollback y operación asistida por IA con mínimo trabajo humano.

## Decisión

1. Mantener SharePoint como autoridad de la entrega histórica y evidencia interna, no como repositorio vivo de código.
2. Crear un repositorio GitHub dedicado `Neuma-Web` bajo control de Gonzalo y convertirlo en SoR del código fuente y CI/CD.
3. Mantener `Neuma-Core` separado para metodología, arquitectura y decisiones versionables/publicables.
4. Usar Notion para backlog, releases, riesgos, Gates y trazabilidad operativa.
5. Tratar la VPS IONOS exclusivamente como runtime de producción.
6. Sustituir el despliegue manual por GitHub Actions + SSH/rsync, releases inmutables identificados por commit SHA y activación mediante symlink atómico.
7. Mantener aprobación humana para publicación a PROD y cambios de infraestructura/secrets.

## Consecuencias

### Positivas

- cambios reproducibles y auditables;
- rollback rápido;
- menor dependencia del conocimiento del desarrollador original;
- separación clara entre código, metodología, operación y runtime;
- habilita que NEUMA Operations prepare cambios y QA con intervención humana concentrada en el Gate productivo.

### Costos y dependencias

- creación e importación inicial de `Neuma-Web`;
- configuración única de GitHub Actions y Environment `production`;
- creación de usuario/clave SSH de despliegue en IONOS;
- ajuste único de Nginx para servir `/var/www/neuma/current`;
- primer despliegue controlado y validación de rollback.

## Alternativas descartadas

- **SharePoint como repositorio vivo de Angular:** inadecuado para branching, PR, CI/CD y builds reproducibles.
- **Editar directamente la VPS:** rápido pero frágil, poco auditable y propenso a divergencia.
- **Incorporar Angular dentro de `Neuma-Core`:** mezcla ciclos de vida, riesgos, permisos y pipelines diferentes.
- **Depender de un conector Angular–ChatGPT:** no es necesario; Git/GitHub y CI/CD constituyen la interfaz operacional apropiada.

## Criterio de reversión

La decisión podrá revisarse si cambia materialmente el hosting o si una plataforma administrada ofrece menor riesgo/costo total sin sacrificar control, trazabilidad, reversibilidad ni independencia del código fuente.