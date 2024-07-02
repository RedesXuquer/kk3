---
title: Montaje del servicio WEB, MySQL y PHP
date: 2023-09-25 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Servicios en red]
tags: [redes locales, teoría, smr]
img_path: /assets/img/web/   
---

![Logo de Apache](apache.png)
_Logo de Apache_


# Introducción
Un servidor web es un componente fundamental de la infraestructura de Internet que desempeña un papel crucial en la entrega de contenido en línea. En esencia, un servidor web es un software o hardware que almacena, gestiona y distribuye páginas web, archivos, imágenes y otros recursos a través de Internet. Está diseñado para recibir solicitudes de clientes web, como navegadores de Internet, y responder a esas solicitudes enviando los archivos correspondientes para que los usuarios puedan ver y interactuar con ellos en sus dispositivos.

# Instalación del servicio web en Ubuntu Server 22.04 LTS

## Cosas necesarias previas a la instalación
- Configuración de MV servidor en red nat
- MV cliente Xubuntu en la misma red nat
- Configuración red nat 192.168.100.0/24

Con permisos de root ejecutamos el comando:

```console
sudo apt-get install apache2
```

Comprobamos que el servicio está activo en su puerto 80:

```console
netstat -putona
```

Otra opción para comprobar que el servicio está activo:

```console
sudo /etc/init.d/apache2 status
```

![Información de Apache2](exitophp.png)
_Información de Apache2_

La ubicación de nuestros archivos es
```
cd /var/www/html/
```

Podemos realizar pruebas en nuestro navegador de Host y poner en la dirección _localhost_

Una página de ejemplo podría ser:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Mi Página Web de Ejemplo</title>
</head>
<body>
    <header>
        <h1>Bienvenido a Mi Página Web de Ejemplo</h1>
        <nav>
            <ul>
                <li><a href="#">Inicio</a></li>
                <li><a href="#">Acerca de</a></li>
                <li><a href="#">Servicios</a></li>
                <li><a href="#">Contacto</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section>
            <h2>Acerca de Nosotros</h2>
            <p>Somos una empresa ficticia dedicada a brindar soluciones imaginarias.</p>
        </section>

        <section>
            <h2>Nuestros Servicios</h2>
            <ul>
                <li>Servicio 1</li>
                <li>Servicio 2</li>
                <li>Servicio 3</li>
            </ul>
        </section>
    </main>

    <footer>
        <p>Derechos de autor &copy; 2023 Mi Página Web de Ejemplo</p>
    </footer>
</body>
</html>
```

## Logs de Apache2
```
sudo tail -f /var/log/apache2/access.log
```
```
sudo tail -f /var/log/apache2/error.log
```
```
sudo tail -n 100 /var/log/apache2/access.log
```

## Archivos de configuración de Apache2
```
# This is the main Apache server configuration file.
sudo vim /etc/apache2/apache2.conf

# If you just change the port or add more ports here
sudo vim /etc/apache2/port.conf

# Default Apache virtualhost
sudo vim /etc/apache2/site-available/default.conf
```

Y para validar la configuración de Apache2
```
sudo apache2ctl configtest
```

## Extras

Cambia el puerto 80 al 8080
Investiga para que sirve el archivo default.conf

# Instalación del servicio MySQL en Ubuntu Server 22.04 LTS

## Diferencia entre MariaDB y MySql

MariaDB y MySQL son dos sistemas de gestión de bases de datos relacionales (RDBMS) que comparten una historia y un propósito comunes, pero también tienen algunas diferencias clave:

### Origen:

MySQL: MySQL es un sistema de gestión de bases de datos relacionales de código abierto que se originó en 1995. Fue desarrollado por una empresa sueca llamada MySQL AB y posteriormente adquirido por Sun Microsystems y luego por Oracle Corporation en 2010.
MariaDB: MariaDB es una bifurcación (fork) de MySQL que se creó en 2009. Fue desarrollado por Michael "Monty" Widenius, el cofundador de MySQL, como una respuesta a preocupaciones sobre el futuro de MySQL bajo la propiedad de Oracle.
Licencia:

MySQL: MySQL utiliza la licencia dual, lo que significa que ofrece una versión de código abierto bajo la Licencia Pública General de GNU (GPL) y una versión comercial con licencia propietaria.
MariaDB: MariaDB utiliza la Licencia Pública General de GNU (GPL) en su versión de código abierto y no ofrece una versión comercial propietaria.

### Compatibilidad:

MariaDB se ha esforzado por mantener la compatibilidad con MySQL en la mayoría de los casos. La mayoría de las aplicaciones y consultas escritas para MySQL también funcionarán en MariaDB sin cambios significativos.
Sin embargo, MariaDB ha agregado algunas características y optimizaciones que no están presentes en las versiones de MySQL más antiguas. Además, puede haber diferencias en las características específicas de la versión entre MySQL y MariaDB.
Almacenamiento y motores de almacenamiento:

Ambos sistemas admiten una variedad de motores de almacenamiento, pero MariaDB ha introducido su propio motor de almacenamiento llamado Aria, que se utiliza como reemplazo de MyISAM.
MariaDB también ha mejorado el motor InnoDB en comparación con las versiones más antiguas de MySQL.
Rendimiento y características:

MariaDB ha trabajado en mejoras de rendimiento y en la incorporación de nuevas características en comparación con MySQL.
MariaDB incluye capacidades de replicación y clustering mejoradas y ha desarrollado características específicas de almacenamiento en caché y optimización.
En general, la elección entre MariaDB y MySQL dependerá de sus necesidades específicas y preferencias. Ambos sistemas son robustos y ampliamente utilizados en la comunidad de desarrollo de software, y su elección puede basarse en factores como la compatibilidad con aplicaciones existentes, la filosofía de licencia y las características específicas que requiera para su proyecto.

## Instalación de mariaDB

Instalamos el servicio de bases de datos:
```
sudo apt-get install mariadb-server
```

Comprobamos:
```
sudo netstat -putona
```

Comprobamos:
```
sudo /etc/init.d/mariadb status
```

Configuramos el servicio:
```
sudo mariadb-secure-installation
```

Entramos en mariadb:
```
mysql -u root -p
```

Mostramos las bases de datos:
```
show databases;

