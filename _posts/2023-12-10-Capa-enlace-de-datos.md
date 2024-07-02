---
title: Capa enlace de datos
date: 2023-12-10 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Redes Locales]
tags: [redes locales, teoría, tsmr]
img_path: /assets/img/fisica/
---

# Capa de enlace de datos
## Propósito
### La capa de enlace de datos:
La **Capa de Enlace de Datos** “Capa 2”, actúa como un **facilitador** que permite la **comunicación** entre dispositivos en una red. Esta se encuentra en el modelo **OSI**.
Su **función principal** es asegurarse de que los datos estén listos para ser **transmitidos** a través de la infraestructura **física** y de que lleguen a su destino **sin problemas**.

Esta capa permite que los dispositivos se **comuniquen** entre sí **sin** necesidad de conocer los **detalles técnicos** de los cables y la **infraestructura** subyacente. También se asegura de que los **datos** estén **bien empaquetados** y que cualquier problema en la transmisión se **detecte** y se **corrija**.
La **Capa de Enlace de Datos** es un **traductor** que hace posible que los dispositivos se entiendan en una red, evitando que tengan que preocuparse por los **detalles técnicos** de la comunicación. Esto es esencial para que las redes funcionen de manera **eficiente** y para que sea más fácil **incorporar** nuevas tecnologías sin cambiar todo el sistema.

### Subcapas de enlace de datos IEEE 802 LAN/MAN:
Los estándares **IEEE 802 LAN/MAN** se aplican a diferentes tipos de redes, como **Ethernet con cable**, **redes inalámbricas** y **redes personales inalámbricas**. La **capa de enlace de datos** en estos estándares se divide en dos partes:
* **Control de Enlace Lógico (LLC)**: Es un **intermediario** que coloca **etiquetas** en los datos para que los dispositivos sepan cómo manejarlos. Esto es útil cuando tienes **diferentes tipos** de datos viajando por la misma red.
* **Control de Acceso a Medios (MAC)**: Este se encarga de **preparar los datos** para **enviarlos** y **recibirlos** en la red. También se asegura de que los datos lleguen **correctamente** y ayuda a múltiples dispositivos a compartir **la misma red** de manera organizada.



La parte de **Control de Acceso a Medios** realiza algunas tareas específicas:
*	Divide los datos en paquetes **identificables**.
*	Agrega **direcciones** a los datos para saber quién envía y quién recibe.
*	**Revisa** si los datos se han dañado en el camino.
*	Coordina cómo varios dispositivos **comparten la red** (como hablar por turnos).


### Provisión de acceso a los medios:
Cuando los datos viajan de un **dispositivo local** a uno **remoto** a través de **una red**, pueden encontrarse con diferentes **tipos de redes**. Por ejemplo, en una red **Ethernet local**, donde varios dispositivos compiten por usar el **mismo cable**, la capa de **enlace de datos** (MAC) ayuda a organizar esta competencia. En cambio, en conexiones más simples, como las que involucran **dos routers**, no necesitamos las mismas reglas de competencia que se utilizan en **Ethernet**.
En el caso de los routers, cuando un paquete llega a ellos, se encargan de **empaquetar** adecuadamente los datos y **enviarlos** al siguiente lugar. Para hacer esto, utilizan un conjunto específico de reglas que se adaptan a cada tipo de **medio de transmisión**. A medida que los paquetes viajan a través de diferentes **partes de la red**, pueden cambiar de **medio** y de **conjunto de reglas**.
Los routers hacen un trabajo muy importante en la capa de enlace de datos, donde se encargan de **empacar**, **desempacar** y **reenviar** los datos en función de las **características** de cada parte de la red por la que pasan.

