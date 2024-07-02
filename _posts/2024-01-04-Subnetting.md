---
title: Subnetting
date: 2024-01-09 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Redes Locales]
tags: [redes locales, teoría, tsmr]
img_path: /assets/img/subnetting/
---

# Subnetting

![Alt text](image.png)

Subnetting es el proceso de dividir una red IP en subredes más pequeñas. Una red IP se compone de direcciones IP que se utilizan para identificar dispositivos en la red. Subnetting permite dividir una red grande en segmentos más pequeños, lo que ofrece varios beneficios, como mejorar el rendimiento, facilitar la gestión de la red y proporcionar una mayor seguridad.

Cuando se realiza el subnetting, se toma una red IP y se divide en subredes más pequeñas, cada una con su propio rango de direcciones IP. Esto ayuda a optimizar el tráfico en la red y a reducir la congestión al limitar la cantidad de dispositivos en cada subred.

Además, el subnetting facilita la gestión de direcciones IP al permitir una asignación más eficiente de direcciones a dispositivos específicos en la red. También proporciona una capa adicional de seguridad al aislar segmentos de la red, lo que dificulta la propagación de problemas o ataques a toda la red.

En resumen, subnetting es una técnica que se utiliza para dividir redes IP en subredes más pequeñas con el objetivo de mejorar la eficiencia, la gestión y la seguridad de la red.

## IP 

Una dirección IP, o dirección de Protocolo de Internet, es un identificador único asignado a cada dispositivo conectado a una red que utiliza el protocolo de Internet para la comunicación. Este protocolo es esencial para el funcionamiento de Internet y redes locales.

Hay dos versiones principales de direcciones IP: IPv4 (Protocolo de Internet versión 4) e IPv6 (Protocolo de Internet versión 6). La mayoría de las direcciones IP utilizadas actualmente son de la versión IPv4, que consta de cuatro conjuntos de números separados por puntos (por ejemplo, 192.168.1.1). Sin embargo, debido al agotamiento de direcciones IPv4, se ha implementado gradualmente IPv6, que utiliza una notación hexadecimal y proporciona un espacio de direcciones mucho más amplio.

Las direcciones IP tienen dos funciones principales:

Identificación del host o dispositivo: Cada dispositivo en una red tiene una dirección IP única que lo identifica. Esto permite que los datos se envíen a destinos específicos en la red.

Localización en la red: La dirección IP también se utiliza para determinar la ubicación del dispositivo en la red. La dirección IP está organizada jerárquicamente, lo que significa que se puede identificar la red y la subred a la que pertenece un dispositivo basándose en parte en sus números.

Por lo tanto, una dirección IP es un número único asignado a cada dispositivo en una red para permitir la identificación y la comunicación en el entorno de Internet. Estas direcciones son fundamentales para el enrutamiento de datos a través de la red global.

### Características

Las direcciones IP (Protocolo de Internet) tienen varias características clave que las definen y las distinguen. Aquí hay una explicación de algunas de las características más importantes:

- Unicidad: Cada dirección IP es única en una red determinada en un momento dado. Esto significa que no puede haber dos dispositivos diferentes con la misma dirección IP en la misma red.

- Jerarquía: Las direcciones IP están organizadas en una estructura jerárquica. Hay una parte de la dirección que identifica la red y otra parte que identifica el dispositivo en esa red. Esto facilita el enrutamiento eficiente de datos a través de Internet.

- Versión: Hay dos versiones principales de direcciones IP: IPv4 e IPv6. IPv4 utiliza una notación de cuatro conjuntos de números decimales separados por puntos (por ejemplo, 192.168.1.1), mientras que IPv6 utiliza una notación hexadecimal más larga.

- Direcciones Públicas y Privadas: Las direcciones IP pueden ser públicas o privadas. Las direcciones IP públicas son asignadas por la Autoridad de Asignación de Números de Internet (IANA) y son accesibles desde Internet. Las direcciones IP privadas se utilizan en redes locales y no son directamente accesibles desde Internet.

- Clases y Subredes: En el pasado, las direcciones IP se dividían en clases (A, B, C, etc.), pero ahora se utiliza el concepto de subredes, que permite una asignación más flexible y eficiente de direcciones IP en una red.

