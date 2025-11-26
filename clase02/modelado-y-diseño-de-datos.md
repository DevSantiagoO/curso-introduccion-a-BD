# Clase 02: Modelado y Diseño de Datos

## La Fase Conceptual: Abstracción y Modelado

Antes de escribir cualquier sentencia de SQL, el paso fundamental es la **Fase Conceptual**, donde se define qué información se va a almacenar.

### Abstracción de Datos

La **abstracción de datos** es el proceso intelectual de simplificación que significa lograr una **representación lógica** de las situaciones y objetos del mundo real.

* **Objetivo:** Enfocarse en la **esencia** de la información crucial, descartando detalles irrelevantes para el sistema.
* **Proceso:** Transforma objetos concretos (una persona, un producto) en un esquema lógico que la base de datos pueda entender.

### Modelo de Datos

Un **modelo de datos** es el conjunto de herramientas y conceptos que proporciona los medios necesarios para conseguir esa abstracción y describir la estructura de la base de datos. Es el "plano" o la arquitectura.

* **El Modelo E/R:** El **Modelo Entidad-Relación (E/R)** es la herramienta gráfica más utilizada para la fase conceptual en bases de datos relacionales.

## Componentes del Modelo Entidad-Relación (E/R)

El Modelo E/R describe la estructura de la información mediante la identificación y vinculación de tres elementos básicos.

### Entidades (Tablas)

Una **Entidad** representa cualquier objeto, concepto, real o abstracto, del cual necesitamos almacenar información. Es el elemento principal del diseño.

* **Transformación:** Una entidad se convierte en una **Tabla** en la base de datos (e.j., `CLIENTES`, `PRODUCTOS`).
* **Tipos de Entidades:**
    * **Fuertes:** Existen por sí mismas y tienen una clave primaria propia (e.g., un `AUTOR`).
    * **Débiles:** Su existencia depende de una Entidad Fuerte (e.j., un `DETALLE_FACTURA` depende de la `FACTURA` principal).

**Ejemplo:** En un sistema de ventas, `CLIENTE`, `PRODUCTO` y `PEDIDO` son entidades fundamentales.

### Atributos (Columnas/Campos)

Un **Atributo** es una característica o propiedad que describe a una entidad. Son los detalles que queremos guardar sobre cada instancia de la entidad.

* **Transformación:** Un atributo se convierte en una **Columna** o **Campo** en la tabla.
* **Atributo Clave (Primary Key):** Atributo o conjunto de atributos que **identifica de forma única** a cada instancia de una entidad (e.j., `DNI` para una persona o `ISBN` para un libro).
* **Ejemplos de Clasificación:**
    * **Compuesto:** Como `Dirección` (compuesto por `Calle` y `Ciudad`).
    * **Derivado:** Como `Edad` (calculada a partir de `FechaNacimiento`).

 **Ejemplo:** Para la Entidad `PRODUCTOS`, los atributos serían `nombre`, `precio`, `stock`, `ID_Proveedor`.

### Relaciones (Vínculos)

Una **Relación** es la asociación o conexión lógica y significativa que existe entre dos o más entidades.

* **Cardinalidad:** Define cuántas instancias de una entidad pueden estar asociadas con cuántas instancias de otra.

| Cardinalidad | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **Uno a Uno (1:1)** | Una instancia de A se relaciona con una de B, y viceversa. | Un `EMPLEADO` **dirige** un `DEPARTAMENTO`. |
| **Uno a Muchos (1:N)** | Una instancia de A se relaciona con muchas de B, pero B solo con una de A. (La más común) | Un `PROFESOR` **imparte** muchas `CLASES`. |
| **Muchos a Muchos (N:M)** | Muchas instancias de A se relacionan con muchas de B, y viceversa. (Requiere una **tabla intermedia**) | Un `ALUMNO` **se inscribe** en muchas `MATERIAS`. |

