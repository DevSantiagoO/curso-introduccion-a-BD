# Transición de Modelos: Del Diseño Conceptual a la Implementación Lógica

La diferencia entre el Modelo E/R y el Modelo Relacional no es solo gráfica, sino **estructural**. La clave está en cómo se resuelven las relaciones y cómo el mundo real se "aplana" en tablas, un proceso conocido como **Mapeo Relacional**.

### Modelo Entidad-Relación (E/R): La Perspectiva Conceptual

El Modelo E/R es la forma en que pensamos. Permite una vista rica y flexible de la información, enfocada en la **semántica** (el significado) y las **reglas de negocio**.

* **Definición:** Es el modelo de **alto nivel** y **conceptual** que utiliza **Entidades**, **Atributos** y **Relaciones** para plasmar la realidad.
* **Flexibilidad Semántica:** Permite atributos complejos (compuestos, multivaluados) y relaciones complejas (ternarias, recursivas).
* **Representación:** Un **Diagrama E/R** 

![alt text](ej-E-R.png)

Muestra las conexiones lógicas, pero no representa cómo se guardarán físicamente los datos. 
* Cada rectángulo representa las ENTIDADES.
* Cada óvalo representa los ATRIBUTOS.
* Después tenemos relaciones o cardinalidades que son las formas en la que cierta entidad se puede relacionar con otra.

**Ejemplo de Pensamiento Conceptual:** Decimos: "Un **Empleado** tiene **varios Teléfonos** (atributo multivaluado) y está **Supervisado** por otro **Empleado** (relación recursiva)". Esta complejidad se resuelve *después* en el modelo lógico.

**Ejemplo**
![alt text](ej-E-R-basico.png)

**La linea que une ambas entidades sin utilizar ningún simbolo en sus extremidades representa la relación 1 a 1.**

![alt text](image.png)

> **Web para hacer Diagramas de Entidad - Relación: https://app.diagrams.net/**

### Modelo Relacional: La Perspectiva Lógica y Estructural

El Modelo Relacional es la forma en que el computador almacena los datos. Es un modelo de **bajo nivel** (lógico), estandarizado, que se basa rigurosamente en la teoría matemática de **relaciones**.

* **Definición:** Es el modelo **tabular** y **lógico** que organiza toda la información en **tablas bidimensionales** (Relaciones).
* **Unidad Fundamental:** La tabla. Cada tabla es una colección de filas (tuplas) y columnas (atributos).
* **Restricciones de Integridad:** La fuerza del modelo relacional radica en las restricciones que impone a la estructura y a los datos:
    * **Integridad de Entidad (Clave Primaria):** Cada tupla debe ser única (`Primary Key`).
    * **Integridad Referencial (Clave Foránea):** Asegura que las relaciones entre tablas sean válidas (`Foreign Key`).

**Ejemplo modelo relacional.**

![alt text](ej-modelo-relacional.png)

**Ejemplo de Estructura Lógica:** Un SGBD como MySQL no entiende la relación "Tiene". Solo entiende que la tabla `PEDIDOS` tiene una columna llamada `ID_Cliente` (Clave Foránea) que apunta al `ID_Cliente` de la tabla `CLIENTES` (Clave Primaria). **Así se codifica la relación.**

### El Mapeo: El Salto del Diseño a SQL

El proceso de Mapeo Relacional transforma los elementos flexibles del E/R en la estructura rígida y plana del Modelo Relacional:

| Elemento E/R (Conceptual) | Transformación (Lógico/Relacional) | Explicación |
| :--- | :--- | :--- |
| **Entidad Fuerte** | **Tabla** independiente | La entidad `AUTOR` se convierte en la tabla `AUTORES`. |
| **Atributo Compuesto** (`Dirección`) | Múltiples **Columnas** | `Dirección` se divide en `Calle`, `Ciudad` y `CodigoPostal`. |
| **Atributo Multivaluado** (`Teléfonos`) | Nueva **Tabla** | Se crea una tabla separada, `TELEFONOS_CLIENTE`, vinculada a `CLIENTES` mediante una Clave Foránea. |
| **Relación N:M** (`Alumnos` - `Materias`) | Nueva **Tabla Intermedia** | Se crea la tabla `INSCRIPCIONES` cuya clave es la unión de las claves de `ALUMNOS` y `MATERIAS`. |
| **Relación 1:N** (`Cliente` - `Pedido`) | **Clave Foránea** (FK) | La Clave Primaria de la entidad "Uno" (`ID_Cliente`) se migra como Clave Foránea a la tabla "Muchos" (`PEDIDOS`). |