- Máscara de Subred: Junto con la dirección IP, se utiliza una máscara de subred para dividir la dirección en parte de red y parte de host. La máscara de subred indica qué parte de la dirección se refiere a la red y qué parte identifica al dispositivo en esa red.

- Dinámicas o Estáticas: Las direcciones IP pueden ser asignadas de manera dinámica por un servidor DHCP (Protocolo de Configuración Dinámica de Host) o de manera estática, donde se configuran manualmente en cada dispositivo.

- Longitud de Dirección: IPv4 utiliza direcciones de 32 bits, mientras que IPv6 utiliza direcciones de 128 bits. IPv6 tiene un espacio de direcciones significativamente más grande, lo que ayuda a abordar la escasez de direcciones IPv4.

- Estas características permiten que las direcciones IP cumplan su función fundamental de identificación y enrutamiento en redes, ya sea en Internet o en redes locales.

### IP públicas vs privadas

Las direcciones IP se dividen en dos categorías principales: direcciones IP públicas y direcciones IP privadas. Estas categorías tienen propósitos y características distintas:

Direcciones IP Públicas:

- Acceso desde Internet: Las direcciones IP públicas son aquellas que son asignadas de manera única a un dispositivo y son accesibles directamente desde Internet. Cada dispositivo conectado a Internet, como servidores web, routers y computadoras, necesita tener una dirección IP pública única.
- Asignación por IANA: La Autoridad de Asignación de Números de Internet (IANA) asigna bloques de direcciones IP públicas a organizaciones regionales y proveedores de servicios de Internet (ISP). Luego, los ISP distribuyen estas direcciones a sus clientes.
- Identificación única global: Las direcciones IP públicas son únicas a nivel mundial y no se pueden repetir en Internet. Permiten que los dispositivos se comuniquen de manera única y se encuentren en la red global.

Direcciones IP Privadas:

- Uso en redes locales: Las direcciones IP privadas se utilizan dentro de redes locales (como hogares, empresas o instituciones) y no son directamente accesibles desde Internet. Permiten la comunicación dentro de la red local, pero los dispositivos con direcciones IP privadas necesitan un router o un dispositivo de red con una dirección IP pública para acceder a Internet.
- Reservadas para uso privado: Hay rangos específicos de direcciones IP reservados para uso privado, como los definidos en los estándares RFC 1918. Ejemplos comunes incluyen direcciones en los rangos 192.168.x.x, 172.16.x.x - 172.31.x.x, y 10.x.x.x.
- Traducción de direcciones de red (NAT): Para permitir que múltiples dispositivos en una red privada compartan una única dirección IP pública para acceder a Internet, se utiliza la traducción de direcciones de red (NAT). El router traduce las direcciones IP privadas a la dirección IP pública antes de enviar datos a través de Internet.

En resumen, las direcciones IP públicas son únicas y accesibles desde Internet, mientras que las direcciones IP privadas se utilizan internamente en redes locales y no son directamente accesibles desde la red global. Se utiliza NAT para permitir que los dispositivos con direcciones IP privadas accedan a Internet a través de una única dirección IP pública.

### Direcciones IP públicas

Las direcciones IP públicas se dividen en bloques de direcciones que son asignados y administrados por la Autoridad de Asignación de Números de Internet (IANA), así como por las organizaciones regionales y proveedores de servicios de Internet (ISP). Aquí hay una explicación de los rangos de direcciones IP públicas principales:

#### Clase A:
Rango:
1.0.0.0 a 126.255.255.255
Notas:
Incluye un gran número de direcciones, pero debido a su tamaño, la mayoría de las asignaciones de Clase A se realizan a organizaciones muy grandes o a gobiernos.
#### Clase B:
Rango:
128.0.0.0 a 191.255.255.255
Notas:
Asignado a organizaciones medianas. Los primeros 16 bits indican la red, y los siguientes 16 bits identifican dispositivos en esa red.
#### Clase C:
Rango:
192.0.0.0 a 223.255.255.255
Notas:
Asignado a organizaciones más pequeñas. Los primeros 24 bits indican la red, y los últimos 8 bits identifican dispositivos en esa red.
Clase D (Direcciones de Multidifusión):
Rango:
224.0.0.0 a 239.255.255.255
Notas:
Reservado para la transmisión de datos a múltiples destinos simultáneamente.
Clase E (Reservado para uso futuro):
Rango:
240.0.0.0 a 255.255.255.255
Notas:
Actualmente reservado para uso futuro y experimentación.
Direcciones de Reserva y Especiales:
Direcciones de Loopback:
127.0.0.0 a 127.255.255.255
Usado para las pruebas locales; cualquier tráfico enviado aquí se redirige al propio dispositivo.
Direcciones de Enlace Local:
169.254.0.0 a 169.254.255.255
Utilizado por el protocolo de configuración automática de direcciones (APIPA) cuando un dispositivo no puede obtener una dirección IP de manera dinámica.
Estos rangos son fundamentales para el funcionamiento de Internet, ya que permiten la identificación única de dispositivos y facilitan el enrutamiento eficiente de los datos a través de la red global. Es importante tener en cuenta que, con el agotamiento de direcciones IPv4, se ha promovido la adopción de IPv6, que utiliza un formato diferente y tiene un espacio de direcciones mucho más grande.

### Direcciones IP privadas

Las direcciones IP privadas están reservadas para su uso en redes locales y no son directamente accesibles desde Internet. Estos rangos están definidos en el RFC 1918 y se utilizan comúnmente en redes domésticas, empresas y otras configuraciones internas. Aquí están los rangos de direcciones IP privadas más comunes:

Clase A Privada:
Rango:

10.0.0.0 a 10.255.255.255
Notas:

Amplio rango de direcciones que se pueden utilizar en redes privadas. Muy flexible y adecuado para organizaciones grandes.
Clase B Privada:
Rango:

172.16.0.0 a 172.31.255.255
Notas:

Este rango permite un número significativo de direcciones para redes medianas. Los primeros 12 bits indican la red, y los siguientes 12 bits identifican dispositivos en esa red.
Clase C Privada:
Rango:

192.168.0.0 a 192.168.255.255
Notas:

Este rango es muy común en redes domésticas y pequeñas empresas. Los primeros 16 bits indican la red, y los últimos 8 bits identifican dispositivos en esa red.
Estos rangos de direcciones IP privadas permiten a las organizaciones implementar redes internas sin preocuparse por conflictos de direcciones IP con dispositivos en Internet. Cuando los dispositivos en una red privada necesitan acceder a Internet, se utiliza la técnica de Traducción de Direcciones de Red (NAT) en el enrutador para traducir las direcciones privadas a una única dirección IP pública proporcionada por el ISP.

Es importante destacar que, aunque estas direcciones están reservadas para uso privado, es esencial planificar y administrar adecuadamente las direcciones IP en una red para evitar conflictos y garantizar una comunicación eficiente entre los dispositivos locales.

```
¿Exista las ip pública 10.0.0.10?
La dirección IP 10.0.0.10 es parte del rango de direcciones IP privadas reservadas para redes locales, conocido como Clase A Privada. Por lo tanto, puede ser utilizada en redes privadas internas, como redes domésticas o empresariales, pero no es una dirección IP pública única y globalmente accesible en Internet.

Si tienes un dispositivo con la dirección IP 10.0.0.10 en tu red local, es perfectamente válido y común. Sin embargo, ten en cuenta que para que los dispositivos con direcciones IP privadas, como esta, accedan a Internet, generalmente se utiliza la técnica de Traducción de Direcciones de Red (NAT) en el enrutador para asignar una única dirección IP pública proporcionada por tu proveedor de servicios de Internet (ISP).
```

## Subnetting
Subnetting, o subdivisión de redes, es el proceso de dividir una red IP en subredes más pequeñas. Este procedimiento se realiza por varias razones, entre las cuales se incluyen la eficiencia en el uso de direcciones IP, el control del tráfico de la red, y la mejora de la seguridad. Al utilizar subnetting, se pueden asignar de manera más eficiente las direcciones IP disponibles, evitando el agotamiento del espacio de direcciones y facilitando la administración de la red.

Aquí hay algunos conceptos clave relacionados con el subnetting:

Dirección IP y Máscara de Subred:

