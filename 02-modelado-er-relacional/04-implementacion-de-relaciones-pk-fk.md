# Relaciones entre Tablas: Primary y Foreign Keys

## El Concepto de Claves para Relacionar la Información

En el **Modelo Relacional**, las entidades (tablas) se relacionan lógicamente, no con rombos como en el Modelo E/R. Esta vinculación se logra mediante el uso estratégico de **claves** que garantizan la integridad de los datos.

### Claves Primarias (Primary Keys - PK)

La Clave Primaria es el pilar de la integridad de una tabla. Su función es identificar a cada registro de manera única.

* **Función:** Identificar de **manera única** a cada **fila (tupla)** o registro dentro de una tabla.
* **Restricción de Unicidad:** Un valor de clave primaria **no se puede repetir** dentro de la misma tabla.
* **Restricción de Nulidad:** Una clave primaria **no puede contener valores nulos (NULL)**. Siempre debe tener un valor asignado.
* **Definición:** Generalmente es un campo con un valor auto-incremental (como un ID numérico), un código único (como el ISBN de un libro), o una combinación de atributos (Clave Compuesta).

**Ejemplo:** En la tabla `clientes`, el campo `numero_de_cliente` es un buen candidato a **Primary Key**, ya que garantiza que cada fila corresponde a una persona diferente.

### Claves Foráneas (Foreign Keys - FK)

La Clave Foránea es el mecanismo que utilizamos para establecer las **relaciones** y mantener la **Integridad Referencial** entre tablas.

* **Función:** Es un campo de una tabla **"X"** (la tabla hija o referenciadora) que sirve para enlazar o relacionar a ese registro con un registro de otra tabla **"Y"** (la tabla padre o referenciada).
* **Vinculación:** Una clave foránea en una tabla **es la clave primaria en otra tabla**.
* **Propósito:** Almacenar la PK de la tabla padre para referenciarla, formalizando el vínculo que antes era una flecha en el Diagrama E/R.
* **Permite NULL:** A diferencia de la PK, una FK puede ser nula (NULL) si la participación en la relación es opcional.


## ¿Cómo relacionamos tablas? El Uso de las Claves

Las claves primarias y foráneas son el método estandarizado para implementar las relaciones de **Cardinalidad (1:1, 1:N)** que vimos en la sección anterior.

### Resolución de Relaciones 1:N (Uno a Muchos)

Esta es la forma más común de vincular tablas.

* **Regla de oro:** La **Clave Primaria (PK)** de la tabla del lado **"Uno"** se migra a la tabla del lado **"Muchos"** como una **Clave Foránea (FK)**.

| Tablas | Relación | Implementación |
| :--- | :--- | :--- |
| **Clientes (1)** y **Pedidos (N)** | Un cliente tiene muchos pedidos. | La PK de `clientes` (`id_cliente`) se convierte en la FK en la tabla `pedidos`. |
| **Departamento (1)** y **Empleados (N)** | Un departamento tiene muchos empleados. | La PK de `departamento` (`id_departamento`) se convierte en la FK en la tabla `empleados`. |

### Tip: Integridad Referencial

La integridad referencial es una regla de la base de datos que asegura que no se pueda hacer referencia a una fila que no existe.

* **Evita Errores:** Si la tabla `pedidos` tiene una FK que apunta a la tabla `clientes`, la base de datos no te permitirá insertar un pedido con un `id_cliente` que no existe en la tabla `clientes`. Esto **evita datos huérfanos**.
* **Acciones en Cascada (CASCADE):** Al definir la FK, se especifica qué debe hacer el SGBD si se borra o se actualiza la PK en la tabla padre (por ejemplo, borrar automáticamente todos los pedidos de un cliente si este es eliminado).
