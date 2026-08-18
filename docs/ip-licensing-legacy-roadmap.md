# Propiedad intelectual, licenciamiento y legado — hoja de ruta

> Documento de planeación. No constituye asesoría jurídica ni declara derechos ya registrados.

## Decisión de arquitectura jurídica
NEUMA debe separar cuatro capas que protegen o gobiernan objetos distintos:

1. **Derecho de autor / registro probatorio:** expresiones concretas del marco (textos, manuales, diagramas, materiales pedagógicos y, cuando corresponda, software).
2. **Marca NEUMA:** signo distintivo, identidad comercial y reglas de uso de marca.
3. **Licenciamiento abierto:** permisos de reutilización del contenido publicable.
4. **Gobierno del legado:** procedencia, versiones, atribución, continuidad, sucesión y evolución del marco.

Ninguna de estas capas sustituye a las demás.

## 1. Inventario y cadena de procedencia
Antes de una release pública estable:
- identificar documentos rectores y versiones;
- conservar originales, fechas e historial de cambios;
- documentar contribuciones humanas y asistencia de IA cuando sea material para autoría/procedencia;
- separar contenido propio de citas, imágenes, marcas, plantillas y materiales de terceros;
- mantener un registro de decisiones metodológicas.

## 2. Derecho de autor en Colombia
La Dirección Nacional de Derecho de Autor (DNDA) administra el Registro Nacional de Derecho de Autor. El registro es gratuito y cumple una función probatoria/publicitaria; la protección autoral no debe confundirse con la protección de una idea o metodología abstracta.

### Paquete candidato a registro
Una vez estabilizado y revisado jurídicamente, preparar como mínimo:
- Manual de Gobierno NEUMA 3.0 aprobado;
- Anexos Operativos / Constitución y Arquitectura Operativa en versión aprobada;
- documento público principal o manual pedagógico, si constituye una obra diferenciada;
- diagramas o materiales originales relevantes cuando ameriten tratamiento separado.

### Asistencia de IA
No asumir automáticamente que todo contenido asistido por IA tiene idéntico tratamiento autoral. Conservar evidencia del aporte humano: concepción, selección, estructura, instrucciones, revisión, edición, decisiones y versión final. La determinación jurídica debe hacerse sobre cada obra y con normativa/doctrina vigente al momento del registro.

## 3. Marca NEUMA — SIC
La Superintendencia de Industria y Comercio (SIC) administra el registro de marcas en Colombia. Antes de presentar una solicitud:
- realizar búsqueda de antecedentes fonéticos y figurativos en SIPI;
- definir titularidad;
- identificar productos/servicios y clases de Niza pertinentes;
- decidir si se solicita marca nominativa, mixta y/o signos adicionales;
- evaluar territorios adicionales si la estrategia supera Colombia.

### Regla de prudencia
Una búsqueda web ordinaria no sustituye la búsqueda de antecedentes en SIPI ni un análisis de confundibilidad. No declarar disponibilidad de `NEUMA` hasta completar ese estudio.

## 4. Creative Commons — recomendación provisional
Para **documentación pública metodológica**, la opción base recomendada para evaluación jurídica es **CC BY-SA 4.0**:
- exige atribución;
- permite adaptación y uso comercial;
- exige compartir adaptaciones bajo la misma licencia;
- favorece difusión y continuidad abierta sin cerrar el ecosistema derivado.

### Por qué no aplicar todavía la licencia
Creative Commons advierte que sus licencias no son revocables respecto de copias ya licenciadas. Por ello, no debe añadirse CC BY-SA 4.0 al repositorio hasta completar:
- titularidad y procedencia;
- separación de terceros;
- política de marca;
- definición del corpus exacto que será público.

### Alternativas
- **CC BY 4.0:** mayor libertad y adopción; menor control sobre licenciamiento de derivados.
- **CC BY-NC-SA 4.0:** reserva explotación comercial, pero puede limitar adopción legítima y genera ambigüedad práctica sobre usos comerciales.
- **CC BY-ND 4.0:** no recomendada como línea base para un marco vivo porque restringe adaptaciones.

### Software y marca
- Software: usar una licencia de software separada (el repositorio actualmente contiene MIT; su alcance debe aclararse antes de publicar documentación bajo CC).
- Marca: Creative Commons no concede derechos sobre `NEUMA` como marca. Debe existir una política de marca independiente.

## 5. Problema actual a resolver antes de licenciar
`Neuma-Core` contiene actualmente un `LICENSE` MIT que habla de “Software and associated documentation”. Antes de una release metodológica pública debe evitarse ambigüedad sobre si MIT cubre toda la documentación del marco.

**Recomendación:** en un PR posterior a la revisión jurídica, mantener MIT exclusivamente para código/software identificable y declarar explícitamente la licencia aplicable a documentación metodológica. No cambiar la licencia existente de `main` de forma unilateral mientras no esté resuelto el alcance y la titularidad.

## 6. Separación público / interno
Mantener dos capas:
- **Corpus interno rector (SharePoint):** originales, estrategia, borradores, trazabilidad, documentación completa y material reservado.
- **Distribución pública (GitHub / publicaciones):** contenido deliberadamente revisado, con licencia, atribución, avisos y exclusiones claras.

La versión pública no sustituye automáticamente el corpus interno.

## 7. Paquete de publicación estable
Antes de etiquetar una versión pública estable:
- versión y fecha de corte;
- documento principal;
- mapa del corpus y jerarquía de fuentes;
- historial de cambios;
- licencia(s) por tipo de activo;
- `NOTICE` y atribuciones de terceros;
- política de marca;
- cita recomendada;
- declaración de autoría/titularidad validada;
- declaración prudente sobre asistencia de IA;
- archivo de procedencia;
- identificador persistente/depósito cuando aporte valor.

## 8. Legado y continuidad
La estrategia de legado debe definir separadamente:
- quién puede mantener versiones futuras;
- cómo se conserva la versión canónica de cada release;
- qué cambios requieren gobernanza reforzada;
- cómo se protege la marca frente a usos que sugieran aval oficial;
- cómo se preserva atribución a sus autores/fundadores;
- qué sucede con derechos, administración y continuidad ante incapacidad, retiro o sucesión;
- cómo se documentan forks o implementaciones derivadas sin confundirlas con la versión oficial.

## 9. Gate jurídico previo
Antes de ejecutar acciones irreversibles o externas —licenciar públicamente, presentar registro marcario, registrar una obra final o publicar el Manual completo— realizar revisión jurídica específica y actualizada sobre:
- derecho de autor y Registro Nacional de Derecho de Autor (DNDA);
- marcas y clasificación ante SIC;
- titularidad y contribuciones de terceros;
- tratamiento de contenidos asistidos por IA;
- Creative Commons;
- alcance del MIT existente;
- estrategia sucesoral/patrimonial del activo intelectual.

## Resultado esperado
El objetivo no es “cerrar” NEUMA jurídicamente, sino permitir que sea **identificable, atribuible, preservable, licenciable y evolutivo**, sin confundir apertura con pérdida de gobierno.
