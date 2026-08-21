# ADR-004 — SoR y CI/CD del sitio web NEUMA

- Estado: Aceptada / vigente, reconciliada con ADR-010
- Fecha: 2026-08-18; reconciliación 2026-08-21

## Contexto
El sitio público NEUMA fue entregado como proyecto Angular sobre VPS IONOS/Ubuntu/Nginx. La entrega histórica reside en SharePoint; el modelo heredado de publicación manual dificultaba trazabilidad, reproducibilidad y rollback.

## Decisión
1. Mantener SharePoint como autoridad de entrega histórica y evidencia interna, no como repositorio vivo de código.
2. `gonzaloaromerob/Neuma-Web` es el SoR del código fuente y CI/CD.
3. `Neuma-Core` permanece separado para metodología, arquitectura, decisiones y, desde ADR-010, estado operacional versionable.
4. Backlog/riesgos/Gates operativos aptos para publicación se mantienen en `Neuma-Core` (`operations/STATE.md` o Issues/Projects sólo cuando aporten valor material). Notion deja de ser SoR para trabajo nuevo.
5. La VPS IONOS es exclusivamente runtime de producción.
6. Despliegue gobernado mediante GitHub Actions + SSH, releases inmutables identificadas por commit SHA y symlink atómico.
7. Mantener Gate humano para publicación PROD y cambios materiales de infraestructura/secrets.

## Consecuencias positivas
- cambios reproducibles y auditables;
- rollback rápido;
- menor dependencia de conocimiento individual;
- separación clara entre código, metodología, operación y runtime;
- menor topología persistente y menor necesidad de reconciliación entre plataformas.

## Estado de implementación
`Neuma-Web`, CI/CD productivo y rollback fueron implementados y validados. La arquitectura viva se documenta en `architecture/neuma-web-operations.md`; tareas/riesgos abiertos están en `operations/STATE.md`.

## Alternativas descartadas
- SharePoint como repositorio vivo de Angular;
- editar directamente la VPS;
- incorporar Angular dentro de `Neuma-Core`;
- mantener Notion como capa operativa adicional sin ventaja material demostrada.

## Criterio de reversión
La decisión podrá revisarse si cambia materialmente el hosting o si otra plataforma ofrece menor riesgo/costo total sin sacrificar control, trazabilidad, reversibilidad ni independencia del código fuente.