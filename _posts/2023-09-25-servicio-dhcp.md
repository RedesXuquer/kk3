---
title: Montaje del servicio DHCP
date: 2023-09-25 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Servicios en red]
tags: [redes locales, teoría, smr]
img_path: /assets/img/dhcp/
image: 
    path: dhcp.jpg
---

# Introducción
El protocolo DHCP es uno de los más utilizados por los routers, tanto domésticos como también profesionales. De manera predeterminada cualquier cliente cableado o WiFi está configurado para obtener una dirección IP por DHCP. Aunque continuamente se está utilizando el DHCP, ¿sabes para qué sirve?

Por más que este protocolo sea tan utilizado, lo cierto es que seguramente no conozcas para qué sirve exactamente. Además de esto, no todo el mundo conoce cada una de sus funcionalidades y también cómo funciona. Entre otros aspectos, también puedes encontrar qué mensajes se intercambian entre el servidor y los clientes. Por eso mismo, en RedesZone puedes encontrar todo lo que debes saber sobre el protocolo DHCP.

# ¿Qué es y para qué sirve este protocolo?
El protocolo DHCP (Protocolo de configuración dinámica de host) o también conocido como «Dynamic Host Configuration Protocol«, es un protocolo de red que utiliza una arquitectura cliente-servidor. Por tanto, tendremos uno o varios servidores DHCP y también uno o varios clientes, que se deberán comunicar entre ellos correctamente para que el servidor DHCP brinde información a los diferentes clientes conectados.

Este protocolo se encarga de asignar de manera dinámica y automática una dirección IP, ya sea una dirección IP privada desde el router hacia los equipos de la red local, o también una IP pública por parte de un operador que utilice este tipo de protocolo para el establecimiento de la conexión.

Cuando tenemos un servidor DHCP en funcionamiento, todas las direcciones IP que ha proporcionado a diferentes clientes se guardan en un listado donde se relaciona la IP que se le ha proporcionado (dirección lógica) y la dirección MAC (dirección física de la tarjeta de red). Gracias a este listado, el servidor DHCP se asegura de no proporcionar a dos equipos diferentes la misma dirección IP, lo que ocasiona un caos en la red local.

A medida que el servidor va asignando direcciones IP, también tiene en cuenta cuándo pasa un determinado tiempo y caducan, quedando libres para que otro cliente pueda obtener esta misma dirección IP. El servidor DHCP sabrá en todo momento quién ha estado en posesión de una dirección IP, cuánto tiempo ha estado, y cuándo se ha asignado a otro cliente.

El protocolo DHCP incluye varias formas de asignación de direcciones IP, dependiendo de la configuración que realicemos y el escenario, podremos usar una forma de asignación u otra:

- Manual o estática: el servidor DHCP nos permitirá configurar un listado de parejas IP-MAC con el objetivo de que siempre se le proporcione a un cliente una determinada dirección IP, y que esta dirección no cambie nunca.
- Automática: el servidor DHCP se encarga de proporcionar una dirección IP al cliente que realiza la solicitud, y estará disponible para este cliente hasta que la libere. Existen routers que internamente están configurados para proporcionar direcciones IP privadas de forma secuencial, sin embargo, hay firmwares que están diseñados para proporcionar una dirección IP específica dentro del rango y que no es secuencial, en base a un algoritmo interno y la dirección MAC que se haya conectado.
- Dinámica: este método permite reutilización dinámica de las direcciones IP.
Aunque el protocolo DHCP es muy conocido por proporcionar la dirección IP, máscara de subred y la puerta de enlace, tres parámetros básicos y fundamentales, también es capaz de proporcionar otra información de cara a los clientes, como los siguientes parámetros que son configurables y opcionales:

- Servidor DNS primario y secundario.
- Nombre DNS.
- MTU para la interfaz.
- Servidor y dominio NIS.
- Servidores NTP.
- Servidor de nombre WINS para Windows.
- Otras opciones avanzadas.

Un aspecto muy importante es que, si un sistema Windows no es capaz de obtener una dirección IP a través del cliente DHCP en una red, se inicia un proceso llamado APIPA (Automatic Private Internet Protocol Addressing). Este proceso APIPA que usan los sistemas operativos cuando no se puede obtener una dirección IP por DHCP, este protocolo se encarga de asignar una dirección IP privada de clase B en el rango 169.254.0.0/16 con su correspondiente máscara de subred 255.255.0.0.