Cada dispositivo en una red tiene una dirección IP única que lo identifica. Además, se utiliza una máscara de subred para dividir la dirección IP en parte de red y parte de host.
Máscara de Subred y Bits de Subred:

La máscara de subred consiste en una serie de unos seguidos de ceros. Los unos indican la parte de red, y los ceros indican la parte de host. La cantidad de unos en la máscara determina la cantidad de bits dedicados a la red. Por ejemplo, en una máscara de subred de 255.255.255.0 (o /24 en notación de prefijo CIDR), hay 24 bits dedicados a la red y 8 bits para los hosts.
División de Subredes:

Al subdividir una red, se toman prestados bits de la parte de host para crear subredes más pequeñas. Por ejemplo, si se toman prestados 2 bits, se pueden crear 4 subredes (2^2 = 4).
Notación CIDR:

La notación CIDR (Classless Inter-Domain Routing) se utiliza para describir direcciones IP y máscaras de subred. Por ejemplo, 192.168.1.0/24 indica una red con una máscara de subred de 24 bits.
Ventajas de Subnetting:

Eficiencia en el uso de direcciones: Permite asignar direcciones IP de manera más eficiente.
Mejora de la seguridad: Facilita la implementación de políticas de seguridad al aislar segmentos de red.
Control del tráfico: Facilita la administración y control del tráfico en la red.
NAT (Traducción de Direcciones de Red):

En muchos casos, cuando se utilizan direcciones IP privadas en una red local, se implementa la NAT para traducir esas direcciones a una única dirección IP pública al acceder a Internet.
Subnetting es una habilidad esencial en la administración de redes, ya que permite una gestión más efectiva de las direcciones IP y proporciona flexibilidad para adaptarse a las necesidades cambiantes de la red.

```
Dividir una red de Clase C mediante subnetting implica tomar la dirección IP de la red y subdividirla en segmentos más pequeños, conocidos como subredes. Aquí os proporcionaré un ejemplo de cómo dividir una red de Clase C (que tiene una máscara de subred por defecto de 255.255.255.0 o /24 en notación CIDR) en subredes más pequeñas.

Supongamos que tienes la dirección de red de Clase C: 192.168.1.0 con una máscara de subred de 255.255.255.0 (/24). Esta red por defecto tiene 256 direcciones IP disponibles (2^8), pero puedes subdividirla en subredes más pequeñas.

Paso 1: Determinar cuántas subredes necesitas:
Decide cuántas subredes necesitas y cuántos hosts necesitas en cada subred. Por ejemplo, podrías necesitar 4 subredes, cada una con capacidad para 60 hosts.

Paso 2: Determinar el número de bits necesarios:
Calcula cuántos bits necesitarás para representar el número de subredes y hosts que deseas en cada subred. En nuestro ejemplo, necesitarías al menos 2 bits para las subredes (2^2 = 4) y 6 bits para los hosts en cada subred (2^6 = 64).

Paso 3: Crear la nueva máscara de subred:
Añade los bits necesarios a la máscara de subred original. En este caso, necesitas 2 bits para las subredes y 6 bits para los hosts. Entonces, la nueva máscara de subred será 255.255.255.192 (/26 en notación CIDR).

Paso 4: Calcular los tamaños y rangos de subred:
Tamaño de cada subred: 2^(Número de bits para hosts) = 64 direcciones IP
Rango de la primera subred: 192.168.1.0 a 192.168.1.63
Rango de la segunda subred: 192.168.1.64 a 192.168.1.127
Rango de la tercera subred: 192.168.1.128 a 192.168.1.191
Rango de la cuarta subred: 192.168.1.192 a 192.168.1.255
Paso 5: Asignar direcciones a las subredes:
Asigna las direcciones IP a las subredes según el rango calculado. Asegúrate de no tener solapamientos y de que cada dirección IP esté correctamente asignada a la subred correspondiente.

Este es un ejemplo básico de cómo podrías dividir una red de Clase C mediante subnetting. En situaciones reales, es posible que desees considerar otros factores, como la expansión futura de la red, el enrutamiento, y la asignación eficiente de direcciones. La práctica y la comprensión de los cálculos son esenciales para llevar a cabo con éxito el subnetting.

```