### Estándares de la capa de enlace de datos:
Los **protocolos** de la capa de enlace de datos **no están definidos** por las **Solicitud de Comentarios (RFC)**, a diferencia de los protocolos de capas **superiores** en el conjunto **TCP/IP**. El **Grupo de Trabajo de Ingeniería de Internet (IETF)** es responsable de mantener los **protocolos** y **servicios** de las capas superiores en **TCP/IP**, pero no establece las funciones y el funcionamiento de la **capa de acceso a la red** en **TCP/IP**.
La definición de **estándares abiertos** y **protocolos aplicables** a la capa de acceso a la red, que abarca las capas **físicas** y de **enlace de datos** en el modelo **OSI**, se lleva a cabo por organizaciones de ingeniería. Algunas de estas organizaciones incluyen:
* Instituto de Ingenieros Eléctricos y Electrónicos **(IEEE)**.
* Unión Internacional de Telecomunicaciones **(ITU)**.
* Organización Internacional para la Estandarización **(ISO)**.
* Instituto Nacional Estadounidense de Estándares **(ANSI)**.

## Topologias
### Topologías física y lógica:
La **capa de enlace de datos** se encarga de **preparar** los datos de red para su **transmisión** en la **red física**. Para lograr esto, necesita comprender la **topología** de la red. Hay **dos tipos** de topologías en redes **LAN** y **WAN**:
1.	Topología **Física**: Describe cómo están conectados **físicamente** los dispositivos, incluyendo los dispositivos **finales** y los dispositivos **intermedios** (como routers, switches y puntos de acceso inalámbrico). También puede incluir detalles como la **ubicación física** de los dispositivos. Las topologías físicas suelen ser **punto a punto** o en **forma de estrella**.
2.	Topología **Lógica**: Se refiere a cómo se transfieren las **tramas de datos** de un nodo a otro en la red. Identifica las **conexiones virtuales** a través de **interfaces** de dispositivos y **esquemas** de direccionamiento IP en la **capa 3**.
La capa de **enlace de datos** visualiza la topología **lógica** de la red mientras controla el **acceso a los medios** de transmisión. La topología **lógica** influye en el **tipo de trama** de red y en el **control de acceso a los medios** que se utilizan.

### Topologías de WAN: 
Las topologías **WAN** son formas de organizar conexiones en redes de **gran alcance** geográfico:
1.	**Punto a Punto** en **WAN**: Es como una conversación directa entre dos ubicaciones **remotas**, a menudo usando **líneas dedicadas**. Las topologías punto a punto conectan **directamente** dos dispositivos, sin necesidad de compartir la red con otros. Cuando se usan protocolos como **PPP**, los dispositivos no tienen que preocuparse por distinguir entre tramas dirigidas a ellos o a otros. Esto simplifica mucho el manejo de las **comunicaciones**, ya que todas las tramas se mueven solo entre esos dos dispositivos conectados. Incluso si hay dispositivos **intermedios** entre los dispositivos de **origen** y **destino**, la topología **lógica** sigue siendo **punto a punto**. Agregar dispositivos intermedios no cambia la forma en que se establece la conexión punto a punto.
1.	**Hub and Spoke** en **WAN**: Implica una **ubicación central** que se conecta con **varias ubicaciones remotas**, como una estrella con un centro y muchas ramas hacia afuera. El centro administra la red.
1.	**Malla** en **WAN**: Conecta **todas las ubicaciones remotas** entre sí, como si todas estuvieran entrelazadas, proporcionando muchas **rutas** para la comunicación.

La elección de la **topología WAN** depende de las **necesidades** específicas de la organización, la importancia de la **redundancia** y la **administración** en la red.


### Topologías de LAN: 
En las redes de área local **(LAN)** donde varios dispositivos se conectan, generalmente usamos **tres tipos** de configuraciones principales:
* Topología en **Estrella**: Aquí, **todos los dispositivos** se conectan a un dispositivo **central**, como un switch. Si ampliamos esto, podemos interconectar varios switches. Esta configuración es **fácil de usar**, permite agregar o quitar dispositivos **sin complicaciones** y facilita la **solución de problemas**. 
* Topología en **Bus**: En una topología de bus, **todos los dispositivos** están conectados **uno tras otro** en una línea y terminan en **ambos extremos**. No se necesitan dispositivos intermedios como switches.
* Topología en **Anillo**: Aquí, los dispositivos se conectan en un **círculo**, creando un anillo. A diferencia de la topología de bus, el anillo **no necesita** terminarse en ambos extremos.


