# NEUMA v4 — Piloto de workflow: Auditoría

## Estado
Especificación piloto `v0.1-pilot`. No es una skill publicada ni declara conformidad hasta ejecutar la suite v4.

## Identidad
- **ID:** `neuma-workflow-audit`
- **Tipo:** workflow/capacidad
- **Versión piloto:** `v0.1-pilot`
- **Compatibilidad objetivo:** arquitectura modular NEUMA v4 + NEUMA Operations v3.7 como baseline transversal mientras se valida la evolución de Operations.

## Propósito
Aportar un contrato transversal para trabajos de auditoría y aseguramiento: alcance, criterio, evidencia, hallazgos, trazabilidad, independencia y cierre verificable, sin incorporar conocimiento disciplinar específico como verdad propia.

## Alcance
- definir objetivo, alcance, objeto auditado, periodo y criterio aplicable;
- separar evidencia, observación, inferencia, hallazgo, riesgo y recomendación;
- resolver fuentes y SoR del objeto auditado;
- mantener trazabilidad suficiente para reproducir conclusiones;
- identificar limitaciones de alcance, evidencia faltante y conflictos de independencia;
- verificar cierre y postcondición de acciones correctivas cuando proceda.

## Exclusiones
- no inventar criterios de auditoría;
- no sustituir el dominio técnico/jurídico/financiero aplicable;
- no convertir una muestra limitada en certeza sobre la población sin fundamento;
- no presentar una opinión de aseguramiento formal si no existe mandato, criterio y evidencia suficientes;
- no ocultar limitaciones materiales de alcance.

## Autoridad y SoR
El workflow no posee una jerarquía disciplinar propia. Debe resolver, en este orden lógico:
1. mandato, alcance, carta de encargo o instrucción gobernada;
2. criterio de auditoría aplicable y su autoridad declarada;
3. SoR y evidencia primaria del objeto auditado;
4. módulos de dominio activos para interpretar evidencia especializada;
5. fuentes secundarias solo como apoyo.

## Frescura
La evidencia debe corresponder al periodo auditado y, cuando la conclusión dependa de estado actual, verificar vigencia. No mezclar evidencia de periodos distintos sin declararlo.

## Riesgos y controles adicionales
- **Independencia/objetividad:** declarar conflicto material cuando exista.
- **Muestreo:** no generalizar más allá de lo que el diseño permite.
- **Evidencia insuficiente:** degradar conclusión o registrar limitación; no completar huecos con inferencia silenciosa.
- **Hallazgos:** vincular condición, criterio, evidencia y efecto/riesgo.
- **Acciones correctivas:** no cerrar por declaración; verificar postcondición cuando sea material.

## Gates humanos específicos
Requerir Gate cuando corresponda para:
- emitir o publicar una opinión/informe con efectos externos o regulatorios;
- aceptar una limitación de alcance material;
- modificar criterio o alcance de forma que cambie la conclusión;
- cerrar una excepción de riesgo material sin evidencia suficiente;
- escalar hallazgos sensibles a terceros o autoridades.

## Dependencias y conectores
Puede usar repositorios documentales, ticketing, GRC, SIEM, ERP, GitHub, gestores de proyectos u otros SoR según el objeto auditado. No depende de un proveedor concreto.

## Activación
Activar cuando la tarea requiera evaluar un objeto frente a criterios definidos, producir hallazgos trazables, revisar controles, validar cumplimiento o verificar acciones correctivas.

## Desactivación
No activar para análisis exploratorio, asesoría o implementación ordinaria si no existe una función real de evaluación contra criterio.

## Composición
- Con `neuma-domain-cybersecurity`: Auditoría gobierna alcance/criterio/evidencia/hallazgo; Ciberseguridad gobierna interpretación técnica y autoridad técnica.
- Con `neuma-domain-law`: Auditoría gobierna el encargo y evidencia; Derecho gobierna autoridad jurídica e interpretación normativa.
- Con cualquier dominio: el workflow no desplaza la autoridad disciplinar del módulo de dominio.

## Conflictos
Si el workflow exige evidencia o trazabilidad más estricta, puede endurecer controles. No puede rebajar requisitos de Core, Operations o módulos de dominio. Conflictos materiales no resolubles se elevan como Gate humano.

## Conformance
Debe pasar M01–M15 de `docs/neuma-v4-module-conformance-suite.md` y baseline Core/Operations aplicable. Casos especialmente críticos: M03, M05, M06, M07, M09, M10, M11, M12 y M13.

## Deprecación y migración
Preservar mandato, alcance, criterio, evidencia, hallazgos, Gates abiertos y estado de remediación necesario para continuidad y revisión. Evitar dos versiones simultáneamente canónicas del mismo workflow.

## Postcondición esperada
Un trabajo de auditoría especializado mantiene trazabilidad desde criterio y evidencia hasta conclusión, explicita limitaciones, compone correctamente el dominio y no declara cierre sin postcondición verificable.