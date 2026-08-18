# ADR-003 — Bootstrap documental y gobierno de artefactos de proyectos

## Estado
Aprobada / vigente. Integrada en `main` mediante PR #9 (squash merge `96f8daafaf6e79f11c419680b60e1e75f669193c`).

## Contexto
Los proyectos ChatGPT necesitan iniciar y continuar con mínima carga manual sin depender de memoria volátil ni de copiar el NEUMA Project Core en cada campo de instrucciones. En paralelo, los artefactos DOCX, XLSX, PPTX y PDF requieren estándares reutilizables y verificables sin convertir defaults de presentación en reglas rígidas.

## Decisión
1. SharePoint conserva el Project Core, estándares/plantillas de artefactos y cada rector `<Proyecto> - Inst Proyecto.DocX`.
2. Cada rector es autosuficiente al momento de su baseline: incorpora el Core vigente, reglas específicas y referencia canónica al repositorio del proyecto.
3. El campo de instrucciones del Proyecto ChatGPT utiliza un puntero mínimo al rector y al repositorio; no exige cargar el rector como fuente del proyecto.
4. Los estándares de artefactos se resuelven desde SharePoint cuando estén accesibles; las instrucciones específicas y las skills técnicas del formato prevalecen sobre defaults visuales.
5. La baseline incorporada no implica sincronización perpetua. Cambios materiales del Core se propagan mediante actualización controlada del rector cuando corresponda.
6. La reejecución del bootstrap es idempotente; divergencias humanas materiales no se sobrescriben silenciosamente.

## Consecuencias
- Menor trabajo manual y menor dependencia de memoria conversacional.
- Mejor consistencia y trazabilidad entre proyectos y artefactos.
- Necesidad de gobernar cambios materiales del Core y evitar deriva de rectores antiguos.
- GitHub registra el contrato publicable, no las plantillas internas ni contenido confidencial de proyectos.

## Relación con decisiones previas
Complementa ADR-001 (arquitectura federada) y ADR-002 (proyección controlada GitHub → Notion); no modifica sus límites de autoridad.
