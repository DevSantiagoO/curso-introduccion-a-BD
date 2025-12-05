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