Este bloque de direccionamiento se conoce como «link–local» para redes IPv4. Aunque los sistemas operativos se autoconfigure esta dirección IP privada, cada 5 minutos volverán a consultar si hay un servidor DHCP en la red para que les proporcione una dirección IP privada de clase A, B o C habitual. Cuando no funciona el servidor DHCP o no lo tenemos configurado, podéis comprobar la dirección IP que se configura automáticamente si consultamos la IP privada que tenemos en nuestro equipo.

Una vez que ya conocemos qué es el protocolo DHCP y sus principales características, vamos a ver su funcionamiento y qué mensajes se intercambian.

## Funcionamiento y mensajes de intercambio
La comunicación entre el servidor DHCP y los clientes DHCP que tengamos conectados en la red se realiza a través del protocolo UDP, un protocolo que ya conocemos de otros artículos y que es un protocolo no orientado a conexión. En el caso del servidor DHCP usamos el protocolo UDP puerto 67, en el caso de los clientes usamos el protocolo UDP en el puerto 68. Si tenemos un firewall bloqueando estos puertos, ya sea en el servidor o en el cliente, deberemos revisarlo y añadir una regla de aceptar para origen y/o destino estos puertos, de lo contrario el servicio no funcionará, y no podremos obtener las direcciones IP automáticamente.

![Funcionamiento y mensajes de intercambio](funcionamiento.jpg)
_Funcionamiento y mensajes de intercambio_

Cuando conectamos un equipo por primera vez a la red no tiene direccionamiento IP, por tanto, deberemos «buscar» el servidor DHCP por toda la red, ya que tampoco tenemos información sobre el protocolo ARP en un primer momento. Por este motivo, lo primero que hará el cliente es enviar un DHCP DISCOVERY con dirección IP de origen 0.0.0.0 y dirección IP de destino 255.255.255.255 que es la IP de broadcast global. Por supuesto, se envía un datagrama UDP, con puerto de origen el 68 (cliente) y puerto de destino el 67 (servidor). Esta comunicación es de tipo broadcast en la red, e internamente se puede configurar para recibir el OFFER por broadcast o unicast, aunque generalmente es de tipo unicast en el OFFER.

Si existe un servidor y está funcionando correctamente, le enviará una respuesta llamada DHCP OFFER. Este es el datagrama de respuesta del servidor al cliente ante la petición de obtener parámetros por el protocolo. En este caso la dirección IP de origen será la del propio servidor, que generalmente también actúa de router, la IP de destino será la 255.255.255.255 también, el puerto de origen el 67 y el puerto de destino el 68. En este paquete tendremos la dirección IP privada que se le puede proporcionar y se involucra a la dirección MAC del equipo. Esta comunicación es de tipo unicast generalmente, aunque de forma opcional puede ser broadcast.

Una vez que el cliente recibe el OFFER, le enviará un DHCP REQUEST de vuelta. En este caso el cliente selecciona la configuración recibida por el OFFER y una vez más el cliente solicita la IP que indicó el servidor anteriormente. Esta comunicación también es broadcast, porque todavía no tiene una dirección IP privada válida.

Por último, el servidor le enviará un DHCP ACK al cliente, diciéndole que lo ha recibido correctamente e incluye toda la información que hayamos configurado en el servidor, como la duración de la conexión, información sobre los servidores DNS y más. Con este último proceso se completan todos los pasos del proceso, el protocolo también esperará un cierto tiempo hasta que el cliente DHCP configure su interfaz correctamente con los parámetros negociados. Una vez que el cliente obtiene la dirección IP, el cliente empezará a recibir información del protocolo ARP con todos los equipos que hay en la red local, con el objetivo de prevenir posibles conflictos de direcciones IP o superposición de grupos de direcciones de servidores DHCP. En caso de encontrar algún problema, el cliente enviará al servidor un mensaje DHCPDECLINE indicando que la dirección ya está en uso.

Una vez que hemos visto cómo funciona el protocolo DHCP, vamos a explicar qué ataques existen y cómo evitarlos.

