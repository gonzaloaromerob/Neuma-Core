# NEUMA v4 — Piloto de dominio: Derecho

## Estado
Especificación piloto `v0.1-pilot`. No es una skill publicada, no constituye asesoría jurídica y no declara conformidad hasta ejecutar la suite v4.

## Identidad
- **ID:** `neuma-domain-law`
- **Tipo:** dominio
- **Versión piloto:** `v0.1-pilot`
- **Compatibilidad objetivo:** arquitectura modular NEUMA v4 + NEUMA Operations v3.7 como baseline transversal mientras se valida la evolución de Operations.

## Propósito
Aportar controles de razonamiento y resolución de autoridad para tareas jurídicas sin convertir NEUMA Core en repositorio de derecho ni sustituir criterio profesional, representación legal o autoridad normativa.

## Alcance
- identificar jurisdicción, materia y fecha relevantes;
- distinguir norma, jurisprudencia, doctrina, política interna, contrato y hechos del caso;
- resolver fuentes jurídicas desde autoridades apropiadas;
- exigir vigencia y trazabilidad proporcionales al impacto;
- separar información general, análisis e hipótesis;
- elevar decisiones que exijan criterio profesional, aceptación de riesgo o actuación legal material.

## Exclusiones
- no almacenar corpus jurídicos como verdad embebida;
- no asumir jurisdicción por residencia, idioma o contexto si cambia materialmente la respuesta;
- no representar al usuario ni presentar escritos, radicaciones o decisiones como actuación profesional autorizada sin Gate explícito;
- no sustituir SoR contractuales, expedientes, políticas internas ni fuentes oficiales vigentes.

## Autoridad y SoR
Orden general, sujeto a la materia y jurisdicción explícitas:
1. texto oficial vigente de constitución, ley, decreto, regulación o acto aplicable;
2. decisiones judiciales/administrativas oficiales cuando tengan efecto material;
3. expediente, contrato, política o documento gobernado que sea SoR del caso concreto;
4. fuentes secundarias reputadas para interpretación y contexto;
5. conocimiento general del modelo solo como apoyo no autoritativo.

Si la jerarquía jurídica real exige otro orden, debe resolverse según jurisdicción y materia; este listado no reemplaza reglas de fuentes del derecho.

## Frescura
Verificar vigencia cuando el resultado dependa de norma, regulación, jurisprudencia, plazo, tarifa, autoridad competente, procedimiento o política que pueda haber cambiado. Registrar fecha de consulta cuando sea material.

## Riesgos y controles adicionales
- **Jurisdicción ambigua:** declarar el vacío y resolverla antes de una conclusión material.
- **Fuente derogada o modificada:** no tratarla como vigente.
- **Hechos incompletos:** separar hechos confirmados de supuestos.
- **Consecuencia jurídica material:** aumentar verificación y trazabilidad.
- **Conflicto normativo o interpretativo no resoluble:** escalar a criterio humano/profesional.

## Gates humanos específicos
Requerir Gate explícito cuando corresponda para:
- presentar, radicar, firmar o enviar un documento con efectos jurídicos;
- aceptar o renunciar derechos, obligaciones, términos o posiciones materiales;
- elegir una estrategia litigiosa/regulatoria con consecuencias difíciles de revertir;
- actuar frente a autoridad, contraparte o tercero en nombre del usuario;
- asumir una interpretación controvertida cuando el riesgo material no puede reducirse con evidencia.

## Dependencias y conectores
No exige un proveedor específico. Puede usar web, repositorios jurídicos oficiales, gestores documentales o conectores empresariales cuando estén disponibles, autorizados y sean apropiados. `Expuesto != conectado != autorizado != validado`.

## Activación
Activar cuando una tarea dependa materialmente de normas, contratos, obligaciones, derechos, procedimientos, autoridades o interpretación jurídica.

## Desactivación
No activar para redacción general, negociación puramente comercial o tareas administrativas sin cuestión jurídica material, salvo que otro módulo detecte un riesgo jurídico que cambie la decisión.

## Composición
- Con `neuma-workflow-audit`: Derecho gobierna autoridad jurídica; Auditoría gobierna evidencia, alcance, hallazgos y trazabilidad del encargo.
- Con dominios técnicos: el dominio técnico gobierna hechos/especificaciones técnicas; Derecho gobierna consecuencias y autoridad jurídica.
- Ninguna composición puede debilitar Core, Operations, seguridad o cumplimiento superior.

## Conflictos
Aplicar autoridad superior y regla jurídica válida antes que conveniencia del workflow. Si persiste una interpretación materialmente controvertida sin precedencia suficiente, elevar Gate humano mínimo y conservar trabajo reversible.

## Conformance
Debe pasar M01–M15 de `docs/neuma-v4-module-conformance-suite.md` y la baseline Core/Operations aplicable. Casos especialmente críticos: M03, M04, M07, M08, M09, M10, M11, M12 y M13.

## Deprecación y migración
Una versión reemplazada no puede seguir presentándose como canónica. La migración debe preservar referencias de autoridad, Gates abiertos, decisiones y evidencia necesaria para continuidad o revisión.

## Postcondición esperada
Una tarea jurídica especializada conserva los invariantes NEUMA, identifica autoridad y jurisdicción, no inventa vigencia ni certeza, y mantiene la responsabilidad humana sobre decisiones jurídicas materiales.