## Tipos de Datos y la Columna (Atributo)

### La Importancia de la Tipificación de Datos

Cuando un **atributo** del Modelo E/R se convierte en una **columna** del Modelo Relacional, es obligatorio asignarle un **Tipo de Dato**. Este tipo de dato define el dominio de valores que la columna puede aceptar, asegurando la integridad y la eficiencia de la base de datos.

Los tipos de datos que se asignan a los atributos de las entidades cumplen o limitan los valores que pueden almacenar. Entre los más importantes y utilizados en cualquier SGBD (como MySQL, PostgreSQL, etc.) se encuentran:

#### 1. Tipos de Datos Numéricos

Se utilizan para almacenar cualquier valor de carácter numérico y son esenciales para cálculos, estadísticas e identificadores.

| Tipo de Dato | ¿Qué representa? | Explicación Detallada | Ejemplos de Uso |
| :--- | :--- | :--- | :--- |
| **Numérico (INTEGER / INT)** | Números enteros. | Utilizado para valores que no tienen componentes fraccionarios. Es el tipo de dato por excelencia para **Claves Primarias (IDs)** y conteos. | `Edad` (25), `Cantidad de productos` (100), `ID_Cliente` (8). |
| **Double / Decimal / FLOAT** | Números decimales con precisión. | Se utiliza para representar valores con una parte fraccionaria. Dependiendo del SGBD, el tipo `DOUBLE` ofrece mayor precisión, ideal para cálculos financieros o científicos. | `Salarios` (1000.50), `Medidas científicas` (3.14159), `Precio Unitario` (2.75). |

**Ejemplo de Abstracción:** En la entidad `PRODUCTO`, el atributo `Precio` debe ser **Double** para permitir centavos, mientras que `Stock` debe ser **Integer** ya que no se pueden tener 0.5 unidades de stock.

#### 2. Tipos de Datos de Carácter

Se utilizan para representar valores de texto, desde un solo carácter hasta párrafos completos.

| Tipo de Dato | ¿Qué representa? | Explicación Detallada | Ejemplos de Uso |
| :--- | :--- | :--- | :--- |
| **Texto (VARCHAR / CHAR)** | Cadenas de caracteres alfanuméricos. | Es el tipo más común para información descriptiva. **VARCHAR** (Variable Character) es el más flexible, ya que solo ocupa el espacio de los caracteres que almacena, más un pequeño extra. **CHAR** (Character) ocupa siempre el espacio máximo predefinido. | `Nombre` ("Juan"), `Dirección` ("Calle 123"), `Email` ("abc123@mail.com"). |

**Profundización (VARCHAR):** Al definir un campo, se especifica la longitud máxima, por ejemplo, `VARCHAR(255)`. Si el nombre es "Ana" (3 caracteres), solo ocupará ese espacio, a diferencia de `CHAR(255)` que ocuparía 255 caracteres fijos.

#### 3. Tipos de Datos Temporales y Lógicos

Estos tipos gestionan la información relacionada con el tiempo o las decisiones binarias (sí/no).

| Tipo de Dato | ¿Qué representa? | Explicación Detallada | Ejemplos de Uso |
| :--- | :--- | :--- | :--- |
| **Date / Time / DateTime** | Fechas, horas, o la combinación de ambas. | Permite almacenar y consultar valores temporales de forma estructurada. Es crucial para auditar datos, ordenar eventos y calcular intervalos de tiempo (como la edad). | `Fecha de nacimiento` ("2025-05-26"), `Fecha de compra`, `Hora de registro` ("14:30:00"). |
| **Boolean (Booleano / Lógico)** | Valores lógicos: verdadero o falso. | Se utiliza para atributos que solo pueden tener dos estados posibles. Es ideal para *flags* o indicadores de estado. | `Está activo?` (`true`), `Es cliente VIP?` (`false`), `Es mayor de edad?`. |

**Ejemplo de Integridad:** Un campo `FechaCompra` debe ser de tipo **Date** para que el SGBD pueda verificar que la fecha sea válida (ej. que no sea '99/99/99') y permitir comparaciones cronológicas.


## Datos a tener en cuenta

* En Base de Datos los nombres siempre van en **plural** y en **minúsculas**.
