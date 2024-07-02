---
title: Montaje del servicio FTP
date: 2023-11-06 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Servicios en red]
tags: [redes locales, teoría, smr]
img_path: /assets/img/FTP/Linux/  
---

![Logo de Linux y vsFTP](image.png)

# Introducción

vsftpd, que significa "Very Secure File Transfer Protocol Daemon" (Demonio de Protocolo de Transferencia de Archivos Muy Seguro), es un software de servidor FTP (File Transfer Protocol) de código abierto diseñado para sistemas operativos tipo Unix. Es conocido por su enfoque en la seguridad y el rendimiento, lo que lo convierte en una opción popular para configurar servidores FTP en sistemas Linux y otros sistemas basados en Unix.

1. Seguridad: vsftpd está diseñado con un fuerte énfasis en la seguridad. Ofrece una variedad de características de seguridad, como el soporte para conexiones cifradas (FTP sobre TLS/SSL), el soporte para usuarios virtuales y cárceles chroot para restringir el acceso a directorios específicos, y la capacidad de limitar el número de conexiones concurrentes y el acceso desde direcciones IP específicas.

1. Rendimiento: Es conocido por su velocidad y eficiencia. vsftpd está diseñado para ser ligero y optimizado para un alto rendimiento, lo que lo hace adecuado para manejar un gran número de conexiones concurrentes.

1. Configuración: vsftpd proporciona un sistema de configuración flexible que permite a los administradores personalizar diversos aspectos del comportamiento del servidor FTP. Las opciones de configuración están bien documentadas y se pueden ajustar para satisfacer requisitos específicos.

1. FTP Activo y Pasivo: vsftpd admite tanto los modos FTP activo como pasivo, lo que le permite funcionar con una amplia gama de clientes FTP y configuraciones de red.

1. Aislamiento de Usuarios: Admite el aislamiento de usuarios, lo que puede confinar a los usuarios a sus propios directorios de inicio, mejorando la seguridad al evitar que accedan a otras partes del sistema de archivos del servidor.

1. Registro de Actividad: vsftpd proporciona capacidades detalladas de registro, lo que facilita el monitoreo y la solución de problemas de la actividad del servidor FTP.

1. Soporte IPv6: Admite IPv6, lo que le permite funcionar en infraestructuras de red modernas que utilizan la última versión del Protocolo de Internet.

1. Código Abierto: vsftpd es software de código abierto, y su código fuente está disponible de forma gratuita, lo que significa que se puede personalizar y adaptar a necesidades específicas.

Para instalar y configurar vsftpd en un sistema basado en Unix, generalmente tendrás que editar su archivo de configuración, que a menudo se encuentra en "/etc/vsftpd.conf", y luego iniciar o reiniciar el servicio de vsftpd.

Ten en cuenta que aunque vsftpd es un servidor FTP seguro y confiable, el uso de FTP en general ha perdido popularidad debido a preocupaciones de seguridad. Siempre que sea posible, se recomienda utilizar protocolos de transferencia de archivos más seguros, como SFTP (SSH File Transfer Protocol) o SCP (Copia Segura) para transferencias de archivos a través de la red. Estos protocolos ofrecen cifrado y autenticación por defecto, lo que los convierte en alternativas más seguras al FTP tradicional.

# Instalación del servicio FTP en Ubuntu Server 22.04 LTS

## Cosas necesarias previas a la instalación
- Configuración de MV servidor en red nat
- MV cliente Xubuntu en la misma red nat
- Configuración red nat 192.168.100.0/24

## Instalación y configuración inicial de vsFTP
Con permisos de root ejecutamos el comando:

```console
sudo apt-get install vsftpd
```

Comprobamos que el servicio está activo en su puerto 80:

```console
netstat -putona
```

Otra opción para comprobar que el servicio está activo:

```console
sudo /etc/init.d/vsftpd status
```

