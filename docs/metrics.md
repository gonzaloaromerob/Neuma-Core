# Métricas de madurez NEUMA Operations

NEUMA Operations no se evalúa principalmente por cantidad de conectores o endpoints disponibles.

## Métricas prioritarias
- **Tasa de verificación:** proporción de escrituras materiales con postcondición comprobada.
- **Errores de destino:** operaciones ejecutadas sobre objeto, rama, cuenta o repositorio incorrectos.
- **Duplicación:** objetos derivados duplicados frente a ejecuciones idempotentes.
- **Divergencias detectadas:** discrepancias entre System of Record y proyecciones identificadas antes de producir daño.
- **Recuperabilidad:** proporción de fallos con rollback o compensación definida y ejecutable.
- **Escalamientos correctos:** Gates C activados cuando aparece una consecuencia material nueva.
- **Falsos escalalamientos:** confirmaciones innecesarias que podrían haberse resuelto como A/B.
- **Exposición de información:** movimientos o publicaciones que contradigan clasificación de sensibilidad; objetivo: cero.
- **Trabajo evitado:** iteraciones manuales o pasos redundantes eliminados sin degradar control.

## Criterio
La automatización mejora cuando reduce fricción y errores manteniendo o aumentando agencia, trazabilidad y capacidad de recuperación.