## ¿Implementación del DHCP?

Cuando vemos que una empresa u organización necesita un DHCP, es necesario iniciar un proceso de implementación. Este nos ayudará con la planificación y evaluación de las necesidades que tiene la red, y las que tenemos como usuarios del mismo. Lo primero que se debe tener en cuenta es el servidor en el cual se va a realizar la instalación del DHCP, siendo el responsable de asignar las direcciones IP a todos los clientes. Por lo general, es recomendable instalar el servicio DHCP en servidores dedicados, a pesar de que también se puede hacer en un servidor de archivos o de aplicaciones.

Una vez hemos elegido el servidor, es necesario realizar la configuración adecuada al servicio DHCP. Entre los parámetros a configurar se incluyen los tiempos de asignación de las direcciones, así como las puertas de enlace, direcciones del servidor DNS y la dirección del servidor WINS. También cabe la posibilidad de configurar otras opciones, las cuales dependen del servicio al que elegimos darle uso. Como las direcciones de servicios de impresión o nombres de dominio. Una vez realizada toda la configuración y creado el rango de direcciones IP, se debe implementar el servidor en la red. Esto es algo que puede requerir una configuración específica para routers y switches, de forma que permitan que los clientes tengan comunicación con el servidor DHCP y obtengan así una dirección IP válida.

Después de todo esto, lo más recomendable es contar con un plan de mantenimiento para los servidores DHCP. Esto incluye la supervisión de los registros del servidor, que nos ayudarán a detectar posibles problemas o errores. También serán necesarias las actualizaciones periódicas para la configuración, y para la implementación de medidas de seguridad que nos mantengan protegidos en todo momento contra posibles ataques contra nuestro sistema.

En resumen, implementar un DHCP implica disponer de una planificación cuidadosa. La configuración de todos los parámetros, es algo que nos va a ayudar a que la red sea mucho más eficiente, pero para ello debe ser la adecuada para cada caso. Lo más recomendable, es realizar una documentación adecuada para cada uno de los casos donde se implemente el servidor DHCP. De forma que, si tenemos algún problema, no tengamos que pensar en donde puede estar el origen del mismo.

## Ataques que existen al DHCP

El protocolo DHCP no utiliza ningún tipo de autenticación, por este motivo es muy vulnerable a ataques y existen diferentes tipos de ataques que vamos a poder realizar.

Un ataque muy común es configurar un servidor DHCP no autorizado para proporcionar información «falsa» o «maliciosa» a los clientes. Cuando conectamos un servidor DHCP ilegítimo en una red local que ya tiene un servidor DHCP legítimo, los clientes obtendrán la dirección IP, DNS y demás información al primero que responda. Por este motivo, un usuario malintencionado podría levantar un «Rogue DHCP Server» en la red, para hacerse con el control de las direcciones de varios clientes. Cuando un ciberdelincuente instala un Rogue DHCP, lo hace por varios motivos:

Realizar un ataque de denegación de servicio a la red: si el cliente o los clientes obtienen este direccionamiento, puede «cortar» la conexión a Internet. De esta forma, los clientes no tendrán acceso a Internet ni tampoco a la red local.
Ataque Man in the Middle: al tener el control total sobre el direccionamiento y los servidores DNS, ni siquiera es necesario hacer un ataque ARP Spoofing porque tendremos el control total de toda la red, y podremos reenviar a los clientes a webs maliciosas modificando los servidores DNS de nuestro propio servidor DHCP que acabamos de instalar. Un servidor DHCP ilegítimo puede proporcionar información falsa de servidores DNS a los diferentes clientes. Por supuesto, no solamente accederán a las webs maliciosas, sino que también podrá espiar fácilmente las conexiones porque nosotros seremos el gateway.
Para mitigar este ataque, se debe garantizar que no haya ningún Rogue DHCP en nuestra red local, y ahí entra en juego el «DHCP Snooping» que incorporan los switches. Esta tecnología permite bloquear los mensajes DHCP Offer y DHCP Ack de los puertos donde no esté permitido, es decir, donde no esté el servidor legítimo. De esta forma, aunque al servidor DHCP falso le lleguen los mensajes, nunca podrá contestar y los clientes de la red local permanecerán a salvo. En el siguiente esquema se puede ver cómo funciona el DHCP Snooping:

![DHCP Snooping enable](snooping.jpg)
_DHCP Snooping enable_

Otro ataque muy común a los servidores DHCP, debido a que no tenemos ningún tipo de mecanismo de autenticación de los clientes, es el de realizar decenas de peticiones de direcciones IP, con el objetivo de agotar el almacenamiento de direcciones IP del servidor, al presentar nuevos identificadores de cliente cada vez que se realiza una petición. Esto haría que el servidor «colapse» y no pueda proporcionar más direccionamiento. Existen algunos mecanismos de mitigación, sobre todo a nivel de operadores de Internet que hacen uso de DHCP, como la RFC3046 usando etiquetas la cual se usa como un token de autorización, también tenemos la RFC3118 que es para autenticar los mensajes pero que no se ha usado ampliamente. Con el lanzamiento del protocolo 802.1X para autenticar a los clientes cableados, se dejó en un segundo plano estos RFC.

Sea cual sea el ataque, quién lo ocasione debe tener acceso a la red para que este pueda abusar de este protocolo. Por eso es recomendable tomar ciertas medidas de seguridad que nos permita llevarlo a cabo con garantías. De cara a la red local lo más importante es tener bien configurado el DHCP Snooping para evitar los Rogue DHCP, de esta forma, estaremos protegidos.

## Seguridad con DHCP Snooping
DHCP Snooping es una función de seguridad que trabaja en el segundo nivel del modelo OSI. Esta se encuentra integrada en el dispositivo el cual conecta los clientes con el servidor. Su trabajo será verificar toda la información que pasa a través del conmutador, de forma que solo los paquetes que él apruebe y provengan de un servidor de confianza, se enviarán a los clientes.

Para tener garantías de que solo los servidores correctos puedan interferir en la información que recibimos o enviamos, el DHCP Snooping utiliza varios pasos. Lo primero que tendremos que hacer es especificar un puerto seguro para nuestros dispositivos, y todo lo que entre por otro puerto que no sea el asignado, se considerará inseguro. Por lo cual, este bloqueará el envío y el cliente no recibirá nunca esa información.

Este tipo de protección y solo en algunos dispositivos, puede ayudarnos generando un informe de defensa que luego se pueden analizar. Nos distinguirá diferentes errores. Primero tendremos la discrepancia entre la dirección MAC y la información que se encuentre almacenada en la base de datos. Y, por otro lado, nos informará de todos los paquetes que fueron enviados desde un puerto no seguro. Esto puede estar más orientado a un nivel profesional, pero las funcionan se pueden usar en un entorno más privado como una casa.

Debemos tener en cuenta, que de todos los errores que nos podamos encontrar, muchos pueden deberse a ciertas circunstancias de la red que generan errores por mala configuración, estos no suelen ser motivo de mucha preocupación más allá de configurarlo todo correctamente. Por otro lado, si existen errores que pueden significar que se está intentando ejecutar alguna acción que puede ser de dudosa legalidad, como, por ejemplo, alguien que esté intentando entrar en nuestra red de forma deliberada.

Tal y como habéis visto, el protocolo DHCP es ampliamente utilizado por todos nosotros para obtener el direccionamiento IP y otra información necesaria para el buen funcionamiento de la red local, además, no debemos olvidar los ataques y cómo podemos protegernos de ellos, finalmente, recordad que tenemos la funcionalidad de Static DHCP para que el servidor siempre nos proporcione la misma dirección IP.

# Instalación del servicio en Ubuntu Server 22.04 LTS

## Cosas necesarias previas a la instalación
- Configuración de MV servidor en red nat
- MV cliente Xubuntu en la misma red nat (Configuración interna seleccionada DHCP)
- Configuración red nat 192.168.100.0/24

Con permisos de root ejecutamos el comando:

```console
sudo apt-get install isc-dhcp-server
```

Comprobamos que el servicio está activo en su puerto 67:

```console
netstat -putona
```

Tras completar la instalación del servidor vamos a definir la interfaz de red sobre la que funcionará el servidor DHCP. Para este laboratorio de ejemplo será *enp0s3*, por lo que declaramos esta interfaz de IPv4:

