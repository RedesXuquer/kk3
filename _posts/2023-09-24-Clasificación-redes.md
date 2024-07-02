---
title: Introducción a las redes locales
date: 2022-05-16 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Redes Locales]
tags: [redes locales, binario, decimal, hexadecimal, tsmr]
img_path: /assets/img/binario/
image: 
    path: binario.jpg
---

---
title: Clasificación de las redes
date: 2023-09-25 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Redes Locales]
tags: [redes locales, teoría, smr]
img_path: /assets/img/topologias/
image: 
    path: diagrama-topologia-de-red-en-arbol.webp 
---
# Introducción:

Las infraestructuras de red pueden variar en gran medida en términos de:

- El tamaño del área que abarcan.
- La cantidad de usuarios conectados.
- La cantidad y los tipos de servicios disponibles.
- El área de responsabilidad.

Los dos tipos más comunes de infraestructuras de red son las redes de área local (LAN) y las redes de área amplia (WAN). Una LAN es una infraestructura de red que proporciona acceso a usuarios y dispositivos finales en un área geográfica pequeña. Normalmente, una LAN se utiliza en un departamento dentro de una empresa, un hogar o una red de pequeñas empresas. Una WAN es una infraestructura de red que proporciona acceso a otras redes en un área geográfica amplia, que generalmente es propiedad y está administrada por una corporación más grande o un proveedor de servicios de telecomunicaciones.

# LAN

Una red LAN, o Red de Área Local, es un conjunto de dispositivos de comunicación interconectados dentro de un área geográfica limitada, como un edificio, una escuela, una empresa u otro espacio relativamente pequeño. Estas redes están diseñadas para permitir que los dispositivos, como ordenadores, impresoras, teléfonos y otros dispositivos electrónicos, se comuniquen y compartan recursos de manera eficiente y rápida.

## 1. Propósito de una LAN:

- Compartir recursos: Las LAN permiten compartir recursos como impresoras, archivos, conexiones a internet y dispositivos de almacenamiento entre varios dispositivos conectados a la red. Esto reduce la duplicación de recursos y facilita el acceso a los mismos.

- Comunicación: Las LAN permiten la comunicación instantánea entre dispositivos conectados. Esto es crucial en un entorno empresarial para el intercambio de información y la colaboración entre empleados.

- Acceso a internet: Las LAN suelen proporcionar acceso compartido a internet para todos los dispositivos conectados, lo que permite a los usuarios acceder a recursos en línea y servicios basados en la web.

- Centralización de servicios: Algunas LAN también pueden centralizar servicios como autenticación, seguridad y almacenamiento de datos, lo que facilita la gestión de la red y la aplicación de políticas de seguridad.

## 2. Componentes de una LAN:

- Dispositivos finales: Estos son los dispositivos que se conectan a la red, como ordenadores, portátiles, tablets, teléfonos, impresoras y otros dispositivos electrónicos.

- Dispositivos de red: Estos incluyen routers, switches y puntos de acceso inalámbrico (APs). Los enrutadores conectan la LAN a otras redes, como internet. Los switches se utilizan para conectar los dispositivos finales entre sí en la LAN, mientras que los APs permiten conexiones inalámbricas.

- Medios de transmisión: Los medios de transmisión son los cables o conexiones inalámbricas que permiten la comunicación entre dispositivos. Los cables Ethernet son comunes en las LAN con cable, mientras que las LAN inalámbricas utilizan ondas de radio para la comunicación.

## 3. Topologías de LAN:
Las redes LAN pueden tener diferentes topologías, que se refieren a la forma en que los dispositivos están conectados físicamente. Algunas topologías comunes incluyen:

- Estrella: Todos los dispositivos están conectados a un centro, como un conmutador o un enrutador. Si un dispositivo necesita comunicarse con otro, la información pasa a través del centro.

- Bus: Todos los dispositivos están conectados a un solo cable, llamado bus. La información se envía a través del bus y todos los dispositivos pueden escucharla, pero solo el destinatario adecuado la procesa.

- Anillo: Los dispositivos están conectados en un círculo cerrado, donde la información circula en una dirección constante. Cada dispositivo recibe y retransmite la información.

