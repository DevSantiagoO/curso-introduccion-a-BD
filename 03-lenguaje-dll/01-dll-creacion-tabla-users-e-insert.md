# DDL y DML: Creación y Población de la Tabla `USERS` en Workbench

Este documento detalla el proceso para definir la estructura de la tabla `USERS` (**DDL**) e ingresar los primeros registros (**DML**), reflejando la interfaz de MySQL Workbench.

![alt text](image.png)


## I. Definición de la Estructura (DDL: `CREATE TABLE`)

La estructura se define estableciendo el **Tipo de Dato** y las **Restricciones** para cada columna. En MySQL Workbench, esto se hace visualmente antes de generar el código SQL.

| Columna | Tipo de Dato | Restricciones | Propósito |
| :--- | :--- | :--- | :--- |
| **`id_user`** | `INT` | `NOT NULL`, `AUTO_INCREMENT`, **`PRIMARY KEY`** | Identificador único y obligatorio del usuario. |
| **`name`** | `VARCHAR(100)` | `NOT NULL` | Nombre obligatorio del usuario. |
| **`surname`** | `VARCHAR(100)` | `NOT NULL` | Apellido obligatorio del usuario. |
| **`age`** | `INT` | | Edad del usuario. |
| **`init_date`** | `DATE` | | Fecha de inicio o registro del usuario (guarda: `YYYY-MM-DD`). |
| **`email`** | `VARCHAR(255)` | | Correo electrónico. |


### Código SQL Generado (DDL)

El código DDL es la instrucción que se envía al servidor MySQL para crear físicamente la tabla.

```sql
-- DDL: CREATE TABLE
CREATE TABLE USERS (
    id_user INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    surname VARCHAR(100) NOT NULL,
    age INT,
    init_date DATE,
    email VARCHAR(255),
    PRIMARY KEY (id_user)
);
```

## II. Ingreso de Datos (DML: INSERT INTO)
Una vez que la estructura (`CREATE TABLE`) es enviada y ejecutada con éxito, se procede a ingresar los primeros registros utilizando la sentencia INSERT INTO.

* Recordatorio de Convención: Las palabras reservadas de SQL (como `SELECT`, `INSERT`, `VALUES`, `FROM`) deben escribirse en mayúsculas.

```SQL

-- DML: INSERT INTO para agregar registros
INSERT INTO USERS (name, surname, age, init_date, email)
VALUES ('Juan', 'Perez', 30, '2023-01-15', 'juan.perez@mail.com');

INSERT INTO USERS (name, surname, age, init_date, email)
VALUES ('Ana', 'Gomez', 25, '2023-05-20', 'ana.gomez@mail.com');
```

## III. Verificación (DML: SELECT)
Para confirmar la inserción, la tabla se consulta inmediatamente:

```SQL
-- DML: SELECT para verificar la inserción
SELECT * FROM USERS;
```
