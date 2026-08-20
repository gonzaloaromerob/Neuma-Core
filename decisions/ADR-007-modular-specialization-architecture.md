# ADR-007 — Arquitectura de especialización modular NEUMA

## Estado
Validada por decisión humana. Publicación en `main` pendiente del Gate C de merge del PR correspondiente.

## Contexto
NEUMA debe permanecer como marco transversal y portable, sin convertirse en un repositorio enciclopédico ni en el contenedor universal de conocimiento disciplinar. La especialización por áreas como salud, derecho, ciberseguridad, TIC, ciencia o arte, y por actividades como licitaciones, ventas, marketing, proyectos, auditoría o investigación, es útil; sin embargo, implementarla como ramas jerárquicas que heredan y duplican Core produciría forks metodológicos, divergencia, mantenimiento costoso y ambigüedad de autoridad.

La evolución hacia NEUMA v4 requiere una arquitectura que permita especialización real sin contaminar los invariantes de Core ni obligar a versionar todo NEUMA cada vez que cambie una disciplina, regulación o workflow.

## Decisión
Adoptar una arquitectura de **composición modular** con los siguientes principios:

1. **Core deliberadamente pequeño.** NEUMA Core conserva únicamente invariantes cognitivos universales y no incorpora conocimiento disciplinar como verdad general.
2. **Operations transversal.** NEUMA Operations mantiene gobierno, ejecución, control A/B/C, SoR, proyecciones, resiliencia, verificación y postcondición operacional; no se especializa por disciplina mediante forks.
3. **Dos ejes de especialización.** Los módulos se clasifican principalmente como:
   - **dominio**: salud, derecho, ciberseguridad, TIC, ciencia, arte, finanzas u otros campos;
   - **capacidad/workflow**: licitaciones, ventas, marketing, proyectos, auditoría, investigación, due diligence u otros procesos.
4. **Composición, no combinaciones preconstruidas.** Un trabajo puede activar dominio + workflow cuando sea materialmente útil, sin crear por defecto artefactos combinatorios como `neuma-derecho-licitaciones-sector-publico-*`.
5. **No forks de Core.** Un módulo no redefine ni debilita invariantes de NEUMA Core. Puede endurecer controles por riesgo, regulación o contexto.
6. **Conocimiento gobernado fuera de Core.** El conocimiento especializado debe resolverse desde autoridades, fuentes y SoR apropiados, con jurisdicción, vigencia, alcance y trazabilidad proporcionales. No se copian grandes cuerpos de conocimiento dentro de NEUMA por defecto.
7. **Contrato mínimo de módulo.** Cada módulo declara identidad/versionado, tipo, alcance y exclusiones, compatibilidad, autoridades/SoR, frescura, riesgos, Gates humanos, herramientas/conectores, activación, composición/conflictos, conformance, deprecación y migración.
8. **Activación mínima.** Cargar solo módulos materialmente necesarios para reducir acoplamiento, contexto y riesgo.
9. **Conflictos explícitos.** Cuando dos módulos entren en conflicto, se aplican reglas de precedencia declaradas. Si el conflicto no es resoluble sin criterio humano material, se eleva como Gate; no se arbitra por conveniencia.
10. **Versionado desacoplado.** Core, Operations y módulos pueden evolucionar con ciclos distintos. Solo un cambio incompatible en el contrato modular o en invariantes transversales justifica por sí mismo un cambio mayor de NEUMA.

## Implicaciones para NEUMA v4
- v4 debe formalizar un contrato portable de módulos y composición.
- La conformidad debe probar no duplicación/fork de Core, resolución correcta de autoridad, activación mínima, conflictos, Gates humanos, continuidad y postcondiciones.
- Antes de un catálogo amplio deben existir pocos pilotos representativos.
- El catálogo de módulos no constituye por sí mismo NEUMA Core.

## Límites
- Esta ADR no aprueba módulos concretos ni su contenido disciplinar.
- No crea una taxonomía cerrada de dominios o workflows.
- No autoriza a una skill especializada a sustituir autoridad profesional, regulación, SoR o criterio humano material.
- No impone un proveedor, runtime ni formato único de empaquetado.

## Postcondición esperada
NEUMA puede incorporar especialización creciente sin convertirse en un monolito de conocimiento, sin multiplicar forks del Core y sin perder trazabilidad de autoridad, compatibilidad, riesgo o responsabilidad humana.
