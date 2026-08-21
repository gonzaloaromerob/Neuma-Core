# ADR-003 — Bootstrap documental y gobierno de artefactos de proyectos

## Estado
Aprobada / vigente. Integrada originalmente en `main` mediante PR #9 (squash merge `96f8daafaf6e79f11c419680b60e1e75f669193c`) y reconciliada posteriormente con la arquitectura desacoplada de NEUMA Core. Extensión operacional de proyección humana definida por ADR-009.

## Contexto
Los proyectos ChatGPT necesitan iniciar y continuar con mínima carga manual sin depender de memoria volátil ni de duplicar NEUMA Core en cada proyecto o documento rector. En paralelo, los artefactos DOCX, XLSX, PPTX y PDF requieren estándares reutilizables y verificables sin convertir defaults de presentación en reglas rígidas.

## Decisión
1. SharePoint conserva el corpus rector interno, los estándares/plantillas canónicos de artefactos y cada rector `<Proyecto> - Inst Proyecto.DocX`.
2. Cada rector contiene únicamente contexto, alcance y reglas específicas del proyecto. No incorpora ni congela una baseline de NEUMA Core.
3. NEUMA Core y la operación transversal se resuelven desde la skill NEUMA Operations; el rector no los reproduce ni los sustituye.
4. El rector y el campo ChatGPT Project Instructions son artefactos distintos con referencia unidireccional: Project Instructions puede apuntar al rector; el rector no contiene, reproduce, recomienda, cita, plantilla ni preserva el texto del campo Project Instructions.
5. El campo Project Instructions utiliza un puntero mínimo estable al rector y, cuando sea material, a NEUMA Operations. No exige cargar el rector como fuente del proyecto ni duplicar el Core.
6. Los estándares y plantillas de artefactos se resuelven desde su System of Record antes de generar o reformatear. Si existe un override organizacional vigente, este debe recuperarse y aplicarse; el default portable solo procede cuando no existe tal override. Las instrucciones específicas del entregable y las skills técnicas del formato prevalecen sobre defaults visuales.
7. Esta precedencia aplica transversalmente a DOCX, XLSX, PPTX y PDF, manteniendo estándares y QA específicos para cada familia.
8. Cuando el entorno declare una **proyección humana operacional** —por ejemplo una carpeta SharePoint/Office usada por el propietario humano para seguir el proyecto— el bootstrap debe identificarla como proyección gobernada. Los cambios materiales posteriores deben mantenerla suficientemente actualizada para que el humano pueda reconstruir estado, decisiones, Gates y fuentes sin depender de GitHub/Notion internos. Esta regla se desarrolla en ADR-009 y sigue siendo configuración del entorno, no dependencia universal de NEUMA.
9. La reejecución del bootstrap es idempotente; divergencias humanas materiales no se sobrescriben silenciosamente.
10. Los cambios materiales de NEUMA Core se gobiernan en su fuente correspondiente y no requieren regenerar rectores salvo que afecten reglas específicas del proyecto.

## Consecuencias
- Menor duplicación y menor riesgo de deriva entre NEUMA Core y los proyectos.
- Separación explícita entre contrato transversal, configuración específica del proyecto, Project Instructions y estándares de artefactos.
- El texto operativo del campo Project Instructions no se convierte en contenido del documento rector ni en una sección sugerida dentro de este.
- Mejor consistencia y trazabilidad entre proyectos y artefactos.
- Los estándares organizacionales no pueden ser sustituidos silenciosamente por defaults portables por omisión de resolución.
- Cuando exista una proyección humana operacional configurada, su obsolescencia material bloquea el cierre exitoso aunque los SoR técnicos estén actualizados.
- GitHub registra el contrato publicable, no las plantillas internas ni contenido confidencial de proyectos.

## Relación con decisiones previas y posteriores
Complementa ADR-001 (arquitectura federada) y ADR-002 (proyección controlada GitHub → Notion). ADR-009 extiende esta decisión con aprendizaje gobernado, proyección humana operacional y QA cruzado.