## 4. Protocolos y estándares:
- Las LAN utilizan protocolos y estándares para garantizar que los dispositivos puedan comunicarse entre sí. Algunos ejemplos de protocolos comunes en una LAN incluyen TCP/IP (para la comunicación en internet), Ethernet (para la transmisión de datos en redes con cable) y Wi-Fi (para redes inalámbricas).

## 5. Seguridad y administración:
- La seguridad es un aspecto crítico en la gestión de una LAN. Se utilizan medidas como cortafuegos, sistemas de detección de intrusiones, autenticación de usuarios y cifrado de datos para proteger la red contra amenazas externas e internas. La administración de la LAN implica la configuración, el monitoreo y el mantenimiento de los dispositivos y recursos para garantizar un funcionamiento óptimo.

En resumen, una red LAN es un componente fundamental en entornos empresariales y domésticos para facilitar la comunicación y el intercambio de recursos entre dispositivos dentro de un área geográfica limitada. Proporciona la base para la conectividad de dispositivos y el acceso a servicios en línea, y su diseño y gestión son esenciales para garantizar un funcionamiento eficiente y seguro.

# MAN

Una red MAN (Metropolitan Area Network, por sus siglas en inglés) es un tipo de red de comunicación que abarca un área geográfica metropolitana o una ciudad. Es una red intermedia entre las redes de área local (LAN) que cubren áreas pequeñas, como edificios o campus, y las redes de área amplia (WAN) que abarcan áreas geográficas extensas, como regiones, países o continentes.

## 1. Propósito y Alcance de una MAN:

- Cobertura Metropolitana: La principal característica de una MAN es que abarca una zona geográfica más grande que una LAN pero más pequeña que una WAN. Esta área suele ser una ciudad o una región metropolitana.

- Conexión de Áreas Urbanas: Las MAN se utilizan para interconectar diferentes ubicaciones dentro de una ciudad o una región metropolitana. Esto permite la comunicación y el intercambio de datos entre sitios que pueden estar a varios kilómetros de distancia.

- Soporte de Aplicaciones Urbanas: Las MAN son útiles para respaldar aplicaciones específicas de áreas metropolitanas, como servicios de videoconferencia, transmisión de datos a alta velocidad, sistemas de vigilancia y acceso a internet de alta velocidad para empresas y usuarios.

## 2. Componentes de una MAN:

- Enrutadores y Dispositivos de Red: Al igual que en las LAN y WAN, los routers desempeñan un papel fundamental en una MAN. Dirigen el tráfico de datos entre diferentes ubicaciones de la red y determinan la mejor ruta para que los datos lleguen a su destino.

- Fibra Óptica y Otros Medios de Transmisión: Dado que las MAN suelen cubrir distancias más largas que las LAN, a menudo utilizan medios de transmisión de alta velocidad, como cables de fibra óptica, para transmitir datos de manera eficiente a través de la ciudad.

- Tecnologías de Acceso: Las MAN pueden utilizar una variedad de tecnologías de acceso, como Ethernet metropolitano, redes de fibra óptica, redes de área amplia inalámbrica y otros métodos para conectar ubicaciones remotas.

## 3. Topologías y Diseño de una MAN:

- Topología de Anillo: En una MAN, una topología de anillo es común, donde las ubicaciones se conectan en un círculo cerrado. Esto proporciona redundancia y tolerancia a fallos, ya que si un enlace falla, los datos pueden seguir circulando en la otra dirección.

- Topología de Estrella: También es posible utilizar una topología de estrella, donde todas las ubicaciones se conectan a un punto central de la red, como un nodo principal o un centro de datos.

## 4. Seguridad y Administración:

- Seguridad: Al igual que en otras redes, la seguridad es un aspecto crítico de las MAN, ya que transmiten datos a través de áreas urbanas densamente pobladas. Se implementan medidas de seguridad, como cortafuegos, sistemas de detección de intrusiones y autenticación, para proteger la red y los datos transmitidos.

- Administración y Supervisión: La administración de una MAN implica la configuración y el monitoreo continuo de dispositivos de red, la gestión del ancho de banda y la implementación de políticas de seguridad en toda la red metropolitana.

