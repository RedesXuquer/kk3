---
title: Servicio FTP con usuarios virtuales de AD en Windows Server
date: 2023-11-13 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Servicios en red]
tags: [redes locales, teoría, smr]
img_path: /assets/img/FTP/Windows/
---

# Servicio FTP con usuarios virtuales de AD en Windows Server 2012R2

En este tutorial, te guiaremos a través del proceso de instalación de un servidor FTP en un entorno Windows Server, aprovechando la integración con Active Directory para gestionar usuarios y aplicando medidas de seguridad esenciales.

## Paso 1: Preparación del Entorno

Antes de comenzar, asegúrate de que tu servidor Windows está correctamente configurado y tiene instalado el servicio Active Directory. Esto proporcionará la base para gestionar usuarios de manera centralizada.

## Paso 2: Instalación del Servicio FTP

Abre el "Administrador del Servidor" en tu Windows Server.
Selecciona "Administrar" y luego "Agregar roles y características".
Sigue el asistente de instalación, seleccionando el rol "Servidor FTP" y cualquier característica adicional que necesites.
Completa la instalación y asegúrate de habilitar la opción "Habilitar el soporte para FTP básico" y "Habilitar el soporte para FTP de escritura".

![Alt text](<Captura de pantalla 2023-11-10 194121.png>)
![Alt text](<Captura de pantalla 2023-11-10 194531.png>)
![Alt text](<Captura de pantalla 2023-11-10 194134.png>)

Una vez instalado todo vamos a configurar el AD con las siguientes características:
- Dominio raíz: Axuquer.local
- Establecemos la contraseña
- NetBIOS: AXUQUER

![Alt text](<Captura de pantalla 2023-11-10 195344.png>)
![Alt text](<Captura de pantalla 2023-11-10 195440.png>)
![Alt text](<Captura de pantalla 2023-11-10 195509.png>)
![Alt text](<Captura de pantalla 2023-11-10 195535.png>)
![Alt text](<Captura de pantalla 2023-11-10 195550.png>)
![Alt text](<Captura de pantalla 2023-11-10 195641.png>)

## Paso 3: Creación de usuarios FTP virtuales

Vamos a crear 2 usuarios y 1 grupo:
- Primer usuario: userFtp1
- Segundo usuario: userFtp2
- Grupo: usuariosFtp

![Alt text](MyFile_2023-11-10_20-06-33.png)
![Alt text](MyFile_2023-11-10_20-06-41.png) 
![Alt text](MyFile_2023-11-10_20-06-49.png)
![Alt text](MyFile_2023-11-10_20-06-57.png)
![Alt text](MyFile_2023-11-10_20-07-26.png)
![Alt text](MyFile_2023-11-10_20-07-33.png)
![Alt text](MyFile_2023-11-10_20-07-57.png)
![Alt text](MyFile_2023-11-10_20-08-13.png)
![Alt text](MyFile_2023-11-10_20-08-50.png)
![Alt text](MyFile_2023-11-10_20-09-55.png)
![Alt text](MyFile_2023-11-10_20-10-01.png)
![Alt text](MyFile_2023-11-10_20-10-17.png)

## Paso 4: Configuración del Servidor FTP

Abre el "Administrador de IIS" (Internet Information Services).
Navega hasta el nodo del servidor y selecciona "Sitios FTP".
Haz clic derecho en "Sitio FTP predeterminado" y selecciona "Configurar seguridad de autenticación".
Habilita la autenticación básica.

![Alt text](MyFile_2023-11-13_17-33-40.png)
![Alt text](MyFile_2023-11-13_17-32-38.png)
![Alt text](MyFile_2023-11-13_17-32-44.png)
![Alt text](MyFile_2023-11-13_17-33-51.png)
![Alt text](MyFile_2023-11-13_17-34-10.png)
![Alt text](MyFile_2023-11-13_17-34-20.png)
![Alt text](MyFile_2023-11-13_17-34-44.png)

## Paso 5: Configuración de los permisos de los directorios

En el "Administrador de Servidores", selecciona "Herramientas" y luego "Usuarios y Equipos de Active Directory".
Crea los usuarios que necesitarás para acceder al servidor FTP.
Asegúrate de que estos usuarios tengan permisos adecuados en las carpetas del servidor FTP.
Paso 5: Establecer Seguridad Adicional

![Alt text](MyFile_2023-11-13_17-35-31.png)
![Alt text](MyFile_2023-11-13_17-35-03.png)
![Alt text](MyFile_2023-11-13_17-35-38.png)
![Alt text](MyFile_2023-11-13_17-45-26.png)
![Alt text](MyFile_2023-11-13_17-45-33.png)
![Alt text](MyFile_2023-11-13_17-46-08.png)

## Paso 6: Activa el FTP como pasivo y abre los puertos pertinentes

![Alt text](MyFile_2023-11-13_17-58-25.png) ![Alt text](MyFile_2023-11-13_17-58-00.png) ![Alt text](MyFile_2023-11-13_17-58-03.png) ![Alt text](MyFile_2023-11-13_17-58-07.png)

## Paso 7: Activación de SSL/TLS

![Alt text](MyFile_2023-11-13_18-00-52.png) ![Alt text](MyFile_2023-11-13_17-59-58.png) ![Alt text](MyFile_2023-11-13_18-00-15.png) ![Alt text](MyFile_2023-11-13_18-00-28.png) ![Alt text](MyFile_2023-11-13_18-00-42.png)

Para mejorar la seguridad, considera las siguientes medidas:

Configuración de Firewall: Ajusta las reglas de firewall para permitir el tráfico FTP.
Uso de SSL/TLS: Habilita el cifrado mediante SSL/TLS para proteger la transferencia de datos.
Monitoreo de Registro: Configura el registro del servidor FTP para registrar eventos de seguridad.
Actualizaciones y Parches: Mantén tu servidor actualizado con las últimas actualizaciones de seguridad de Microsoft.
Con estos pasos, habrás instalado un servidor FTP en Windows Server, integrado con Active Directory y reforzado con medidas de seguridad. Recuerda realizar pruebas exhaustivas y ajustar la configuración según las necesidades específicas de tu entorno. ¡Ahora tu servidor FTP está listo para proporcionar un acceso seguro y gestionado a tus archivos!