```console
sudo vi /etc/default/isc-dhcp-server
```

```console
INTERFACESV4="enp0s3"
INTERFACESV6=""
```

Lo siguiente es configurar nuestro DHCP, para ello vamos a */etc/dhcp* y editamos el fichero *dhcpd.conf*

```console
sudo vi /etc/dhcp/dhcpd.conf
```

```console
#Declaramos la dirección de red y la máscara de nuestro DHCP
subnet 192.168.100.0 netmask 255.255.255.0 {
  #Definimos el rango de direcciones que va a dar nuestro DHCP
  range 192.168.100.100 192.168.100.110;
  #Definimos los servidores DNS's
  option domain-name-servers 8.8.8.8, 8.8.4.4;
  #Definimos la máscara de red
  option subnet-mask 255.255.255.0;
  #Definimos la dirección de la puerta de enlace
  option routers 192.168.100.1;
  #Definimos la dirección de broadcast
  option broadcast-address 192.168.100.255;
  #Tiempo por defecto en que la concesión de la IP es valida.
  default-lease-time 600;
  #Tiempo máximo que se permite asignar a una concesión de dirección IP.
  max-lease-time 7200;
  }
```

Podemos comprobar la sintaxis con:

```console
dhcpd -t -cf /etc/dhcp/dhcpd.conf
```
De ser errónea nos mostrara el punto donde se encontró el error, este sería el output que se recibe si no hay fallos de sintaxis:

Tras esta configuración solo queda reiniciar el servidor y comprobar que se encuentra en buen estado:

```console
service isc-dhcp-server restart
service isc-dhcp.server status
```

## Comprobación con VM cliente Xubuntu
En una máquina cliente Xubuntu vamos a las propiedades de red IPv4 y marcamos la opción para que asigne los parámetros de red automáticamente, tras eso podemos hacer un *ip a* para verificar que nos ha dado una IP del rango que hemos definido en la configuración del DHCP.

```console
ip a
```

## Extras
Para ver la lista de hosts conectados al servidor dhcp podemos ejecutar:
```console
watch dhcp-lease-list
```
Dentro del archivo de configuración del DHCP
```console
sudo vi dhcpd.conf
```
```console
host WinClient1{
  #Dirección MAC del equipo
  hardware ethernet 00:11:22:33:44:99;
  #Dirección IP fija 
  fixed-address 192.168.100.240;
}
```
```console
host WinClient1{
  #Dirección MAC del equipo
  hardware ethernet 00:11:22:33:44:99;
  #Denegación de darle una IP
  deny booting;
}
```

```console
#Declaramos la dirección de red y la máscara de nuestro DHCP
subnet 192.168.100.0 netmask 255.255.255.0 {
  #Definimos el rango de direcciones que va a dar nuestro DHCP
  range 192.168.100.100 192.168.100.110;
  #Definimos los servidores DNS's
  option domain-name-servers 8.8.8.8, 8.8.4.4;
  #Definimos la máscara de red
  option subnet-mask 255.255.255.0;
  #Definimos la dirección de la puerta de enlace
  option routers 192.168.100.1;
  #Definimos la dirección de broadcast
  option broadcast-address 192.168.100.255;
  #Tiempo por defecto en que la concesión de la IP es valida.
  default-lease-time 600;
  #Tiempo máximo que se permite asignar a una concesión de dirección IP.
  max-lease-time 7200;
  group{
    host WinClient1{
      #Dirección MAC del equipo
      hardware ethernet 33:44:88:00:11:22;
      #Dirección IP fija 
      fixed-address 192.168.100.240;
    }

    host WinClient2{
      #Dirección MAC del equipo
      hardware ethernet 00:11:22:33:44:99;
      #Denegación de darle una IP
      deny booting;
    }
  }
  }
```

# Instalación del servicio en Windows Server 2012 R2

Estando en panel principal del servidor nos dirigimos a *administrar -> Agregar roles y características*
![Capura 1](Captura_de_pantalla_2023-10-01_201226.png)
_Captura 1 instalación DHCP en Windows_

En el *asistente para agregar roles y características* le damos a siguiente (es una buena opción darle a la opción de omitir... para que no vuelva a salir la primera pantalla) 
![Capura 2](Captura_de_pantalla_2023-10-01_201918.png)
_Captura 2 instalación DHCP en Windows_

