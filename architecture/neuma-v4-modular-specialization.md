# NEUMA v4 — Contrato de especialización modular

## Propósito
Definir el contrato operativo de especialización de NEUMA v4 sin convertir NEUMA Core en un repositorio enciclopédico ni generar forks metodológicos por dominio.

## Principio rector
NEUMA v4 se compone de **Core + Operations + módulos especializados**. Core conserva invariantes universales; Operations conserva gobierno y ejecución transversal; los módulos aportan conocimiento, restricciones, workflows y controles específicos.

## Ejes de especialización
- **Dominio**: salud, derecho, ciberseguridad, TIC, ciencia, arte, finanzas u otros campos disciplinares.
- **Capacidad / workflow / actividad**: licitaciones, ventas, marketing, proyectos, auditoría, investigación, due diligence u otros procesos.
- La composición dominio + workflow es válida cuando aporta valor; no se crean combinaciones precompuestas por defecto.

## Contrato mínimo de un módulo
Todo módulo deberá declarar, como mínimo:
1. Identidad estable, nombre y versión.
2. Tipo: dominio, workflow/capacidad o híbrido justificado.
3. Alcance positivo y exclusiones explícitas.
4. Dependencia mínima compatible de NEUMA Core / Operations.
5. Autoridades, fuentes o SoR permitidos y su precedencia.
6. Reglas de actualización/frescura cuando el conocimiento sea cambiante.
7. Riesgos materiales y controles adicionales.
8. Gates humanos específicos, si aplican.
9. Herramientas/conectores requeridos u opcionales.
10. Criterios de activación y desactivación.
11. Reglas de composición y conflictos con otros módulos.
12. Casos de conformidad y postcondiciones esperadas.
13. Política de compatibilidad, deprecación y migración.

## Reglas de composición
- El módulo **no puede redefinir** invariantes de Core.
- El módulo puede **endurecer** controles operativos por riesgo o regulación, pero no debilitarlos silenciosamente.
- Una instrucción específica del usuario puede parametrizar el trabajo, pero no convertir conocimiento no autorizado en SoR.
- Cuando dos módulos entren en conflicto, prevalece la regla más específica solo si no contradice Core, autoridad superior o restricciones de seguridad/compliance.
- Conflictos no resolubles por precedencia explícita se elevan como decisión material; no se arbitran por conveniencia.
- La activación debe ser mínima: cargar solo los módulos materialmente necesarios.

## Conocimiento y autoridad
- Los módulos no deben copiar grandes cuerpos de conocimiento por defecto.
- Deben resolver conocimiento desde autoridades/SoR apropiados, con trazabilidad proporcional.
- Versiones regulatorias, estándares o políticas cambiantes requieren verificación viva cuando sean materiales.
- El módulo no convierte una fuente en verdad universal; declara jurisdicción, vigencia, alcance y límites.

## Compatibilidad y versionado
- Core y Operations mantienen versionado independiente del catálogo de módulos.
- Un módulo declara rango de compatibilidad; no obliga a versionar NEUMA completo por cada cambio disciplinar.
- Cambios incompatibles en el contrato modular sí pueden justificar un major de NEUMA.
- La deprecación debe incluir reemplazo o ruta de migración cuando exista dependencia material.

## Conformance v4
La validación de un módulo debe probar al menos:
- no duplicación o fork de Core;
- resolución correcta de autoridad/SoR;
- activación mínima;
- comportamiento ante fuentes faltantes o contradictorias;
- conflicto entre módulos;
- Gate humano cuando corresponda;
- continuidad/recovery del estado material;
- postcondición verificable.

## Estrategia de pilotos
Antes de un catálogo amplio, validar el contrato con pocos módulos representativos. Criterio recomendado: un dominio de alta criticidad, un dominio técnico y un workflow transversal. La selección concreta se decide más adelante si afecta prioridades o riesgo.

## Estado
Contrato aprobado por ADR-007 y publicado en `main`. La conformidad conductual fue validada en E2 y la validación empírica representativa E3 fue publicada mediante PR #25. Esto no libera NEUMA v4 ni certifica los módulos piloto; la arquitectura permanece previa al Gate humano de declaración RC v4.
