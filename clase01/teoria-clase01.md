# Clase 01: Fundamentos y Configuración

## Introducción: ¿Qué es una Base de Datos (BD)?

Una **Base de Datos (BD)** es una **colección organizada y sistemática de datos** que están interrelacionados y que pertenecen a un **mismo contexto** o dominio. Su propósito fundamental es **almacenar** la información de manera eficiente y segura para permitir su **posterior gestión, consulta y análisis**.

* **Colección Organizada:** Los datos no están dispersos, sino que se estructuran de forma lógica (por ejemplo, en tablas, documentos o grafos).
* **Contexto Específico:** Aunque los datos sean diversos, giran en torno a un tema o una organización particular (e.g., todos los datos de un banco, o todos los datos de una biblioteca).
* **Persistencia:** La información se mantiene almacenada a largo plazo.


## La Naturaleza de la Interrelación

La característica clave de una base de datos es que los datos, aunque puedan tener **contenidos o temáticas diferentes**, están vinculados por **relaciones en común**. Esto es lo que permite que la BD sea una fuente de información coherente y no solo una lista de archivos.

* **Diferencia de Contenido:** Un dato puede ser el nombre de un cliente ("Juan Pérez") y otro dato puede ser un número de producto ("P-456").
* **Relación en Común:** La base de datos establece la relación: **"El Cliente Juan Pérez compró el Producto P-456"**. Esta vinculación transforma los datos brutos en **información útil**.

### Ejemplos de Bases de Datos

Para entender mejor su aplicación, considera los siguientes escenarios:

| Ámbito | Elementos Almacenados (Contenido Diverso) | Relación en Común |
| :--- | :--- | :--- |
| **Comercio Electrónico** | Nombre de usuario, dirección de envío, precio del producto, fecha de la compra. | El **ID de Pedido** vincula al cliente, los productos comprados y la dirección de destino. |
| **Biblioteca** | Título del libro, nombre del autor, número de ejemplares, identificación del socio. | La **Transacción de Préstamo** vincula a un socio específico con un ejemplar de un libro durante un período. |
| **Sistema Universitario** | Nombre del estudiante, calificación de una asignatura, nombre del profesor, horario de la clase. | El **Registro de Matrícula** vincula a un estudiante con una asignatura específica impartida por un profesor en un semestre. |

## ¿Dónde y Cómo se Gestionan las Bases de Datos (BD)?

La ubicación de una BD no solo se refiere al lugar físico, sino también a su posición dentro de la **arquitectura de software** que permite su uso.

## Ubicación Arquitectónica: La Capa de Persistencia

En el contexto de un sistema informático, la Base de Datos se ubica en el **nivel más bajo** de la arquitectura, conocido como la **Capa de Persistencia**.

* **Definición:** Es el lugar donde los datos viven de forma permanente y segura, incluso cuando la aplicación que los utiliza deja de funcionar.
* **Contraste:** A diferencia de la memoria volátil (RAM), donde residen los programas en ejecución, la BD reside en un almacenamiento persistente.
* **Jerarquía:** Esta capa es la base sobre la cual se construyen todas las demás capas del sistema (lógica de negocio y presentación).

## La Dualidad de la Base de Datos: Lógico vs. Físico

Una BD se describe mejor como una entidad con dos aspectos clave:

### A. Aspecto Físico (El *Dónde* Real)

La BD es considerada "física" porque, para existir, requiere de un *hardware* concreto.

* **Dispositivo Físico:** Se almacena en unidades de disco duro (HDD/SSD) de un **servidor** (que puede ser una máquina local, un servidor dedicado o una máquina virtual).
* **Entorno:** Estos servidores suelen estar ubicados en **Centros de Datos (Data Centers)**.
* **Ejemplo Moderno:** Hoy en día, muchas BD residen en la **nube** a través de servicios gestionados (como Amazon RDS, Azure Database o Google Cloud SQL), lo que abstrae la preocupación física al usuario, pero la necesidad de un servidor subyacente sigue siendo real.

### B. Aspecto Lógico (La *Cómo* se Ve)

El aspecto lógico se refiere a la estructura, el diseño y la forma en que los datos están organizados y se relacionan entre sí.