Modificamos y añadimos información a nuestro archivo de configuración:
```console
sudo vi /etc/vsftpd.conf
```
```console
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# This directive enables listening on IPv6 sockets. By default, listening
# on the IPv6 "any" address (::) will accept connections from both IPv6
# and IPv4 clients. It is not necessary to listen on *both* IPv4 and IPv6
# sockets. If you want that (perhaps because you want to listen on specific
# addresses) then you must run two copies of vsftpd with two configuration
# files.
listen_ipv6=NO
#
# Allow anonymous FTP? (Disabled by default).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO

#
# Uncomment this to indicate that vsftpd use a utf8 filesystem.
#utf8_filesystem=YES

pasv_enable=YES
pasv_min_port=10000
pasv_max_port=10005
pasv_address=127.0.0.1
```

Reiniciamos el servicio:
```console
sudo vi /etc/init.d/vsftpd restart
```

Realizamos una prueba de que funciona con el cliente FTP WinSCP:
![Alt text](<Captura de pantalla 2023-11-06 231835.png>)
![Alt text](<Captura de pantalla 2023-11-06 231859.png>)

Realizamos una prueba de que funciona con el cliente FTP Filezilla:

![Alt text](<Captura de pantalla 2023-11-06 231939.png>)
![Alt text](<Captura de pantalla 2023-11-06 231943.png>)
![Alt text](<Captura de pantalla 2023-11-06 231959.png>)

## Configuración de usuarios que no sean del sistema

Nos dirigimos al archivo de configuración de VSFTP:
```console
sudo vi /etc/vsftpd.conf
```

Añadimos al final las siguientes líneas:
```console
guest_enable=YES
virtual_use_local_privs=YES
user_sub_token=$USER
local_root=/var/ftp/$USER
chroot_local_user=YES
```

Reiniciamos el demonio y comprobamos:

Vamos a crear un archivo el cual será el que utilizaremos para añadir los usuarios:
```console
sudo vi /etc/virtusers.txt
```

Añadimos el usuario ftpUser1 con su contraseña (es la misma) y ftpUser2 con su contraseña (es la misma)
```console
ftpUser1
passUser1
ftpUser2
passUser2
```

Instalamos db-util para poder trabajar con dichos usuarios:
```console
sudo apt-get install db-util
```

Configuramos los archivos necesarios:
```console
sudo db_load -T -t hash -f /etc/virtusers.txt /etc/virtusers.db
```

Vaciamos el siguientes archivos para que queden de esta forma:
```console
sudo vi /etc/pam.d/vsftpd
```
```console
auth <tab>required <tab>pam_userdb.so db=/etc/virtusers
account <tab>required <tab>pam_userdb.so db=/etc/virtusers
```

```console
sudo mkdir -p /var/ftp/ftpUser1
sudo mkdir -p /var/ftp/ftpUser2
```

Reiniciamos servicio FTP:

Cambiamos permisos:
```console
sudo chown ftp: -R /var/ftp/ftpUser1
sudo chown ftp: -R /var/ftp/ftpUser2
```

Añadimos otra línea al archivo de configuración de vsFTP
```console
allow_writeable_chroot=YES
```

Reiniciamos servicio FTP y comprobamos:

Cliente FileZilla:
![Alt text](<Captura de pantalla 2023-11-06 235213.png>)

Cliente WinSCP:
![Alt text](<Captura de pantalla 2023-11-06 235225.png>)

Situación de los directorios virtuales:
![Alt text](<Captura de pantalla 2023-11-06 235238.png>)

## Ciframos las conexiones

Generamos el certificado:
```console
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/vsftpd.pem -out /etc/ssl/private/vsftpd.pem
```

![Configuración del certificado](image2.png)

Lo establecemos en nuestro archivo de configuración de vsFTP:
```console
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
```

Realizamos las pruebas pertinentes:

![Conexión con WinSCP utilizando conexión cifrada](image3.png)
