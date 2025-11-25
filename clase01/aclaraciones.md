# Lenguajes y Sistemas: SQL vs. MySQL

| Concepto | Tipo | Función |
| :--- | :--- | :--- |
| **SQL** | **Lenguaje** | Es el idioma estándar para interactuar con las bases de datos relacionales. |
| **MySQL** | **Sistema** | Es el software (SGBD) que almacena, procesa y ejecuta las instrucciones que le das en SQL. |


## I. SQL (Structured Query Language)

**SQL** es el **Lenguaje de Consulta Estructurado**. Es el **idioma universal** que utilizas para gestionar bases de datos relacionales.

Cuando quieres crear una tabla, insertar datos o hacer una consulta, escribes sentencias SQL, como:

* **Crear:** `CREATE TABLE`
* **Insertar:** `INSERT INTO`
* **Consultar:** `SELECT * FROM`

**Todos los Sistemas Gestores de Base de Datos (SGBD) relacionales** (como Oracle, PostgreSQL, SQL Server y MySQL) entienden y utilizan SQL.

## II. MySQL (El Sistema Gestor de Base de Datos - SGBD)

**MySQL** es un **programa** específico, un **Sistema Gestor de Bases de Datos** (DBMS o SGBD) desarrollado por Oracle (y MariaDB es su versión *open source*).

Su función es ser el **motor** que:
1.  Recibe las sentencias escritas en SQL desde el cliente (como Workbench o phpMyAdmin).
2.  Interpreta esas sentencias.
3.  Ejecuta la acción (almacenar, modificar o recuperar datos) en los archivos físicos de la base de datos.
4.  Devuelve el resultado.

## III. ¿Qué Cambia MySQL con SQL? (Dialecto)

Aunque MySQL utiliza el estándar SQL, introduce algunas extensiones o modificaciones propias que se conocen como **Dialecto**.

| Aspecto | Estándar SQL | MySQL (Dialecto) |
| :--- | :--- | :--- |
| **Comando Principal** | **SQL** | MySQL se refiere al **sistema** que recibe el lenguaje SQL. |
| **Sintaxis** | Es la base que garantiza la portabilidad entre diferentes SGBD. | Añade **funciones especiales** o **tipos de datos** que solo funcionan en MySQL. |
| **Ejemplo** | La sentencia `SELECT` es la misma en todos los SGBD. | MySQL tiene extensiones como `LIMIT` o el uso de *Storage Engines* como `InnoDB` o `MyISAM` que no son parte del estándar SQL. |

**En resumen:** Tú utilizas el **lenguaje SQL** para dar órdenes al **sistema MySQL** (el programa/motor) que es el encargado de ejecutarlas y guardar tus bases de datos.

# Acceso y Gestión de Bases de Datos en Entorno Local

## I. XAMPP: El Paquete "Todo en Uno"

**XAMPP** no es un servidor único, sino un **paquete de software** multiplataforma que simplifica la instalación de un entorno de desarrollo web local. Es un *stack* (pila) de tecnologías cuyos componentes principales son:

* **X (Cross-platform):** Indica que funciona en **Windows, Linux y macOS**.
* **A (Apache):** El **servidor web** encargado de procesar las peticiones HTTP (generalmente en el puerto **80**).
* **M (MariaDB/MySQL):** El **Sistema Gestor de Base de Datos (SGBD)**. Este es el software que realmente **almacena, organiza y gestiona** la información.
* **P (PHP) y P (Perl):** Lenguajes de programación del lado del servidor.

### Concepto Clave

XAMPP te da el **Servidor de Base de Datos** (MySQL/MariaDB) y el **Servidor Web** (Apache) listos para funcionar con un solo clic.


## II. El SGBD: MySQL/MariaDB (El Motor)

El SGBD (Sistema Gestor de Base de Datos) es el software que actúa como motor de persistencia. En el caso de XAMPP, es MySQL o su bifurcación, MariaDB.

### Formas de Acceso al Motor (MySQL)

Para interactuar con el motor de base de datos (MySQL), tenemos dos caminos principales:

| Método de Acceso | Descripción | Uso |
| :--- | :--- | :--- |
| **Acceso por Consola** | La forma más básica y directa. Se accede mediante la **Línea de Comandos** (Terminal) de tu sistema operativo (e.g., usando el comando `mysql -u root -p`). | Orientado a la **administración** avanzada, *scripts* y tareas sin interfaz gráfica. |
| **Acceso Gráfico (Cliente)** | Permite interactuar con la BD mediante una Interfaz Gráfica de Usuario (**GUI**), usando ventanas, botones y tablas. | Ideal para el **desarrollo**, diseño de esquemas y consultas complejas de forma visual. |

Para el **Acceso Gráfico**, se requiere un programa **Cliente** dedicado, como **MySQL Workbench** (una aplicación de escritorio que instalaste por separado).


## III. phpMyAdmin: La Herramienta Web de Acceso Gráfico

**phpMyAdmin** es una **aplicación web** hecha en PHP.

**Su propósito es ser la interfaz gráfica para MySQL accesible desde el navegador.**

* **¿Cómo Funciona?** phpMyAdmin reside en el servidor **Apache** (generalmente en el puerto **80**), y cuando accedes a `http://localhost/phpmyadmin`, Apache ejecuta la aplicación PHP. Esta aplicación PHP, a su vez, se conecta al motor **MySQL** (que está en el puerto **3306**) para mostrarte, de forma interactiva, los datos, las tablas y las configuraciones de la BD.
* **Conclusión:** phpMyAdmin es una **herramienta de gestión de bases de datos** que te permite ejecutar comandos SQL, diseñar tablas y ver datos de forma **interactiva** desde tu navegador, sin necesidad de instalar una aplicación de escritorio adicional (como Workbench).

### Resumen de la Relación

* **XAMPP** levanta el entorno.
* **Apache** levanta **phpMyAdmin** (la interfaz web).
* **MySQL Workbench** es una **alternativa de escritorio** a phpMyAdmin.
* Tanto phpMyAdmin como Workbench son **clientes** que envían comandos SQL al motor **MySQL/MariaDB**.