### Comunicación Dúplex completo y semidúplex:
Es fundamental comprender la **comunicación dúplex** al hablar de topologías de **LAN**, ya que se refiere a cómo los datos se transmiten entre **dos dispositivos**. Hay dos modos comunes de dúplex:
* Comunicación **Semidúplex**: En este modo, dos dispositivos pueden **enviar** y **recibir** datos, pero **no** al mismo tiempo. Se utiliza en **WLAN** y en algunas topologías de **bus** heredadas con switches **Ethernet**. Solo un dispositivo puede **enviar** o **recibir** datos a la vez en un medio compartido.
* Comunicación de **Dúplex Completo**: En este modo, **ambos dispositivos** pueden **enviar** y **recibir** datos **simultáneamente** en el **mismo medio** compartido. Los switches Ethernet suelen funcionar en este modo de forma **predeterminada**, pero pueden cambiar a **semidúplex** si se conectan a dispositivos externos.


La comunicación en modo **semidúplex** restringe la **transmisión de datos** a una dirección a la vez, mientras que el modo de **dúplex completo** permite el **envío** y la **recepción** de datos al **mismo tiempo**.
Es crucial que dos interfaces interconectadas, como la tarjeta de red de una computadora y una interfaz en un switch Ethernet, operen en el mismo modo dúplex. Si no coinciden, puede haber **problemas de compatibilidad** que generen **ineficiencia** y **retrasos en la comunicación**.

### Métodos de control de acceso:
En una red de **acceso múltiple**, como las LAN Ethernet y WLAN, varios dispositivos intentan comunicarse al **mismo tiempo**. Hay dos enfoques para regular cómo estos dispositivos **comparten** el medio de comunicación:
* Acceso Basado en la **Contienda**:
En este enfoque, **todos** los dispositivos **compiten** por el acceso al medio y **solo uno** puede transmitir a la vez. Cuando varios dispositivos intentan transmitir **simultáneamente**, se utiliza un sistema de **resolución de conflictos**. Esto se ve en redes Ethernet antiguas de bus, donde se detectan colisiones y se gestionan.
* Acceso **Controlado**:
En este caso, cada dispositivo tiene un **turno asignado** para usar el medio. Aunque es más **predecible**, **no** es tan **eficiente**, ya que los dispositivos deben esperar su **turno** para transmitir. Ejemplos incluyen el método de **"token"** utilizado en redes de **anillo**, donde solo el dispositivo con el **"token"** puede **transmitir**.
En las redes Ethernet modernas, no se necesitan estos métodos de control de acceso, ya que permiten la transmisión y la recepción **simultáneas**.

### Acceso por contención: CSMA/CD:
Estos son ejemplos de redes que utilizan este **método de acceso**:
* LAN **inalámbrica**, que usa **CSMA/CA** (Acceso Múltiple con Prevención de Colisiones).
* LAN **Ethernet** de topología de **bus heredada**, que utiliza **CSMA/CD** (Acceso Múltiple con Detección de Colisiones).
* LAN **Ethernet** heredada con un **hub**, que también usa **CSMA/CD**.


En estas redes, la **comunicación** se realiza en modo **semidúplex**, lo que significa que **solo un** dispositivo puede transmitir o recibir datos a la vez. Para gestionar esto, se emplea un proceso que coordina cuándo un dispositivo puede **transmitir** y cómo se **resuelven** las situaciones en las que varios dispositivos intentan **transmitir** al **mismo tiempo**.

Cuando dos dispositivos intentan transmitir **simultáneamente**, se produce lo que se conoce como una **colisión**. En las redes LAN Ethernet **heredadas**, ambos dispositivos **detectan** esta colisión en la red, lo que se refiere a la **función de detección de colisiones** (CD) en CSMA/CD. La tarjeta de red (NIC) **compara** los datos enviados con los recibidos o **identifica** irregularidades en la señal en el medio. Cuando ocurre una colisión, los datos enviados por ambos dispositivos se **dañan** y necesitan ser **retransmitidos**. Este proceso asegura que la comunicación en redes basadas en competencia sea **ordenada** y **sin conflictos**.