## 5. Ejemplos de MAN:

- Metro Ethernet: Es un ejemplo común de una MAN que utiliza tecnología Ethernet para proporcionar servicios de comunicación de alta velocidad en áreas metropolitanas.

- Redes de Telecomunicaciones: Las redes de telefonía móvil y las redes de acceso a internet de alta velocidad en áreas metropolitanas son ejemplos de MAN que ofrecen servicios de comunicación a los usuarios urbanos.

- Redes de Transporte Público: Algunas ciudades utilizan MAN para supervisar y gestionar sistemas de transporte público, como sistemas de trenes o autobuses.

En resumen, una red MAN es un tipo de infraestructura de comunicación que conecta ubicaciones dentro de una ciudad o una región metropolitana, permitiendo la comunicación y el intercambio de datos a distancias metropolitanas. Estas redes son fundamentales para respaldar aplicaciones urbanas y proporcionar servicios de comunicación eficientes en áreas densamente pobladas.

# WAN

Una red WAN, o Red de Área Amplia (Wide Area Network, en inglés), es un tipo de red de comunicación que abarca un área geográfica extensa, generalmente a nivel regional, nacional o incluso internacional. A diferencia de las redes LAN (Redes de Área Local), que se limitan a un espacio geográfico pequeño, las WAN conectan múltiples LAN dispersas geográficamente para permitir la comunicación y el intercambio de datos a larga distancia.

## 1. Propósito y Alcance de una WAN:

- Conexión de ubicaciones remotas: El propósito principal de una WAN es conectar diferentes ubicaciones geográficas, como oficinas, sucursales, campus universitarios o filiales de una empresa, que pueden estar separadas por grandes distancias geográficas.

- Comunicación a larga distancia: Las WAN permiten la comunicación y el intercambio de datos entre ubicaciones distantes, lo que facilita la colaboración, el acceso a recursos compartidos y la transmisión de información crítica entre lugares lejanos.

- Acceso a recursos centralizados: A través de una WAN, las sucursales pueden acceder a recursos centralizados, como bases de datos, servidores de correo electrónico y sistemas de gestión empresarial, ubicados en la sede principal de la organización.

## 2. Componentes de una WAN:

- Routers y Enrutadores: Los routers son dispositivos clave en una WAN. Se utilizan para dirigir el tráfico de datos entre diferentes ubicaciones de la red, determinando la mejor ruta para que los datos lleguen a su destino.

- Circuitos y Líneas de Comunicación: Las WAN suelen utilizar líneas de comunicación de alta velocidad, como líneas telefónicas dedicadas, líneas de fibra óptica, conexiones satelitales o conexiones de Internet de banda ancha para transmitir datos a larga distancia.

- Protocolos WAN: Para garantizar la interoperabilidad entre diferentes dispositivos y tecnologías de red en una WAN, se utilizan protocolos WAN estándar, como el Protocolo de Internet (IP) y el Protocolo de Control de Transmisión (TCP).

## 3. Topologías y Diseño de una WAN:

- Topología de Estrella: En una WAN, una topología de estrella es común, donde todas las ubicaciones remotas se conectan a una ubicación central (a menudo la sede principal de la organización).

- Topología de Malla: En una topología de malla, cada ubicación remota se conecta directamente con todas las demás ubicaciones remotas, lo que proporciona redundancia y una mayor tolerancia a fallos.

- Tecnologías de Acceso: Las WAN pueden utilizar una variedad de tecnologías de acceso, como líneas contratadas, conexiones VPN (Redes Privadas Virtuales) a través de Internet, conexiones satelitales o conexiones de fibra óptica, dependiendo de la disponibilidad y los requisitos de velocidad.

## 4. Seguridad y Administración:

- Seguridad: Debido a que las WAN transmiten datos a larga distancia, la seguridad es fundamental. Se implementan medidas de seguridad, como firewalls, cifrado de datos y autenticación, para proteger la confidencialidad y la integridad de los datos transmitidos.

- Administración y Supervisión: La administración de una WAN implica la configuración y el monitoreo continuo de los dispositivos de red, la resolución de problemas, la gestión del ancho de banda y la implementación de políticas de seguridad en todas las ubicaciones remotas.

