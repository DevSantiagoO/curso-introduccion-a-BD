# Clase 03: Introducción y Fundamentos de SQL (Structured Query Language)

## 1. Definición y Propósito del SQL

El **SQL** (Structured Query Language, o Lenguaje de Consulta Estructurado) es el **lenguaje estándar** y universalmente aceptado que se utiliza para interactuar con bases de datos relacionales.

* **Modelo de Datos:** SQL trabaja directamente con el **Modelo Relacional**, donde la información está organizada en tablas (relaciones) y filas (tuplas).
* **Función Esencial:** Permite a los usuarios realizar **consultas**, manipular datos y definir estructuras. Sin SQL, no podríamos pedirle, cambiarle o guardarle información a la base de datos.
* **Clasificación:** Es un **lenguaje de dominio específico** (DSL), diseñado exclusivamente para la gestión de datos.

### Principio de la Interacción SQL
Una **consulta SQL** es una **instrucción** específica que le das a una **base de datos** para que devuelva, modifique o gestione información. Es como hacerle una **pregunta** o darle una **orden** a la base de datos usando el lenguaje SQL.

* La tabla es la **Unidad Fundamental**. Contiene **filas (Tuplas)** y **columnas (Atributos)**.
* Las **Restricciones de Integridad** (como la Primary Key y la Foreign Key) son las reglas que aseguran que el SGBD pueda guardar datos válidos y mantener las relaciones entre tablas.


## 2. Clasificación Completa de Sentencias SQL

Según lo que hacen, las consultas se agrupan en cuatro tipos de lenguaje:

| Tipo | Significado | Objetivo Principal | Ejemplos de Sentencias |
| :--- | :--- | :--- | :--- |
| **DDL** | **Definición de Datos** | Define o modifica la **estructura** (tablas, columnas, claves) | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` |
| **DML** | **Manipulación de Datos** | Interactúa con los **datos** (filas) dentro de las tablas | `SELECT`, `INSERT`, `UPDATE`, `DELETE` |
| **DCL** | **Control de Datos** | Administra los **permisos y la seguridad** de acceso | `GRANT`, `REVOKE` |
| **TCL** | **Control de Transacciones** | Gestiona la **integridad y el estado** de las operaciones | `BEGIN/START TRANSACTION`, `COMMIT`, `ROLLBACK` |

### 2.1. Lenguaje de Manipulación de Datos (DML)

El DML se centra en la **lectura y modificación** de la información (las filas).

* **`SELECT`:** Buscar datos (como listar todos los productos de una tienda).
* **`INSERT`:** Guardar datos (por ejemplo, registrar un usuario en una app).
* **`UPDATE`:** Actualizar datos (cambiar el precio de un producto).
* **`DELETE`:** Eliminar datos (borrar un comentario de una red social).

### 2.2. Lenguaje de Definición de Datos (DDL)

El DDL se centra en la **creación y modificación del esqueleto** de la BD.

* **`CREATE`:** Crea estructuras (ej: `CREATE TABLE clientes...`).
* **`ALTER`:** Modifica estructuras existentes (ej: agregar una nueva columna).
* **`DROP`:** Elimina estructuras completas (ej: eliminar una tabla o la base de datos).

### 2.3. Control de Datos (DCL)
Utilizado por administradores para garantizar la seguridad.
* **`GRANT`:** Otorga permisos a un usuario para realizar ciertas acciones.
* **`REVOKE`:** Revoca o quita permisos previamente otorgados.

### 2.4. Control de Transacciones (TCL)
Fundamental para operaciones críticas, asegurando que una serie de pasos se complete **totalmente o nada**.
* **`COMMIT`:** Confirma que todos los cambios realizados son permanentes y se guardan en la base de datos.
* **`ROLLBACK`:** Deshace todos los cambios desde el inicio de la transacción si ocurre un error o se cancela.

**Tip de Implementación:** En la implementación del ejercicio `emp_Seguros`, las sentencias `CREATE TABLE` fueron **DDL**, y las `INSERT INTO` fueron **DML**.