```
Creamos una base de datos:
```
create database ejemplo;
```

La selecionamos:
```
use ejemplo;
```

Creamos un tabla:
```
CREATE TABLE mitabla(
         id MEDIUMINT NOT NULL AUTO_INCREMENT,
         nombre CHAR(30) NOT NULL,
         edad INTEGER(30),
         salario INTEGER(30),
         PRIMARY KEY (id) );
```

Añadimos información a nuestra tabla:
```
INSERT INTO mitabla (nombre, edad, salario) VALUES
        ("Pedro", 24, 21000),
        ("Maria", 26, 24000),
        ("Juan", 28, 25000),
        ("Luis", 35, 28000),
        ("Monica", 42, 30000),
        ("Rosa", 43, 25000),
        ("Susana", 45, 39000);
```

Mostramos la información introducida:
```
select * from mitabla;
```

Para salir de mariadb:
```
exit
```

# Instalación de PHP y demás librería para poder trabajar con MariaDB

## PHP8.1
Instalamos PHP 8.1:
```
sudo apt-get install php8.1
```

Comprobamos que la instalación ha sido correcta:
```
sudo vi /var/www/html/index.php
```

Con el siguiente contenido:
```
<?php
phpinfo();
?>
```
![Información de PHP](exitoweb.png)
_Información de PHP_

Ahora vamos a instalar las librería necesaria para conectar PHP con MariaDB:
```
sudo apt-get install php8.1-mysql
```

Comprobamos nuevamente que la instalación ha sido correcta:
```
sudo vi /var/www/html/conexionmysql.php
```

Con el siguiente contenido (hay que realizar los cambios pertinentes para nuestra configuración):
```
<?php
// Conectando, seleccionando la base de datos
$link = mysqli_connect('local_computer', 'mysql_user', 'mysql_pass')
    or die('No se pudo conectar: ' . mysqli_error());
echo 'Connected successfully';
mysqli_select_db($link, 'database') or die('No se pudo seleccionar la base de datos');

// Realizar una consulta MySQL
$query = 'SELECT * FROM table';
$result = mysqli_query($link, $query) or die('Consulta fallida: ' . mysql_error());

// Imprimir los resultados en HTML
echo "<table>\n";
while ($line = mysqli_fetch_array($result)) {
        echo "\t<tr>\n";
    foreach ($line as $col_value) {
        echo "\t\t<td>$col_value</td>\n";
    }
    echo "\t</tr>\n";
}
echo "</table>\n";

// Liberar resultados
mysqli_free_result($result);

// Cerrar la conexión
mysqli_close($link);
?>
```

![Conexión de PHP a MariaDB](exitomariadb.png)
_Conexión de PHP a MariaDB_

## Extras

- Configuración de HTTPS
[Configuración de HTTPS](https://techexpert.tips/es/apache-es/habilitar-https-en-apache/)
- Redirección de HTTP a HTTPS
[Redirección de HTTP a HTTPS](https://techexpert.tips/es/apache-es/apache-redireccionar-http-a-https/)

- Utilización y configuración de VirtualHost.
[Utilización y configuración de VirtualHost](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-20-04)

- Configuración del fichero host en el Windows anfitrión.
[Configuración del fichero host en el Windows anfitrión](https://www.ionos.es/digitalguide/servidores/configuracion/archivo-hosts/#:~:text=los%20sistemas%20débiles.-,Así%20editas%20el%20archivo%20hosts,XP%2C%207%2C%208%20y%2010&text=Selecciona%20la%20opción%20“Ejecutar%20como,podrás%20modificar%20el%20archivo%20hosts.)