# NEUMA 4.0 — Release canónica

## Estado

**NEUMA 4.0 queda publicada como release canónica del marco NEUMA con fecha 2026-08-20**, conforme al Gate humano explícitamente autorizado después de completar el Release Candidate y verificar sus postcondiciones.

Esta identidad versiona el **marco NEUMA integral**. No sincroniza por nombre las versiones de sus componentes y no implica despliegue o adopción automática en PROD.

## Identidad de release

- Marco: **NEUMA 4.0**.
- NEUMA Operations: **v3.8**, release interna estable y control plane transversal vigente.
- `neuma-domain-law`: **v0.2-pilot**.
- `neuma-domain-cybersecurity`: **v0.2-pilot**.
- `neuma-workflow-audit`: **v0.2-pilot**.
- Baseline RC publicada mediante PR #27 / merge SHA `b0585e2e030e8cd65163686409ce6f47e598729b`.
- Postcondiciones RC verificadas mediante Issue #28, cerrado como completado.

## Qué define NEUMA 4.0

NEUMA 4.0 consolida una arquitectura en la que:

1. **NEUMA Core permanece pequeño y universal**, sin convertirse en un repositorio enciclopédico de dominios;
2. **NEUMA Operations gobierna transversalmente** verdad → claridad → decisión → acción, con verificación proporcional y postcondición cuando corresponda;
3. la especialización se resuelve mediante **módulos desacoplados por dominio y workflow/capacidad**;
4. la activación es **mínima y material**, distinguiendo declarado/instalado, resoluble, compatible y activo;
5. autoridad, Systems of Record y frescura se resuelven explícitamente cuando son materiales;
6. la composición admite hardening pero no debilitamiento silencioso de controles;
7. conflictos materiales no resolubles, autoridad humana o efectos irreversibles se elevan mediante Gates explícitos;
8. continuidad y recovery preservan estado material sin depender de la conversación como único contenedor;
9. migración, rollback, compatibilidad y conformance se gobiernan como contratos verificables;
10. la evolución se produce ante evidencia material, no por expansión o refinamiento inercial.

## Evidencia de liberación

La publicación de NEUMA 4.0 se sustenta en la secuencia gobernada documentada en `Neuma-Core`:

- ADR-007 y contrato de especialización modular publicados;
- suite de conformance M01–M15 / F01–F15;
- E2 integral: Core 20/20, modular 28/30 y cero fallos críticos;
- E3 de falsación: M02/F02 y M13/F13 elevados a Pass empírico, con casos representativos de composición, conflictos, fuentes, Gates y postcondición;
- preparación pre-RC mediante PR #26: bundle, migración y rollback;
- declaración RC mediante PR #27;
- verificación post-RC mediante Issue #28, sin bloqueadores materiales nuevos para el alcance de la release.

No surgió evidencia material que justificara modificar Core, forzar NEUMA Operations a v4.0 o promover los módulos piloto antes de esta release.

## Compatibilidad y migración

NEUMA 4.0 adopta la ruta descrita en `docs/neuma-v4-migration-v3-to-v4.md`:

- la transición desde la familia v3.x es aditiva y reversible para la baseline evaluada;
- NEUMA Operations v3.8 conserva identidad y lifecycle propios;
- los módulos piloto conservan `v0.2-pilot`;
- las combinaciones evaluadas con Operations v3.8 son compatibles por regla gobernada backward-compatible documentada en E2/E3;
- futuras combinaciones no evaluadas permanecen `unknown` hasta evidencia gobernada.

## Alcance del release

NEUMA 4.0 publica como estado estable del **marco** la arquitectura modular, su modelo de gobierno, conformance, evidencia, migración y rollback que integran el bundle validado.

Los módulos piloto se incluyen únicamente como evidencia y componentes experimentales compatibles con el marco evaluado. **No quedan certificados, promovidos a stable ni convertidos en dependencias universales.**

## Licenciamiento, marca y titularidad

Esta release no modifica la arquitectura de derechos vigente del repositorio:

- el archivo raíz `LICENSE` delimita alcance y estado de licenciamiento;
- `LICENSES/MIT.txt` aplica únicamente a software o código expresamente identificado como cubierto por MIT;
- la documentación metodológica no adquiere una licencia Creative Commons por la publicación de NEUMA 4.0;
- marca, signos distintivos, derecho de autor, titularidad/procedencia, política de marca y legado patrimonial permanecen bajo sus Gates separados.

La release no debe interpretarse como cesión implícita de derechos, licencia general sobre la metodología ni cierre de los Gates jurídicos pendientes.

## Rollback y estabilidad

La evidencia y procedimiento de rollback del candidato permanecen en `docs/neuma-v4-rc-rollback.md` como referencia histórica y de recuperación del proceso de liberación.

Tras esta publicación:

- los cambios incompatibles del marco requieren nueva decisión/versionado proporcional;
- las correcciones compatibles pueden evolucionar sin sincronizar artificialmente versiones entre Core, Operations y módulos;
- un hallazgo crítico posterior debe registrarse, evaluar impacto en la release y activar remediación/rollback proporcional cuando corresponda;
- E1/E2/E3, RC y sus artefactos se preservan como evidencia histórica y no se reescriben para simular continuidad perfecta.

## Exclusiones y Gate siguiente

La publicación de NEUMA 4.0 **no**:

- despliega ni modifica `www.neuma.com.co`;
- cambia `Neuma-Web` ni su CI/CD;
- autoriza adopción automática en entornos productivos;
- promueve módulos piloto;
- concede nuevas licencias;
- resuelve los Gates jurídicos pendientes.

El siguiente Gate humano material es cualquier **adopción, comunicación o despliegue PROD con efecto externo material**. Hasta ese Gate, la release metodológica/documental queda publicada y trazable en `Neuma-Core`.