### Acceso por contención: CSMA/CA:
En las **WLAN IEEE 802.11**, se utiliza una variante del protocolo **CSMA** llamada **CSMA/CA** (Acceso Múltiple con Detección de Portadora). Esta técnica es similar a **CSMA/CD** en el sentido de que **verifica** si el medio de comunicación está **libre** antes de transmitir. Sin embargo, **CSMA/CA** emplea **métodos adicionales** para prevenir colisiones en entornos **inalámbricos**.
A diferencia de **CSMA/CD**, **CSMA/CA** no detecta las **colisiones**, pero trata de evitarlas. Esto se logra esperando un breve período antes de transmitir. Además, cada dispositivo **inalámbrico** que transmite incluye **información** sobre cuánto tiempo necesitará el medio para la transmisión. Todos los otros dispositivos **inalámbricos** reciben esta **información** y saben cuánto **tiempo** el medio no estará disponible para su uso.
Después de que un dispositivo **inalámbrico** envía una trama **802.11**, el receptor envía un **acuse de recibo** para **confirmar** que la trama se recibió correctamente.
Tanto en redes **LAN Ethernet** con concentradores como en redes **WLAN**, los sistemas **basados en contienda** no son eficientes cuando se utilizan intensivamente. Es importante destacar que las redes **LAN Ethernet** con switches **no utilizan** sistemas basados en contienda, ya que los **switches** y las **NIC** de los dispositivos operan en modo **dúplex completo**, lo que permite la transmisión y recepción simultáneas.

## Trama de enlace de datos
### La trama:
Este tema se enfoca en explicar el **proceso** que sigue una trama de datos a medida que viaja **a través** de una **red**. La **información** contenida en una trama está determinada por el **tipo de protocolo** que se utiliza.
La capa de **enlace de datos** se encarga de **preparar**** los datos encapsulados (que normalmente son paquetes **IPv4** o **IPv6**) para que puedan ser transmitidos a través de la red local. Esto se logra al añadir un **encabezado** y un **tráiler** a los datos, lo que crea una unidad llamada **"trama"**.

El protocolo de capa de enlace de datos es responsable de **gestionar** las **comunicaciones** entre las tarjetas de interfaz de red (NIC) dentro de la misma red. Aunque existen varios protocolos de capa de enlace de datos que **describen** las tramas, todas comparten **tres partes básicas**: un **encabezado**, los **datos reales** y un **tráiler**. Lo que hace especial a la capa de enlace de datos es que, a diferencia de otros protocolos de encapsulación, **agrega información** al final de la trama, conocida como tráiler.
Cada protocolo de **capa de enlace de datos** tiene su propia manera de encapsular los datos **en la trama**. No existe un formato de trama único que funcione para todas las situaciones. La cantidad de **información de control** que se agrega a la trama depende del **entorno**, las **necesidades de control de acceso** al medio y la **topología lógica** de la red. Por ejemplo, una trama de una red inalámbrica **(WLAN)** debe incluir **información adicional** para evitar colisiones, lo que la diferencia de una trama en una red Ethernet.
La estructura de las tramas de **capa de enlace de datos** varía según el **protocolo** utilizado y el **entorno** de la red, ajustándose a las necesidades **específicas** de cada caso.

### Campos de la trama:
La **capa de enlace de datos** divide la transmisión en **bloques comprensibles**, con información de control ubicada en el **encabezado** y el **tráiler** en campos separados. Esto crea una **estructura** reconocible por los nodos y permite que las señales **físicas** se descifren en **paquetes** en el destino.
Las tramas de **enlace de datos** incluyen campos genéricos, como indicadores de inicio y fin de trama para marcar los límites de la trama, direcciones que indican los nodos de **origen** y **destino** en los medios, un campo de tipo que identifica el protocolo de capa 3 en el campo de datos, un campo de control que puede identificar servicios especiales de **control de flujo**, como la calidad de servicio **(QoS)**, y, por supuesto, los datos reales que contienen el contenido de la trama. Además, se agrega una parte de detección de errores al final de la trama, que se utiliza para verificar si la trama llegó sin errores debido a posibles **interferencias**, **distorsiones** o **pérdida de señales** en los medios.
La capa de enlace de datos asigna **direcciones físicas** a los dispositivos en la red local. Estas direcciones se encuentran en el **encabezado** de la trama y especifican tanto el nodo de **origen** como el nodo de **destino** en la red local. A diferencia de las direcciones lógicas de la Capa 3, que son jerárquicas y se utilizan para identificar la red a la que pertenece un dispositivo, las direcciones **físicas** son únicas para cada dispositivo individual. Estas direcciones solo se utilizan para la **comunicación** dentro de la misma red local y no tienen relevancia fuera de ella.
La capa de enlace de datos **segmenta** y **controla** las tramas de datos a medida que se mueven a través de una red local y se encarga de asignar direcciones **físicas** para la comunicación dentro de la misma red.