## 5. Ejemplos de WAN:

- Internet: La World Wide Web es un ejemplo masivo de una WAN que conecta usuarios y organizaciones de todo el mundo.

- Redes Corporativas: Empresas con múltiples sucursales utilizan WAN para conectar sus oficinas y permitir la transferencia de datos y la comunicación en tiempo real entre ellas.

- Redes de Telefonía: Las redes de telefonía móvil y las redes de telefonía fija utilizan WAN para conectar torres de telefonía y centrales telefónicas en todo un país o región.

En resumen, una red WAN es una infraestructura de comunicación esencial que conecta ubicaciones geográficamente dispersas, facilitando la comunicación y el intercambio de datos a larga distancia. Estas redes son vitales para empresas, organizaciones y la conectividad global en la era digital.

# Otras redes:

- LAN inalámbrica (WLAN): Wireless Local Area Network – son similares a las LAN, solo que interconectan de forma inalámbrica a los usuarios y los extremos en un área geográfica pequeña.
- Red de área de almacenamiento (SAN): Storage Area Network – son infraestructuras de red diseñadas para admitir servidores de archivos y proporcionar almacenamiento, recuperación y replicación de datos.
- Red de área Personal (PAN): PAN – Personal Area Network – es definitivamente el tipo más pequeño de red que puede usar actualmente y el nombre proviene de la red de área personal. Probablemente haya usado esto en la última semana sin siquiera saberlo. Es la red interconectada de dispositivos tecnológicos al alcance de una persona individual, pero generalmente limitada a un alcance de 10 metros como máximo.

# El Internet

Internet es una colección global de redes interconectadas (internetworks o internet para abreviar). En la figura se muestra una forma de ver a la Internet como una colección de LAN y WAN interconectadas.

Algunos de los ejemplos de LAN están conectados entre sí a través de una conexión WAN. Las WAN se conectan entre sí. Las líneas de conexión WAN rojas representan todas las variedades de formas en que conectamos las redes. Las WAN pueden conectarse a través de cables de cobre, cables de fibra óptica y transmisiones inalámbricas (no se muestran).

Asegurar una comunicación efectiva a través de esta infraestructura diversa requiere la aplicación de tecnologías y estándares consistentes y comúnmente reconocidos, así como la cooperación de muchas agencias de administración de redes. Hay organizaciones que se desarrollaron para ayudar a mantener la estructura y la estandarización de los protocolos y procesos de Internet. Estas organizaciones incluyen el Internet Engineering Task Force (IETF), Internet Corporation for Assigned Names and Numbers (ICANN), y el Internet Architecture Board (IAB), además de muchos otros.

# Intranets y Extranets
Hay otros dos términos que son similares al término internet: intranet y extranet.

El término intranet se utiliza para referirse a la conexión privada de LAN y WAN que pertenecen a una organización. Una intranet está diseñada para que solo puedan acceder a ella los miembros y empleados de la organización, u otras personas autorizadas.

Es posible que una organización utilice una extranet para proporcionar acceso seguro a las personas que trabajan para otra organización, pero requieren datos de la empresa. Aquí hay algunos ejemplos de extranets:

- Una empresa que proporciona acceso a proveedores y contratistas externos.
- Un hospital que proporciona un sistema de reservas a los médicos para que puedan hacer citas para sus pacientes.
- Una secretaría de educación local que proporciona información sobre presupuesto y personal a las escuelas del distrito.

La figura ilustra los niveles de acceso que los diferentes grupos tienen a una intranet de la empresa, a una extranet de la empresa y a Internet.

# Redes por tología física
## 1.Red en bus

![Red en bus](topologia-red-bus.webp)
_Red en bus_

Una red en bus es aquella topología que se caracteriza por tener un único bus de comunicaciones (denominado bus, troncal o backbone) al cual se conectan los diferentes dispositivos. De esta forma todos los dispositivos comparten el mismo canal.

### Ventajas
- Facilidad de implementación y crecimiento.
- Fácil adaptación.
- Simplicidad en la arquitectura.
- Es una red que no ocupa mucho espacio.

