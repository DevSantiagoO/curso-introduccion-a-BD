# Guía Práctica: Exportar e Importar Bases de Datos (.SQL)

El archivo `.sql` es el formato estándar para portabilidad y respaldo de bases de datos relacionales. Contiene todas las sentencias necesarias para crear la estructura (tablas, claves) y los datos de tu base de datos.

## 1. Exportación (Hacer un Backup o Copia)

La exportación convierte tu base de datos funcional en un único archivo de texto (`.sql`) que puedes guardar o compartir.

### Paso 1: Seleccionar la Base de Datos

1.  Abre **phpMyAdmin** en tu navegador (ej: `http://localhost/phpmyadmin/`).
2.  En el panel de la izquierda, haz clic sobre el nombre de la base de datos que quieres exportar (ej: `emp_Seguros`).

### Paso 2: Usar la Función de Exportar

1.  Haz clic en la pestaña superior llamada **"Exportar"**.
2.  **Método de Exportación (Recomendado):**
    * Selecciona **"Rápido"** (Quick) para la mayoría de los casos. Este método exportará la estructura y todos los datos con la configuración predeterminada.
3.  **Formato:**
    * Asegúrate de que el formato esté seleccionado como **"SQL"**.

**Tip Avanzado (Método Personalizado):** Si seleccionas "Personalizado", puedes elegir:
* Exportar solo la **estructura** (sin los datos de prueba).
* Exportar solo los **datos** (para tablas que ya existen).
* Excluir tablas específicas si es necesario.

### Paso 3: Descargar el Archivo

1.  Haz clic en el botón **"Exportar"** (o "Continuar").
2.  Tu navegador descargará el archivo, típicamente nombrado como `nombre_de_la_bd.sql` (ej: `emp_Seguros.sql`).


## 2. Importación (Restaurar o Cargar un Backup)

La importación recrea las tablas y llena los datos leyendo las sentencias SQL contenidas en el archivo `.sql`.

### Paso 1: Crear la Base de Datos Destino

**Necesitas un lugar vacío donde restaurar el archivo.**

1.  En phpMyAdmin, haz clic en la pestaña **"Bases de datos"** (Databases).
2.  En el campo "Crear base de datos", introduce el nombre exacto de la base de datos que deseas importar (ej: `emp_Seguros`).
3.  Haz clic en **"Crear"**.
    * *(Si la BD ya existe y deseas reemplazarla, primero debes seleccionarla y usar la opción **"Eliminar"** o **"Drop"** y luego crearla de nuevo. **¡Cuidado, esto borra todos los datos!**)*

### Paso 2: Usar la Función de Importar

1.  Haz clic en el panel de la izquierda sobre la **base de datos recién creada** (ej: `emp_Seguros`).
2.  Haz clic en la pestaña superior llamada **"Importar"**.

### Paso 3: Subir y Ejecutar el Archivo

1.  En la sección "Archivo a importar", haz clic en **"Seleccionar archivo"** (Choose file).
2.  Busca y selecciona el archivo `.sql` que exportaste previamente (ej: `emp_Seguros.sql`).
3.  **Configuración:** Generalmente, puedes dejar todas las demás opciones con sus valores predeterminados (codificación, etc.).
4.  Haz clic en el botón **"Importar"** (o "Continuar") al final de la página.

**Resultado:** Si la importación es exitosa, phpMyAdmin mostrará un mensaje verde y verás todas tus tablas (`clientes`, `propiedades`, `servicios`, etc.) en el panel de la izquierda dentro de la base de datos `emp_Seguros`.

## Ejemplo de Uso

| Escenario | Acción Principal | Uso del Archivo `.sql` |
| :--- | :--- | :--- |
| **Cambio de PC** | Exportas tu trabajo de XAMPP. | Importas el archivo `.sql` en el phpMyAdmin de tu nueva PC. |
| **Subir a Producción** | Exportas la BD de tu servidor local. | Importas el archivo `.sql` en el servidor de tu hosting (el servidor web real). |
| **Error Crítico** | Restaurar la BD a una versión anterior. | Importas un archivo `.sql` de un backup antiguo para sobrescribir los datos dañados. |