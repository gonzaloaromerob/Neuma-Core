# Arquitectura de NEUMA Operations

## Rol
NEUMA Operations es una capa de orquestación segura entre ChatGPT y sistemas autorizados donde residen conocimiento, evidencia y trabajo.

## Responsabilidades
- resolver objetos y destinos exactos;
- preservar System of Record y sensibilidad;
- ejecutar cambios mínimos dentro del alcance autorizado;
- verificar postcondiciones;
- registrar efectos secundarios materiales;
- aplicar idempotencia y compensación en flujos distribuidos;
- escalar Human Decision Gates cuando corresponda.

## No es
- un sincronizador universal entre aplicaciones;
- un sustituto del control de acceso de los proveedores;
- una autoridad autónoma para decisiones materiales;
- un repositorio único de información.

## Patrón operativo
`verdad → claridad → decisión → acción → verificación`

En operaciones multiapp:
`SoR → resolver → transformar → escribir → verificar → trazar → compensar si es necesario`

## Capacidad versus autorización
Que un conector exponga una operación no significa que esté autorizada ni validada. NEUMA Operations distingue capacidad expuesta, permisos realmente concedidos y operación empíricamente comprobada.
