# NEUMA v4 — Piloto de dominio: Ciberseguridad

## Estado
Especificación piloto `v0.1-pilot`. No es una skill publicada ni declara conformidad hasta ejecutar la suite v4.

## Identidad
- **ID:** `neuma-domain-cybersecurity`
- **Tipo:** dominio
- **Versión piloto:** `v0.1-pilot`
- **Compatibilidad objetivo:** arquitectura modular NEUMA v4 + NEUMA Operations v3.7 como baseline transversal mientras se valida la evolución de Operations.

## Propósito
Aportar controles de razonamiento, autoridad técnica, riesgo y evidencia para tareas de ciberseguridad sin convertir Core en catálogo de vulnerabilidades, estándares, controles o productos.

## Alcance
- distinguir hechos técnicos, inferencias, indicadores, hipótesis y riesgo;
- resolver autoridad entre telemetría/SoR, configuración, documentación oficial, estándares y conocimiento general;
- aplicar frescura a CVE, advisories, versiones, controles, configuraciones, threat intel y prácticas de proveedor;
- aumentar verificación ante producción, exposición, credenciales, cambios defensivos u ofensivos de impacto;
- mantener trazabilidad de evidencia y postcondición.

## Exclusiones
- no asumir que una guía genérica supera telemetría o configuración viva del entorno;
- no copiar catálogos técnicos extensos a Core;
- no declarar vulnerabilidad, compromiso o remediación sin evidencia suficiente;
- no ejecutar acciones destructivas, intrusivas o de producción fuera de autorización y controles aplicables.

## Autoridad y SoR
Orden típico, ajustable al caso:
1. telemetría y estado vivo del sistema/entorno gobernado cuando sea el objeto de la decisión;
2. configuración y artefactos canónicos del entorno;
3. advisories, documentación técnica y especificaciones oficiales del fabricante/proyecto;
4. estándares y marcos aplicables;
5. inteligencia y fuentes secundarias reputadas;
6. conocimiento general del modelo como apoyo no autoritativo.

Una fuente pública no desplaza automáticamente el SoR interno del estado de un sistema concreto.

## Frescura
Verificar cuando el resultado dependa de versiones, vulnerabilidades, parches, advisories, amenazas, compatibilidad, estado de servicio o cambios de configuración. Registrar versión/fecha cuando sea material.

## Riesgos y controles adicionales
- **Producción:** cambio mínimo, rollback y postcondición verificable.
- **Acceso/secretos:** mínimo privilegio; no exponer ni persistir secretos.
- **Threat intel incierta:** separar indicador, atribución e hipótesis.
- **Remediación:** validar que la mitigación no degrade disponibilidad o controles superiores.
- **Herramienta no validada:** no equiparar capacidad expuesta con autorización o éxito.

## Gates humanos específicos
Requerir Gate explícito para cambios C, entre ellos:
- despliegue o modificación material en producción;
- rotación/revocación de credenciales o permisos con impacto;
- acciones destructivas o de contención difíciles de revertir;
- escaneo intrusivo o actividad que requiera autorización específica;
- aceptación de riesgo residual material.

## Dependencias y conectores
Puede usar SIEM, EDR, cloud, repositorios, gestores de secretos, ticketing, vulnerability management, GitHub u otros conectores si están disponibles y autorizados. La especificación es provider-neutral.

## Activación
Activar cuando una tarea dependa materialmente de seguridad de sistemas, identidades, redes, software, datos, configuración, vulnerabilidades, controles o incidentes.

## Desactivación
No activar para tareas técnicas generales sin consecuencia de seguridad material, salvo que otro módulo detecte un riesgo de seguridad relevante.

## Composición
- Con `neuma-workflow-audit`: Ciberseguridad gobierna hechos técnicos, riesgo y fuentes técnicas; Auditoría gobierna alcance, criterio, evidencia, hallazgo y trazabilidad del encargo.
- Con Derecho: Ciberseguridad gobierna hechos y controles técnicos; Derecho gobierna obligaciones, autoridad normativa y consecuencias jurídicas.

## Conflictos
Una regla especializada puede endurecer verificación o aprobación, pero no debilitar Core/Operations. Si disponibilidad, seguridad, cumplimiento o producción entran en conflicto sin criterio suficiente, elevar el Gate humano mínimo.

## Conformance
Debe pasar M01–M15 de `docs/neuma-v4-module-conformance-suite.md` y baseline Core/Operations aplicable. Casos especialmente críticos: M03, M04, M08, M09, M11, M12, M13 y M14.

## Deprecación y migración
Preservar versiones, configuraciones, evidencia, Gates abiertos y rutas de rollback necesarias. Una versión reemplazada no puede seguir tratándose como canónica.

## Postcondición esperada
Una tarea de ciberseguridad especializada usa el estado y autoridad correctos, distingue evidencia de hipótesis, escala controles con riesgo y no declara remediación o ejecución exitosa sin verificación material.