* **Esquema:** Es la "hoja de ruta" de la BD, que define las tablas, campos, tipos de datos y las relaciones. Esto es lo que percibe y usa el programador.
* **Independencia de Datos:** Una de las grandes ventajas de esta dualidad es la **Independencia de Datos**. Un usuario o programa interactúa con el aspecto *lógico* (el esquema) sin saber ni preocuparse por la ubicación *física* exacta en el disco.

## El Sistema Gestor de Base de Datos (SGBD/DBMS)

Para pasar del aspecto lógico al físico (es decir, para acceder a los datos), se necesita un intermediario: el SGBD/DBMS.

| Concepto | Significado | Función Clave |
| :--- | :--- | :--- |
| **SGBD** | Sistema Gestor de Base de Datos | Software que actúa como interfaz entre el usuario y la BD física. |
| **DBMS** | Data Base Management System | Acrónimo en inglés (el término más común a nivel global). |

### Funciones Ampliadas del SGBD:

1.  **Acceso y Manipulación:** Permite a los usuarios y aplicaciones **consultar, insertar, modificar y eliminar** datos (operaciones CRUD).
2.  **Seguridad:** Controla qué usuarios tienen permiso para acceder a qué partes de la BD (creación de usuarios, roles y permisos).
3.  **Integridad:** Asegura que los datos sean precisos y consistentes, aplicando reglas y restricciones definidas en el esquema.
4.  **Concurrencia:** Gestiona múltiples usuarios que intentan acceder y modificar los mismos datos al mismo tiempo, evitando conflictos.

### Ejemplos de SGBD Populares:

* **Relacionales (SQL):** **MySQL**, **PostgreSQL**, Oracle Database, Microsoft SQL Server.
* **No Relacionales (NoSQL):** MongoDB, Redis, Cassandra.

## El Servidor de Base de Datos

El Servidor de Base de Datos (BD) es el componente físico o virtual esencial que aloja el software gestor (SGBD) y los datos, haciéndolos accesibles a los usuarios.

### Concepto Básico: Servidor y Modelo Cliente-Servidor

Un **servidor** es una **computadora** (o un programa) que proporciona **servicios o recursos** a otras computadoras conectadas a través de una red.

* **Modelo Cliente-Servidor:** Este modelo es la base de la mayoría de las arquitecturas de BD.
    * **Cliente:** La aplicación o máquina que **solicita** un recurso (ej. una consulta SQL).
    * **Servidor:** La máquina que **ofrece, procesa y responde** a esa solicitud (ej. devuelve los datos solicitados).

### Definición y Rol del Servidor de BD

Un **Servidor de Base de Datos** es una computadora, ya sea **local o remota**, dedicada exclusivamente a **almacenar, organizar, procesar y permitir el acceso** a los datos de manera segura y eficiente.

* **El Vínculo Crucial:** El Servidor de BD es la máquina física donde se encuentra instalado el **SGBD (Sistema Gestor de Base de Datos)**. Sin el servidor, el SGBD no tiene dónde residir y gestionar los datos.
* **Función Principal:** Actúa como el motor que ejecuta las operaciones del SGBD, respondiendo a las peticiones de los clientes (aplicaciones web, móviles, programas de escritorio, etc.).

### Funcionalidades Clave del Servidor de BD

El servidor se encarga de manejar las responsabilidades de la BD, asegurando un entorno de datos robusto y accesible:

* **Procesamiento de Consultas:** Ejecuta las consultas (ej. `SELECT * FROM tabla`) de forma optimizada y devuelve los resultados al cliente.
* **Seguridad:** Implementa medidas de autenticación y autorización para asegurar que solo los usuarios permitidos puedan acceder y modificar la BD.
* **Manejo de Concurrencia:** Gestiona miles de peticiones simultáneas, evitando la corrupción de datos.
* **Backup y Recuperación:** Se encarga de las copias de seguridad de la información y permite la restauración en caso de fallos.

### Tipos y Ejemplos de Servidores

Para poder usar bases de datos, siempre es necesario disponer de un servidor, lo cual implica tener instalado un SGBD específico.

#### A. Tipos de Instalación

| Tipo de Servidor | Descripción |
| :--- | :--- |
| **Local** | Instalado en la misma máquina del desarrollador para pruebas. |
| **Dedicado** | Una máquina física o virtual (VM) cuyo único propósito es ejecutar el SGBD. |
| **En la Nube** | Servicios gestionados (PaaS) que abstraen la gestión del hardware (ej. Amazon RDS, Google Cloud SQL, Azure Database). |

#### B. Ejemplos (Servidor + SGBD)