Seleccionamos *instalación basada en características o en roles*
![Capura 3](Captura_de_pantalla_2023-10-01_201934.png)
_Captura 3 instalación DHCP en Windows_

Configuración por omisión y *siguiente*
![Capura 4](Captura_de_pantalla_2023-10-01_201945.png)
_Captura 4 instalación DHCP en Windows_

Seleccionamos *servidor DHCP*
![Capura 5](Captura_de_pantalla_2023-10-01_202008.png)
_Captura 5 instalación DHCP en Windows_

Seleccionamos *agregar carcaterística*
![Capura 6](Captura_de_pantalla_2023-10-01_202018.png)
_Captura 6 instalación DHCP en Windows_

Seleccionamos *siguiente*
![Capura 7](Captura_de_pantalla_2023-10-01_202028.png)
_Captura 7 instalación DHCP en Windows_

Configuración por omisión y *siguiente*
![Capura 8](Captura_de_pantalla_2023-10-01_202059.png)
_Captura 8 instalación DHCP en Windows_

Seleccionamos *siguiente*
![Capura 9](Captura_de_pantalla_2023-10-01_202110.png)
_Captura 9 instalación DHCP en Windows_

Seleccionamos *instalar*
![Capura 10](Captura_de_pantalla_2023-10-01_202122.png)
_Captura 10 instalación DHCP en Windows_

Esperamos durante la instalación...
![Capura 11](Captura_de_pantalla_2023-10-01_202131.png)
_Captura 11 instalación DHCP en Windows_

Una vez terminamos de instalar DHCP vamos a configurar el servicio en *Herramientas -> DHCP*
![Capura 12](Captura_de_pantalla_2023-10-01_202235.png)
_Captura 12 instalación DHCP en Windows_

Con el botón derecho del ratón presionamos sobre IPv4 y *ámbito nuevo*
![Capura 13](Captura_de_pantalla_2023-10-01_202303.png)
_Captura 13 instalación DHCP en Windows_

Rellenamos *Nombre y Descripción*
![Capura 14](Captura_de_pantalla_2023-10-01_202341.png)
_Captura 14 instalación DHCP en Windows_

Seleccionamos el rango de Ip's y máscara
![Capura 15](Captura_de_pantalla_2023-10-01_202401.png)
_Captura 15 instalación DHCP en Windows_

En esta venta configuramos si queremos excluir alguna o algunas IP's
![Capura 16](Captura_de_pantalla_2023-10-01_202422.png)
_Captura 16 instalación DHCP en Windows_

Tiempo de duración máxima que se asigna una Ip a un dispositivo
![Capura 17](Captura_de_pantalla_2023-10-01_202454.png)
_Captura 17 instalación DHCP en Windows_

Continuamos con las algunas configuraciones extras
![Capura 18](Captura_de_pantalla_2023-10-01_202504.png)
_Captura 18 instalación DHCP en Windows_

Introducimos la *Puerta de enlace*
![Capura 19](Captura_de_pantalla_2023-10-01_202522.png)
_Captura 19 instalación DHCP en Windows_

Configuración por omisión y *siguiente*
![Capura 20](Captura_de_pantalla_2023-10-01_202534.png)
_Captura 20 instalación DHCP en Windows_

Introducimos *Servidores WINS*
![Capura 21](Captura_de_pantalla_2023-10-01_202544.png)
_Captura 21 instalación DHCP en Windows_

Activamos el servicio...
![Capura 22](Captura_de_pantalla_2023-10-01_202554.png)
_Captura 22 instalación DHCP en Windows_

Comprobamos que el servicio a dado la IP 100 a nuestro cliente Xubuntu
![Capura 23](Captura_de_pantalla_2023-10-01_202834.png)
_Captura 23 instalación DHCP en Windows_

- [Información de la configuración en el server Ubuntu](https://infotips.es/redes/servidor-dhcp-en-ubuntu-server-22-04-lts/)
- [Qué es el DHCP, funcionamiento y ejemplos de configuración](https://www.redeszone.net/tutoriales/internet/que-es-protocolo-dhcp/)