### Desventajas
- Hay un límite de equipos dependiendo de la calidad de la señal.
- Puede producirse degradación de la señal.
- Complejidad de reconfiguración y aislamiento de fallos.
- Limitación de las longitudes físicas del canal.
- Un problema en el canal usualmente degrada toda la red.
- El canal requiere ser correctamente cerrado (caminos cerrados).
- Altas pérdidas en la transmisión debido a colisiones entre mensajes.
- Alta demanda
- ocupa mucho espacio.
- Hay mejores opciones de red.

## 2.Red en estrella

![Red en estrella](topologia-de-red-en-estrella-2022.webp)
_Red en estrella_

Una red en estrella es una red de computadoras donde las estaciones están conectadas directamente a un punto central y todas las comunicaciones se hacen necesariamente a través de ese punto (conmutador, repetidor o concentrador). Los dispositivos no están directamente conectados entre sí, además de que no se permite tanto tráfico de información. Dada su transmisión, una red en estrella activa tiene un nodo central “activo” que normalmente tiene los medios para prevenir problemas relacionados con el eco.

Se utiliza sobre todo para redes locales (LAN). La mayoría de las redes de área local que tienen un conmutador (switch) o un concentrador (hub) siguen esta topología. El punto o nodo central en estas sería el switch o el hub, por el que pasan todos los paquetes de usuarios.

Es la topología utilizada por la plataforma de Google.

### Ventajas
- Posee un sistema que permite agregar nuevos equipos fácilmente.
- Reconfiguración rápida de cada daño.
- Fácil de prevenir daños y/o conflictos, ya que no afecta a los demás equipos si ocurre algún fallo.
- Centralización de la red.
- Fácil de encontrar fallas de cada uno de ellos.

### Desventajas
- Si el hub (repetidor) o switch central falla, toda la red deja de transmitir.
- Es costosa, ya que requiere más cables que otras topologías
- El cable viaja por separado del concentrador a cada computadora.

## 3. Red en anillo

![Red en anillo](topologia-de-red-en-anillo.webp)
_Red en anillo_

Una red en anillo es una topología de red en la que cada nodo se conecta exactamente a otros dos nódos, formando una única ruta continua, para las señales a través de cada nodo: un anillo. Los datos viajan de un nodo a otro, y cada nodo maneja cada paquete.

### Ventajas
- Red muy ordenada donde cada dispositivo tiene acceso al token y la oportunidad de transmitir.
- Se desempeña mejor que una topología de bus bajo una gran carga de red 
- No requiere un nodo central para administrar la conectividad entre las computadoras
- Debido a la configuración de línea de punto a punto de los dispositivos con un dispositivo en cada lado (cada dispositivo está conectado a su vecino inmediato), es bastante fácil de instalar y reconfigurar, ya que agregar o quitar un dispositivo requiere mover solo dos conexiones.
- La configuración de línea punto a punto facilita la identificación y el aislamiento de fallas.
- La reconfiguración de las fallas de línea de los anillos bidireccionales puede ser muy rápida, ya que la conmutación se produce en un nivel alto y, por lo tanto, el tráfico no requiere ser redirigido individualmente.

### Desventajas
- Una estación de trabajo defectuosa puede crear problemas para toda la red. Esto se puede resolver utilizando un anillo doble o un switch que cierre la interrupción.
- Mover, agregar y cambiar los dispositivos puede afectar la red
- El retraso en la comunicación es directamente proporcional al número de nodos en la caja de cambios
- El ancho de banda se comparte en todos los enlaces entre dispositivos
- Más difícil de configurar que una topología en estrella

## 4. Red anillo doble

Una topología en anillo doble consta de dos anillos concéntricos, donde cada Host de la red está conectado a ambos anillos, aunque los dos anillos no están conectados directamente entre sí. Es análoga a la topología de anillo, con la diferencia de que, para incrementar la confiabilidad y flexibilidad de la red, hay un segundo anillo redundante que conecta los mismos dispositivos. La topología de anillo doble actúa como si fueran dos anillos independientes, de los cuales se usa solamente uno por vez.

## 5. Red en malla
![Red en malla](topologia-red-en-malla-2022.webp)
_Red en malla_