El servidor toma el nombre del software SGBD que aloja, lo que define el tipo de datos que maneja:

* **Servidor MySQL:** Alojando el SGBD **MySQL** (Relacional).
* **Servidor PostgreSQL:** Alojando el SGBD **PostgreSQL** (Relacional avanzado/Objeto-Relacional).
* **Servidor Oracle:** Alojando el SGBD **Oracle Database** (Relacional propietario).
* **Servidor MongoDB:** Alojando el SGBD **MongoDB** (NoSQL, basado en documentos).
* **Servidor Redis:** Alojando el SGBD **Redis** (NoSQL, basado en clave-valor en memoria).

## Herramientas para Servidores Locales

Para comenzar a trabajar con Bases de Datos (BD) en un entorno de aprendizaje o desarrollo, generalmente se configuran **servidores de bases de datos LOCALES**. Esto permite practicar y probar aplicaciones sin depender de un servidor remoto o conexión a Internet.

### Configuración de Entorno Local

Para facilitar la instalación de los componentes necesarios (el servidor web, el SGBD y el lenguaje de *scripting*), se utilizan *stacks* o paquetes "todo en uno".

* **Objetivo:** Instalar el **Servidor Web Apache**, el **SGBD (MySQL/MariaDB)** y el lenguaje de programación **PHP** o **Perl** en un solo proceso.
* **Ventaja:** Simplifica la configuración inicial, ya que no hay que instalar y enlazar cada componente por separado.

### Stacks de Servidores Locales (W-X-L-M)

La elección del paquete dependerá principalmente del **Sistema Operativo (SO)** que utilices. Los nombres de estos *stacks* suelen derivar de las iniciales del sistema operativo y los componentes incluidos (Apache, MySQL, PHP).

| Stack de Servidor | Significado (Comúnmente) | Sistemas Operativos Compatibles |
| :--- | :--- | :--- |
| **Wamp Server** | **W**indows + Apache + MySQL + PHP | **Solo para Windows** |
| **Xampp Server** | **X** (Cross-platform) + Apache + MariaDB + PHP | **Windows, Linux y macOS** |
| **Lamp Server** | **L**inux + Apache + MySQL + PHP | **Solo para Linux** |
| **Mamp Server** | **M**acOS + Apache + MySQL + PHP | **macOS y Windows** |

### Explicación de las Iniciales:

* **W, L, M:** Representan el sistema operativo (Windows, Linux, macOS).
* **X:** Indica que es **Multiplataforma** (*Cross-platform*).
* **A:** **Apache HTTP Server** (el servidor web).
* **M:** **MySQL** o **MariaDB** (el SGBD).
* **P:** **PHP**, **Perl** o **Python** (los lenguajes de programación).

### Recomendación y Uso

Si bien todos cumplen la misma función, **Xampp** es a menudo el más recomendado para principiantes debido a su **compatibilidad multiplataforma** y su facilidad de uso.

* **Requisito:** Para comenzar a programar bases de datos, debes descargar e instalar uno de estos servidores y asegurarte de que los servicios (Apache y MySQL/MariaDB) estén correctamente iniciados.

# Cómo abrir XAMPP en Ubuntu

A diferencia de Windows, en Ubuntu XAMPP no suele crear un acceso directo en el escritorio automáticamente al instalarse. La forma estándar de abrirlo es mediante la **Terminal**.

## Opción 1: Iniciar los servicios directamente (Rápido)

Esta opción enciende el servidor (Apache y MySQL) sin abrir ninguna ventana gráfica. Es lo que hacen los desarrolladores habitualmente.

1.  Abre tu terminal (`Ctrl` + `Alt` + `T`).
2.  Copia y pega el siguiente comando (te pedirá tu contraseña de usuario):

```bash
sudo /opt/lampp/lampp start
```

## Opción 2: Abrir el Panel Gráfico (Manager)
Si prefieres ver la ventanita con los botones de "Start", "Stop" y los semáforos en verde (similar al Panel de Control de Windows), usa este comando:

```bash
sudo /opt/lampp/manager-linux-x64.run
```

## Cómo detener XAMPP
Cuando termines la clase o de programar, apaga los servicios para liberar memoria en tu Ubuntu:

```bash
sudo /opt/lampp/lampp stop
```

**Ejemplo de la creación de una tabla en phpmyadmin**

![alt text](ejemplo.png)