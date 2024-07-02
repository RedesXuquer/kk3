---
title: Montaje del servicio IIS, SQL Server y ASP
date: 2023-10-25 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Servicios en red]
tags: [redes locales, teoría, smr]
img_path: /assets/img/windowsWeb/   
---

![Instalación de IIS](1.png)
_Instalación de IIS_
![Instalación de IIS](2.png)
_Instalación de IIS_
![Instalación de IIS](3.png)
_Instalación de IIS_
![Instalación de IIS](4.png)
_Instalación de IIS_
![Instalación de IIS](5.png)
_Instalación de IIS_
![Instalación de IIS](6.png)
_Instalación de IIS_
![Instalación de IIS](7.png)
_Instalación de IIS_
![Instalación de IIS](8.png)
_Instalación de IIS_
![Instalación de IIS](9.png)
_Instalación de IIS_
![Instalación de IIS](10.png)
_Instalación de IIS_
![Instalación de IIS](11.png)
_Instalación de IIS_
![Instalación de IIS](12.png)
_Instalación de IIS_

## Instalación de IIS y configuración de HTTP y HTTPS
[![Página web no segura y segura](1.png)](https://youtu.be/_7x04US5mV8 "Instalación de ISS y configuración de HTTP y HTTPS")
_Instalación de http y https_

## Redirección de HTTP a HTTPS
[![Página web no segura y segura](1.png)](https://youtu.be/wu_6GzTVsY4 "Redirección de HTTP a HTTPS")
_Instalación de http y https_

## Aplicaciones necesarias
- Windows Framework 4.8
- SQL Server® 2012 SP4
- SQL Server Management Studio (SSMS) 19.0.1

### Windows Framework 4.8

Trivial.

### Instalación de SQL Server® 2012 SP4

Le damos a nueva instalación y a continuacióna todo siguiente hasta que nos pregunta la forma de conectarnos a SQL Server:
![Alt text](MyFile_2023-10-30_13-34-54.png) 
![Alt text](MyFile_2023-10-30_13-35-59.png)
![Alt text](MyFile_2023-10-30_13-36-08.png)
![Alt text](MyFile_2023-10-30_13-36-26.png)

Y terminamos la instalación de SQL Server:
![Alt text](image-3.png)

### Instalación de SQL Server Management Studio (SSMS) 19.0.1

![Alt text](MyFile_2023-10-30_13-44-41.png)
![Alt text](MyFile_2023-10-30_13-45-37.png)
![Alt text](MyFile_2023-10-30_13-45-43.png)
![Alt text](MyFile_2023-10-30_13-45-50.png)
![Alt text](MyFile_2023-10-30_13-48-07.png)
![Alt text](MyFile_2023-10-30_13-50-22.png)
![Alt text](MyFile_2023-10-30_13-44-21.png)

### Instalación más roles y características

![Alt text](MyFile_2023-10-30_13-51-31.png)
![Alt text](MyFile_2023-10-30_13-51-58.png)
![Alt text](MyFile_2023-10-30_13-54-57.png)

### Creación de usuario en SQL Server

![Alt text](MyFile_2023-10-30_21-36-00.png)
![Alt text](MyFile_2023-10-30_21-36-16.png)
![Alt text](MyFile_2023-10-30_21-36-49.png)
![Alt text](MyFile_2023-10-30_21-36-55.png)

Y probamos...

### Creación de la base de datos, la tabla y rellenar

![Alt text](MyFile_2023-10-30_21-37-26.png)
![Alt text](MyFile_2023-10-30_21-37-55.png)
![Alt text](MyFile_2023-10-30_21-38-08.png)
![Alt text](MyFile_2023-10-30_21-39-46.png)
![Alt text](MyFile_2023-10-30_21-42-11.png)
![Alt text](MyFile_2023-10-30_21-42-34.png)

### Creación del archivo index.asp

![Alt text](MyFile_2023-10-30_21-44-56.png)

Y probamos...
![Alt text](MyFile_2023-10-30_21-45-58.png)

## Creación de tabla en SQL Server

```
CREATE DATABASE NombreDeTuBaseDeDatos; -- Reemplaza "NombreDeTuBaseDeDatos" con el nombre de tu base de datos

USE NombreDeTuBaseDeDatos; -- Reemplaza "NombreDeTuBaseDeDatos" con el nombre de tu base de datos

CREATE TABLE TuTabla ( -- Reemplaza "TuTabla" con el nombre de tu tabla
    ID INT PRIMARY KEY,
    Nombre VARCHAR(50),
    Apellido VARCHAR(50),
    Edad INT
);

INSERT INTO TuTabla (ID, Nombre, Apellido, Edad) VALUES (1,'Rodolfo', 'Langostino', 50);

```


## Página web conexión a SQL Server

```
<%
' Definir la cadena de conexión a la base de datos
Dim connStr
connStr = "Provider=SQLOLEDB;Data Source=nombre_servidor;Initial Catalog=nombre_bd;User ID=usuario;Password=contraseña;"

' Crear una conexión a la base de datos
Dim conn
Set conn = Server.CreateObject("ADODB.Connection")
conn.Open connStr

' Definir una consulta SQL
Dim strSQL
strSQL = "SELECT * FROM MiTabla"

' Crear un objeto de registro (recordset) y ejecutar la consulta
Dim rs
Set rs = Server.CreateObject("ADODB.Recordset")
rs.Open strSQL, conn

' Recorrer los resultados y mostrarlos
Do Until rs.EOF
    Response.Write(rs("NombreCampo") & "<br />")
    rs.MoveNext
Loop

' Cerrar el recordset y la conexión a la base de datos
rs.Close
Set rs = Nothing
conn.Close
Set conn = Nothing
%>
```

## Extras

- Utilización y configuración de VirtualHost.
[Utilización y configuración de VirtualHost](https://analisisyprogramacionoop.blogspot.com/2018/01/crear-virtual-hosts-windows-iis.html)

- Configuración del fichero host en el Windows anfitrión.
[Configuración del fichero host en el Windows anfitrión](https://www.ionos.es/digitalguide/servidores/configuracion/archivo-hosts/#:~:text=los%20sistemas%20débiles.-,Así%20editas%20el%20archivo%20hosts,XP%2C%207%2C%208%20y%2010&text=Selecciona%20la%20opción%20“Ejecutar%20como,podrás%20modificar%20el%20archivo%20hosts.)