---
title: NextCloud
date: 2024-01-15 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Servicios en red]
tags: [redes locales, teoría, smr]
img_path: /assets/img/nextcloud/
---

# NextCloud

Nextcloud es una plataforma de software de código abierto que ofrece una amplia gama de servicios en la nube para individuos, empresas y organizaciones. Fundada como un proyecto derivado de ownCloud en 2016, Nextcloud se centra en proporcionar una solución de almacenamiento y colaboración en línea que pone énfasis en la privacidad, la seguridad y la autonomía del usuario.

Una de las características fundamentales de Nextcloud es su capacidad para gestionar el almacenamiento de archivos en la nube. Permite a los usuarios almacenar, sincronizar y compartir archivos desde diversos dispositivos, facilitando el acceso a la información desde cualquier lugar con conexión a Internet. La plataforma proporciona aplicaciones nativas para la gestión de archivos, lo que incluye funciones de versionado, compartición de enlaces y la capacidad de colaborar en documentos en tiempo real.

Además del almacenamiento de archivos, Nextcloud ofrece una serie de aplicaciones adicionales que abarcan diversas áreas de la productividad y la colaboración. Incluye un sistema de calendario que permite la gestión de eventos y recordatorios, así como una libreta de direcciones para administrar contactos. La funcionalidad de colaboración en documentos se realiza a través de una suite de oficina en línea que permite a los usuarios trabajar simultáneamente en documentos, hojas de cálculo y presentaciones.

En términos de seguridad y privacidad, Nextcloud ofrece numerosas características para garantizar que los datos de los usuarios estén protegidos. Esto incluye la capacidad de cifrar archivos, autenticación de dos factores, control de acceso basado en roles y opciones avanzadas de configuración de seguridad.

Una ventaja clave de Nextcloud es su capacidad para ser autohospedado. Esto significa que los usuarios tienen la opción de instalar y gestionar Nextcloud en sus propios servidores, brindándoles un control total sobre su infraestructura en la nube. Esta autonomía se alinea con la filosofía de empoderar a los usuarios para que tengan control sobre sus propios datos, en contraste con depender de servicios en la nube externos.

En resumen, Nextcloud es una solución completa de servicios en la nube de código abierto que abarca desde el almacenamiento de archivos hasta la colaboración en línea, poniendo énfasis en la seguridad, la privacidad y la capacidad de autogestión por parte de los usuarios.

## Algunas de las características clave de Nextcloud incluyen:

**Almacenamiento de archivos**: Permite a los usuarios almacenar, sincronizar y compartir archivos en la nube. Puedes acceder a tus archivos desde cualquier lugar con conexión a Internet.

**Calendario y contactos**: Proporciona aplicaciones de calendario y libreta de direcciones para gestionar tus eventos y contactos.

**Colaboración en documentos**: Ofrece herramientas para colaborar en documentos en línea, similar a otras suites de productividad en la nube.

**Seguridad**: Se enfoca en la seguridad y privacidad, permitiendo a los usuarios tener control sobre sus datos y cómo se almacenan y comparten.

**Extensibilidad**: Nextcloud es altamente extensible con la posibilidad de agregar más aplicaciones y funcionalidades a través de complementos.

**Autogestión**: Puedes instalar y gestionar Nextcloud en tus propios servidores, dándote un mayor control sobre tu infraestructura en la nube.

## ¿Qué es Snap?

**Definición**: Snap es un formato de paquete de software y un sistema de distribución de aplicaciones desarrollado por Canonical, la empresa detrás de Ubuntu Linux.

### Características:

Independencia del Sistema: Los paquetes Snap están diseñados para ser independientes del sistema operativo subyacente. Esto significa que una aplicación Snap incluye todas sus dependencias, reduciendo la posibilidad de conflictos y mejorando la portabilidad entre diferentes versiones y distribuciones de Linux.

Encapsulación de Dependencias: Una aplicación Snap lleva consigo todas las bibliotecas y dependencias necesarias para su ejecución, eliminando la necesidad de depender en gran medida de las bibliotecas del sistema.

Actualizaciones Automáticas: Los paquetes Snap admiten actualizaciones automáticas, lo que significa que las aplicaciones pueden mantenerse actualizadas sin intervención del usuario.

Aislamiento: La tecnología de Snap permite el aislamiento de aplicaciones, lo que mejora la seguridad al limitar el acceso de una aplicación a partes del sistema.

Ventajas:

Facilidad de Distribución: La encapsulación de dependencias y la independencia del sistema facilitan la distribución de aplicaciones, ya que los desarrolladores pueden crear paquetes Snap que funcionen en varias distribuciones de Linux sin modificaciones significativas.

Seguridad y Estabilidad: El aislamiento de aplicaciones contribuye a la seguridad y estabilidad del sistema, ya que las aplicaciones Snap no afectan directamente a otras partes del sistema.

En resumen, en el contexto de paquetes de software, "Snap" se refiere a un formato de paquete diseñado para simplificar la distribución, instalación y actualización de aplicaciones en entornos Linux, con un énfasis en la independencia del sistema y la seguridad.

## Instalación en Linux

Un primer paso que necesitamos sería instalar snap:
```
sudo apt update && sudo apt upgrade -y && sudo apt install snapd -y
``` 

Para descargar el paquete snap de Nextcloud e instalarlo en el sistema:
```
sudo snap install nextcloud
``` 

El paquete de Nextcloud se descargará e instalará en su servidor. Puede confirmar que el proceso de instalación se realizó correctamente al enumerar los cambios asociados con el paquete snap:

```
snap changes nextcloud
```

Si desea obtener más información sobre el snap de Nextcloud, hay algunos comandos que pueden ser útiles.

El comando snap info puede mostrarle la descripción, los comandos de administración de Nextcloud disponibles, así como la versión instalada y el canal de snap al que se realiza el seguimiento:
```
snap info nextcloud
```

Los snaps pueden definir las conexiones con las que son compatibles, que constan de una ranura y un conector que, al combinarse, permiten que los snaps accedan a ciertas capacidades o niveles de acceso. Por ejemplo, los snaps que deben actuar como cliente de red deben tener la conexión network. Para ver qué conexiones de snap define este snap, escriba:
```
snap connections nextcloud
```

Para obtener información sobre todos los servicios y aplicaciones específicos que proporciona este snap, puede consultar el archivo de definición del snap escribiendo lo siguiente:
```
cat /snap/nextcloud/current/meta/snap.yaml
```

Una vez instalado parece ser requisito ejecutar el siguiente comando el cual instala y nos crea el usuario (tarda un poco):
```
sudo nextcloud.manual-install usuario contraseña
```

## Ajustar los dominios de confianza

Cuando se instala desde la línea de comandos, Nextcloud restringe los nombres de host a los que la instancia responderá. Por defecto, el servicio solo responde a las solicitudes realizadas al nombre de host “localhost”. Accederemos a Nextcloud a través del nombre de dominio o dirección IP del servidor, de modo que tendremos que configurar este ajuste para que acepte estos tipos de solicitudes.

Puede ver los ajustes actuales consultando el valor de la matriz trusted_domains:
```
sudo nextcloud.occ config:system:get trusted_domains
```

Actualmente, solo localhost está presente como el primer valor en la matriz. Podemos añadir una entrada para el nombre de dominio o dirección IP de nuestro servidor escribiendo lo siguiente:
```
sudo nextcloud.occ config:system:set trusted_domains 1 --value=example.com
```

Si consultamos de nuevo los dominios de confianza, veremos que, ahora, tenemos dos entradas:
```
sudo nextcloud.occ config:system:get trusted_domains
```
