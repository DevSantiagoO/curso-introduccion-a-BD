# 1. Instalación de los Componentes Clave

### 1.1. Instalación de MySQL Server

El servidor MySQL es el *motor* que ejecuta las bases de datos y gestiona las peticiones en el puerto $3306$.

1. **Actualizar la lista de paquetes:**
    ```bash
    sudo apt update
    ```

2. **Instalar el servidor MySQL:**
    ```bash
    sudo apt install mysql-server
    ```
    *Durante la instalación, se te pedirá establecer la **contraseña root** para tu servidor MySQL.*

3. **Ejecutar el script de seguridad (Recomendado):**
    Esto ayuda a mejorar la seguridad de la instalación.
    ```bash
    sudo mysql_secure_installation
    ```
    *Sigue las indicaciones. Generalmente, es seguro responder 'Y' (Sí) a todas las preguntas, especialmente para eliminar usuarios anónimos y deshabilitar el login remoto de `root`.*

### 1.2. Instalación de MySQL Workbench

MySQL Workbench es una **aplicación cliente gráfica** que permite diseñar, desarrollar y administrar bases de datos MySQL de forma visual.

1. **Instalar MySQL Workbench:**
    ```bash
    sudo apt install mysql-workbench
    ```
    *Alternativamente, puedes descargarlo como paquete `.deb` desde el sitio web oficial de MySQL e instalarlo usando `sudo dpkg -i <nombre_paquete>.deb`.*
    


# 2. Gestión del Servicio MySQL (Systemd)

MySQL se instala como un servicio que se gestiona mediante **Systemd** en Ubuntu. Esto permite controlarlo de manera eficiente en segundo plano.

### 2.1. Iniciar el Servicio (Activación del Puerto 3306)

Al iniciar el servicio, el servidor MySQL comienza a escuchar peticiones en el puerto estándar 3306.

```bash
sudo systemctl start mysql
```

**Nota Importante:** El puerto 3306 permanece abierto y el servidor activo hasta que lo detengas explícitamente, incluso si cierras MySQL Workbench o reinicias la computadora (si está configurado para inicio automático).

### 2.2. Detener el Servicio (Cierre del Puerto 3306)

Detener el servicio detiene el proceso del servidor y **cierra el puerto 3306**. Nadie podrá conectarse hasta que se vuelva a iniciar.

```bash
sudo systemctl stop mysql
```

### 2.3. Verificar el Estado del Servicio

Para confirmar si el servidor está corriendo (es decir, si el puerto 3306 está activo):

```bash
sudo systemctl status mysql
```

  * **Si está activo:** Verás `Active: active (running)` en la salida.
  * **Si está inactivo:** Verás `Active: inactive (dead)`.

### 2.4. Reiniciar el Servicio

Útil para aplicar cambios de configuración.

```bash
sudo systemctl restart mysql
```


## 3. Ejecución de Sentencias SQL

Puedes ejecutar comandos SQL de dos maneras principales: a través de la **línea de comandos** o mediante **MySQL Workbench**.

### 3.1. Usando la Terminal (Cliente de Línea de Comandos)

Ideal para tareas rápidas o scripts.

1.  **Acceder a la *shell* de MySQL:**

    ```bash
    sudo mysql -u root -p
    ```

    *Ingresa la contraseña que configuraste para el usuario `root`.*

2.  **Ejecutar sentencias SQL:**
    Una vez dentro, puedes escribir comandos SQL directamente. Por ejemplo:

    ```sql
    SHOW DATABASES;
    CREATE DATABASE mi_base_de_datos;
    USE mi_base_de_datos;
    EXIT;
    ```

### 3.2. Usando MySQL Workbench (Interfaz Gráfica)

La forma más común para desarrollo y administración.

1.  **Abrir Workbench:**
    Inicia la aplicación (búscala en el lanzador de aplicaciones de Ubuntu).

2.  **Crear una Conexión Local:**

      * Haz clic en el signo **`+`** junto a *MySQL Connections*.
      * **Connection Name:** Dale un nombre a tu conexión (ej: `Localhost`).
      * **Hostname:** `127.0.0.1` (o `localhost`).
      * **Port:** `3306`.
      * **Username:** `root` (o el usuario que hayas creado).
      * Haz clic en **Test Connection** para verificar que funciona e ingresa tu contraseña.

3.  **Ejecutar Sentencias SQL:**

      * Haz clic en la conexión que acabas de crear para abrir un **SQL Editor**.
      * Escribe tus consultas SQL en el panel (ej: `SELECT * FROM tabla;`).
      * Haz clic en el botón de **Ejecutar** (el rayo) para procesar la consulta.


## 4. Resumen del Flujo de Trabajo

| Tarea | Herramienta | Comando / Acción | Efecto Clave |
| :--- | :--- | :--- | :--- |
| **Encender el Servidor** | Terminal (Systemd) | `sudo systemctl start mysql` | **Abre el Puerto 3306** |
| **Trabajar con BD** | MySQL Workbench | Conectar y escribir SQL | Diseño y Consulta de Datos |
| **Detener el Servidor** | Terminal (Systemd) | `sudo systemctl stop mysql` | **Cierra el Puerto 3306** |
| **Verificar Estado** | Terminal (Systemd) | `sudo systemctl status mysql` | Muestra si está `active (running)` |

