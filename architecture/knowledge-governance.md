# Gobierno del conocimiento NEUMA

## Modelo federado

NEUMA evita una base monolítica de conocimiento. Cada objeto debe tener un **System of Record (SoR)** inequívoco y los demás sistemas deben conservar referencias o proyecciones mínimas cuando sea suficiente.

| Tipo de objeto | SoR recomendado |
|---|---|
| Principios, ADR, arquitectura, metodología, skills y especificaciones versionables | GitHub / Neuma-Core |
| Evidencias y documentos fuente | Repositorio documental de origen (por ejemplo Drive o SharePoint) |
| Proyectos, riesgos, tareas, gates y seguimiento operativo | Notion |
| Correo y eventos | Proveedor original de correo/calendario |

## Reglas

1. No duplicar contenido completo si una referencia verificable satisface la necesidad.
2. Definir una clave estable para toda proyección entre sistemas.
3. Ante divergencia, prevalece el SoR; no sobrescribir el canónico para acomodar una copia derivada.
4. Toda escritura cross-system debe poder reconstruirse mediante origen, destino, transformación, estado y verificación.
5. La clasificación de sensibilidad debe preceder a cualquier movimiento de información entre sistemas.
6. Los originales y evidencias críticas no deben depender de Notion ni GitHub como único repositorio.
7. Los cambios materiales en artefactos versionables deben utilizar rama/PR y revisión proporcional al riesgo.

## Clasificación mínima de sensibilidad

- **Pública:** apta para publicación deliberada.
- **Interna:** uso de trabajo; no destinada a publicación abierta.
- **Confidencial:** acceso limitado por necesidad y autorización.
- **Restringida:** datos cuya exposición o modificación puede producir daño material, incumplimiento o riesgo elevado.

Un repositorio público como `Neuma-Core` debe contener únicamente material cuya publicación sea deliberada y apropiada.

## Proyecciones

El patrón preferido es:

`SoR → clave determinista → resolución → create/update/no-op/conflict → verificación → trazabilidad → compensación`

La sincronización bidireccional automática no es el patrón por defecto.