La topología de malla es en la que cada nodo está conectado a todos los nodos. De esta manera es posible llevar los mensajes de un nodo a otro por distintos caminos. Si la red de malla está completamente conectada, no puede existir absolutamente ninguna interrupción en las comunicaciones.

### Ventajas
- Mayor redundancia, pues existen múltiples caminos para que el paquete llegue a su destino. (Si falla una conexión o un nodo, se encontrará un camino alternativo)
- No requiere un nodo (o servidor) central, reduciendo el coste de mantenimiento.

### Desventajas
- La topología malla es muy cara de mantener, ya que se necesita mucho cableado.
- Si se utiliza de manera inalámbrica el precio de la instalación es mucho más cara.
- Puede dificultar en la instalación de nuevos dispositivos, ya que se necesitaría conectar el dispositivo con todos los otros dispositivos.
- Las redes malla son difíciles de gestionar y solucionar problemas.

## 6. Red en árbol
![Red en árbol](diagrama-topologia-de-red-en-arbol.webp)
_Red en árbol_

La red en árbol es una topología de red en la que los nodos están colocados en forma de árbol. Desde una visión topológica, es parecida a una serie de redes en estrella interconectadas salvo en que no tiene un concentrador central. En cambio, tiene un nodo de enlace troncal, generalmente ocupado por un hub o switch, desde el que se ramifican los demás nodos. Es una variación de la red en bus, el fallo de un nodo implica una interrupción en las comunicaciones. Se comparte el mismo canal de comunicaciones.

La topología en árbol puede verse como una combinación de varias topologías en estrella. Tanto la de árbol como la de estrella son similares a la de bus cuando el nodo de interconexión trabaja en modo difusión, pues la información se propaga hacia todas las estaciones, solo que en esta topología las ramificaciones se extienden a partir de un punto raíz (estrella), a tantas ramificaciones como sean posibles, según las características del árbol.

Los problemas asociados a las topologías anteriores radican en que los datos son recibidos por todas las estaciones sin importar para quién vayan dirigidos. Es entonces necesario dotar a la red de un mecanismo que permita identificar al destinatario de los mensajes, para que estos puedan recogerlos a su arribo. Además, debido a la presencia de un medio de transmisión compartido entre muchas estaciones, pueden producirse interferencia entre las señales cuando dos o más estaciones transmiten al mismo tiempo. Es la mejor topología de red que existe y con ella los datos fluyen de una manera más rápida que en los otros tipos de topologías de red.

### Desventajas
- Se requiere mucho cable
- Es poco fiable para las empresas distribuidas
- La medida de cada segmento viene determinada por el tipo de cable utilizado.
- Si se cae el segmento principal todo el segmento también cae.
- Es más difícil su configuración.
- Si se llegara a desconectar un nodo, todos los que están conectados a él se desconectan tamb

## 7. Red mixta o híbrida
![Red mixta](topologia-de-red-hibrida-1.webp)
_Red mixta_

En la topología híbrida o topología mixta las redes pueden utilizar diversas topologías para conectarse.

La topología mixta es una de las más frecuentes y se deriva de la unión de varios tipos de topologías de red, de aquí el nombre de “mixtas” o “híbridas”.

Ejemplos de topologías mixtas: en árbol, estrella-estrella, bus-estrella, etc.

Su implementación se debe a la complejidad de la solución de red, o bien al aumento en el número de dispositivos, lo que hace necesario establecer una topología de este tipo. Las topologías mixtas tienen un costo muy elevado debido a su administración y mantenimiento, ya que cuentan con segmentos de diferentes tipos, lo que obliga a invertir en equipo adicional para lograr la conectividad deseada.

### Ventajas y desventajas
La topología de red híbrida es sin duda alguna una red bastante confiable cuando se crea de manera correcta. Observando todos los puntos de vulnerabilidad y buscando una posible solución, combinando otro tipo de topología de red se encontrarán resultados positivos.

Sin embargo, como ya hemos comentado no todo es perfecto, por tal razón acá te presentaremos algunas ventajas y desventajas que siempre debes tener presente a la hora de establecer este tipo de red.