### Direcciones de Capa 2:
La **capa de enlace de datos** se encarga de proporcionar las direcciones que se utilizan para **enviar** tramas a través de una red local compartida. Estas direcciones, llamadas **direcciones físicas**, se encuentran en el encabezado de la trama y especifican a qué dispositivo de la red local se envía la trama. Estas direcciones son **únicas** para cada dispositivo y no indican en qué parte de la red se encuentra el dispositivo. La capa 2 se encarga de que los dispositivos se comuniquen dentro de la **misma red**.
Las **direcciones** de Capa 2 se usan solo para enviar datos dentro de la misma red y **no tienen relevancia fuera de ella**. A diferencia de las direcciones lógicas de la **Capa 3**, que son **jerárquicas** y se usan para **guiar** datos a través de diferentes redes, las direcciones de **Capa 2** son específicas para cada dispositivo y **no cambian**, aunque el dispositivo se mueva a otra red o subred.
Cuando los datos deben viajar a través de diferentes segmentos de red, se necesita un dispositivo intermedio, como un router. El router utiliza la dirección **física** de **Capa 2** para **recibir** y **desempaquetar** la trama, y luego examina la dirección jerárquica de Capa 3. Usando la dirección IP, el router determina **dónde se encuentra** la red del dispositivo de destino y **cuál es la mejor ruta** para llegar a él. Luego, el router crea una nueva trama y la envía al siguiente segmento de red en el camino hacia su destino final.

### Tramas LAN y WAN:
Los protocolos de comunicación utilizados en las redes varían según si se trata de **redes locales cableadas** (LAN) o **redes inalámbricas** (WLAN). En LAN cableadas, como las que utilizan cables Ethernet, se emplean **protocolos Ethernet**. Por otro lado, las comunicaciones inalámbricas se rigen por los protocolos WLAN, específicamente el estándar **IEEE 802.11**.
Tradicionalmente, las redes de área amplia (WAN) han utilizado una serie de **protocolos**, como Protocolo punto a punto **(PPP)**, Control de enlace de datos de alto nivel **(HDLC)**, Frame Relay, Modo de transferencia asíncrona **(ATM)** y **X.25**, para adaptarse a diversas topologías de red, como conexiones punto a punto, configuraciones en forma de estrella (hub-and-spoke) y redes de malla completa.
En la actualidad, muchas de estas tecnologías de capa 2 utilizadas en WAN están siendo **reemplazadas** por la tecnología Ethernet, lo que simplifica y unifica los protocolos de capa 2 en las redes de área amplia.
El protocolo de capa 2 que se selecciona para una **topología de red específica** depende de la **tecnología utilizada** para implementar esa topología. La elección se basa en **factores** como el tamaño de la red **(número de hosts)**, la extensión geográfica de la red y los servicios que se desean ofrecer a través de ella.
Una LAN, que abarca una **zona geográfica más pequeña**, utiliza tecnologías de alto ancho de banda que son capaces de soportar un **gran número** de dispositivos. En cambio, en redes WAN que abarcan áreas geográficas **más amplias**, como varias ciudades, los enlaces de larga distancia y las limitaciones de ancho de banda **influyen** en la elección de los protocolos.
Cada vez más se tiende a adoptar Ethernet en las WAN para **simplificar la infraestructura** y **mejorar** la eficiencia de las redes.