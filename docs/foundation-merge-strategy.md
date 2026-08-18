# Estrategia de merge de Foundation

Si el Gate C es aprobado:

- usar **squash merge** para convertir la historia de preparación en un único commit canónico;
- utilizar el SHA actual de la rama como precondición para evitar fusionar cambios no revisados;
- no habilitar auto-merge;
- verificar inmediatamente `main` y checks posteriores;
- mantener la rama como evidencia temporal hasta que exista una operación segura de limpieza de refs.

El squash conserva el contenido y reduce ruido histórico sin ocultar el PR que documenta la preparación.
