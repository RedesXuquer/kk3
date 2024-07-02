---
title: Capa física
date: 2023-11-05 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Redes Locales]
tags: [redes locales, teoría, tsmr]
img_path: /assets/img/fisica/
---

![Alt text](image.png)

# La capa Física
## Introducción
La capa física es la primera capa del **modelo OSI**.
También se le conoce como CAPA 1, esta es responsable de la **transmisión de bits** no
estructurados a través de un medio de comunicación **físico**, ya sea *cable de cobre*, *fibra
óptica*,
*ondas de radio*, etc.
Esta capa se enfoca en aspectos relacionados con la **transmisión de datos** en su forma más
básica y física.
Esta capa forma parte de la capa **Acceso a red** del modelo TCP/IP.
Sin la capa física, ***no tendría una red***.
En este tema veremos las **características**, **utilidades** y **propósitos** de:
- Propósito de la capa física.
- Características de la capa física.
- Cableado de cobre.
- Cableado UTP.
- Cableado de fibra óptica.
- Medios inalámbricos.
## Propósito de la capa física
El propósito **fundamental** de la capa física en el modelo OSI es *facilitar la transmisión
física* de
bits a través de un medio de comunicación. Esta capa se centra en la **interfaz** entre el
*equipo* y
el *medio físico*, asegurando que los bits se puedan enviar y recibir de manera **confiable** y
**eficiente**.
### La conexión física:
Para que se pueda producir cualquier **comunicación de red** se debe establecer antes una
**conexión a una red local**.
Una conexión física puede ser:
- Una conexión por cable
- Una conexión inalámbrica mediante ondas de radio.
El tipo de conexión **física** utilizada depende de la configuración de la red.
Ejemplo: En muchas oficinas corporativas, los empleados tienen PC de escritorio o portátiles
que se conectan físicamente, **mediante cables**, a un switch compartido.
Este tipo de configuración se denomina red cableada y los datos se transmiten a través de un
cable físico.
Muchas empresas también ofrecen conexiones **inalámbricas** “sin cableado” para PC
portátiles, tablets y smartphones.
En el caso de los dispositivos inalámbricos, los datos se transmiten mediante ondas de radio.
Los dispositivos en una red inalámbrica deben estar conectados a un **punto de acceso**
inalámbrico (AP) o **router inalámbrico**.
En términos de **rendimiento**, no todas las conexiones **físicas** son iguales a la hora de
**conectarse** a una red.
>[!¿Qué son las **Tarjetas de interfaz de red**?]
>
>Las tarjetas de interfaz de red (NIC) conectan un dispositivo a la red.
Las NIC de Ethernet se usan para una **conexión por cable**, mientras que las NIC de la red
de área local **inalámbrica** (WLAN) se usan para la conexión inalámbrica. Los dispositivos
para usuarios finales pueden incluir **un tipo** de NIC o **ambos**.
### La capa física:
Esta capa proporciona los medios de transporte de los bits que conforman una trama de la
capa de **enlace de datos** a través de los medios de red.
Esta capa acepta una **trama completa** desde la capa de enlace de datos y la **codifica**
como una secuencia de señales que se transmiten en los medios locales. Un dispositivo final o
un dispositivo intermediario recibe los bits **codificados** que componen una trama. La capa
física codifica las tramas y crea las señales eléctricas, ópticas o de ondas de radio que
representan los bits en cada trama.
La capa física del nodo de destino recupera estas señales individuales de los medios, las
restaura a sus representaciones **en bits** y pasa los bits a la capa de enlace de datos en
forma de **trama completa**.
## Características de la capa física.
### Los estándares de la capa física:
Vamos a ver los componentes y los medios utilizados para construir una red, así como los
estándares necesarios para que todo funcione en conjunto.
Los protocolos y las operaciones de las capas OSI superiores se llevan a cabo en software
diseñado por ingenieros en **software** e informáticos. El grupo de trabajo de ingeniería de
Internet (IETF) define los **servicios** y **protocolos** del conjunto TCP/IP.
Existen muchas organizaciones internacionales y nacionales que intervienen en el
**establecimiento** y el **mantenimiento** de los estándares de la capa física. Por ejemplo, los
estándares de hardware, medios, codificación y señalización de la capa **física** están
definidos y regidos por estas **organizaciones de estándares**:
1. Organización Internacional para la Estandarización (ISO)
1. Asociación de las Industrias de las Telecomunicaciones (TIA) y Asociación de Industrias
Electrónicas (EIA)
1. Unión Internacional de Telecomunicaciones (ITU)
1. Instituto Nacional Estadounidense de Estándares (ANSI)
1. Instituto de Ingenieros Eléctricos y Electrónicos (IEEE)
1. Autoridades nacionales reguladoras de las telecomunicaciones, incluida la Federal
Communication Commission (FCC) de los Estados Unidos y el Instituto Europeo de Estándares
de Telecomunicaciones (ETSI).
>Los **estándares** de la capa física abarcan tres áreas funcionales
>* Componentes físicos
>* Codificación
>* Señalización
### Componentes físicos:
Los componentes físicos son los dispositivos de hardware electrónico que transmiten las
señales que representan los bits. Todos los componentes de hardware, como **NIC**,
**interfaces** y **conectores**, materiales y diseño de los cables, se especifican en los
estándares asociados con la **capa física**.
### Codificación:
La codificación es un **método** que se utiliza para convertir una transmisión de bits de datos
en un “código” predefinido. La codificación es el método o patrón utilizado para representar la
información digital.
### Señalización:
La capa física debe generar las señales inalámbricas, ópticas o eléctricas.
Estas representan los “1” y los “0” en los medios.
La forma en que se representan los bits se denomina **método de señalización**.
Los estándares de la capa física deben definir **qué tipo de señal** representa un “1” y **qué
tipo de señal** representa un “0”.
Esto puede ser tan simple como un **cambio en el nivel** de una señal eléctrica o de un pulso
óptico.
### Ancho de banda:
Esta es la capacidad a la que un medio puede transportar datos.
El ancho de banda **digital** mide la cantidad de datos que pueden fluir desde un lugar hacia
otro en un **período de tiempo** determinado.
El ancho de banda generalmente se mide en kilobits por segundo (kbps), megabits por
segundo (Mbps) o gigabits por segundo (Gbps).
En ocasiones, el ancho de banda se piensa como la velocidad a la que viajan los bits, sin
embargo, esto no es así.
Una **combinación de factores** determina el ancho de banda práctico de una red:
- Las propiedades de los medios físicos.
- Las tecnologías seleccionadas para la señalización y la detección de señales de red.
Las propiedades de los **medios físicos**, las **tecnologías actuales** y las **leyes de la
física** desempeñan una función al momento de determinar el ancho de banda disponible.
### Terminología del ancho de banda:
Los términos utilizados para medir la **calidad** del ancho de banda incluyen:
1. **Latencia**: Es la cantidad de tiempo, incluidas las demoras que les toma a los datos
transferirse desde un punto determinado hasta otro. (PING) Cuanta mas alta es la latencia, más
demorarán los datos en llegar del punto A al punto B.
1. **Cacidad de transferencia útil**: Esta es la medida de datos utilizables transferidos durante
un período determinado. La capacidad de transferencia útil es el rendimiento menos la
sobrecarga de tráfico para establecer sesiones, acuses de recibo, encapsulación y bits
retransmitidos.
1. **Rendimiento**: Es la medida de transferencia de bits a través de los medios durante un
período de tiempo determinado. El rendimiento generalmente no coincide con el ancho de
banda y suele ser menor.
Pueden afectar:
* La cantidad de tráfico
* El tipo de tráfico
* La latencia creada por la cantidad de dispositivos de red encontrados entre origen y destino
## Cableado de cobre.
### Características del cableado de cobre:
El **cableado de cobre** no es solo un tipo de cable. Hay tres tipos diferentes de cableado de
cobre que se utilizan cada uno en situaciones específicas.
Las redes utilizan **medios de cobre** porque son económicos, fáciles de instalar y tienen baja
resistencia a la corriente eléctrica. Sin embargo, estos medios **están limitados** por la
distancia y la interferencia de señal.
Los **datos** se transmiten en cables de cobre por impulsos eléctricos.
Un detector en la **NIC** de un dispositivo de destino debe recibir una señal que pueda
decodificarse exitosamente para que coincida con la señal que fue enviada.
Cuanto **más lejos** viaja una señal, **más se deteriora**.
Todos los **medios de cobre** tienen unas limitaciones de distancia estrictas.
Los valores de temporización y voltaje de los pulsos eléctricos también son vulnerables a las
interferencias de dos fuentes:
1. Interferencia **electromagnética** (**EMI**) o Interferencia de **radiofrecuencia**
(**RFI**): Las señales de **EMI** y **RFI** pueden distorsionar y dañar las señales de datos
que transportan los medios de cobre. Estas incluyen las **ondas de radio** y dispositivos
**electromagnéticos**, como las luces fluorescentes o los motores eléctricos.
Para contrarrestar los efectos negativos de la **EMI** y la **RFI**, algunos tipos de cables de
cobre se empaquetan con un blindaje metálico y requieren una conexión a tierra adecuada.
1. **Crosstalk**: Este se trata de una perturbación causada por los campos eléctricos o
magnéticos de una señal **de un hilo** a la señal **de un hilo adyacente**. En los circuitos
telefónicos, el crosstalk puede provocar que se escuche parte de otra conversación de voz de
un circuito adyacente.
Para contrarrestar los efectos negativos del crosstalk, algunos tipos de cables de cobre tienen
**pares de hilos** de circuitos opuestos **trenzados** que cancelan dicho tipo de interferencia
en forma eficaz.
La susceptibilidad de los cables de cobre al ruido electrónico también se puede limitar
utilizando estas recomendaciones:
* La elección del tipo o la categoría de cable más adecuados a un entorno de red determinado.
* El diseño de una infraestructura de cables para evitar las fuentes de **interferencia** posibles
y conocidas en la estructura del edificio.
* El uso de técnicas de cableado que incluyen el **manejo** y la **terminación** apropiados de
los cables
### Tipos de cableado de cobre:
Existen 3 tipos de cableado:
- **Par trenzado no blindado (UTP)**: El cableado **UTP** es el medio más común para
conectar dispositivos en redes. Consiste en cuatro pares de hilos trenzados y protegidos por
plástico flexible. Se utiliza con conectores **RJ-45** para enlazar hosts con dispositivos de red
como switches y routers, principalmente en redes LAN. El trenzado de los hilos ayuda a evitar
interferencias y proporciona cierta protección física.
- **Par trenzado blindado (STP)**: El cableado **STP** ofrece una mayor protección
contra interferencias que el UTP, aunque es más costoso y difícil de instalar. Al igual que el
UTP, **utiliza conectores RJ-45**. Este combina técnicas de blindaje para contrarrestar
interferencias electromagnéticas y de radiofrecuencia, además del **trenzado de hilos** para
mitigar el crosstalk.
El cable STP consta de cuatro pares de hilos, cada par está protegido con una hoja metálica y
luego se cubre con una malla tejida o una hoja metálica.
- **Cable coaxial**: El cable **coaxial** contiene dos conductores compartiendo un eje:
uno de cobre para transmitir señales electrónicas y otro de malla de cobre o hoja metálica que
actúa como blindaje contra interferencias electromagnéticas. Está recubierto por **aislamiento
plástico flexible** y un **revestimiento** para protección **física**.
## Cableado UTP.
### Propiedades del cableado UTP:
El cableado **UTP** consta de cuatro pares de hilos trenzados y recubiertos con plástico
flexible. Su **tamaño pequeño** facilita la instalación. No cuenta con blindaje contra **EMI** y
**RFI**, pero los diseñadores emplean técnicas como anulación y variación en la torsión de
hilos para reducir el crosstalk.
La **anulación** se logra al emparejar hilos en circuitos, generando campos magnéticos
opuestos que anulan interferencias.
Variar el **número de vueltas** por par de hilos también mejora la anulación. Los cables UTP
siguen especificaciones para la **cantidad de vueltas por metro**, y cada par coloreado tiene
un trenzado diferente. Estos cables se basan en la anulación de los hilos trenzados para
mantener la calidad de la señal y proporcionar un auto blindaje efectivo en los medios de red.
### Conectores y estándares del cableado UTP:
El cableado **UTP** cumple con los estándares establecidos en conjunto por la TIA/EIA.
La TIA/EIA-568 estipula los estándares comerciales de cableado para las instalaciones **LAN**
y es el estándar de mayor uso en entornos de cableado **LAN**.
El Instituto de Ingenieros Eléctricos y Electrónicos (**IEEE**) establece las características
eléctricas del cableado de cobre y califica el cable UTP en función de su rendimiento. Los
cables **UTP** se categorizan según su capacidad para transportar datos a diferentes
velocidades de ancho de banda. Por ejemplo, el cable de **Categoría 5** es común en
instalaciones de **FastEthernet 100BASE-TX**, y hay otras categorías como **5e**, **6** y
**6a** diseñadas para admitir velocidades de transmisión de datos más altas.
Algunos fabricantes producen cables que exceden las especificaciones de la categoría **6a**
de la **TIA/EIA** y se refieren a estos como cables de **Categoría 7**.
Los cables UTP generalmente se terminan con un conector **RJ-45**. El estándar TIA/EIA-568
describe las asignaciones de los códigos por colores de los hilos a la asignación de pines
(diagrama de pines) de los cables Ethernet.
### Cables UTP directos y cruzados:
Los cables **UTP** pueden requerir diferentes disposiciones de hilos en los conectores
**RJ-45** según las situaciones. Esto implica conectar los hilos de manera diferente para
distintos grupos de pines en el conector.
Los principales tipos de cables que resultan de estas convenciones de cableado son:
- Cable **directo** de Ethernet: Es el tipo más común de cable de red, usado para
conectar un **host a un switch** y un **switch a un router**.
- Cable **cruzado** Ethernet: Se emplea para conectar dispositivos similares, como
**switch a switch**, **host a host** o **router a router**. No obstante, los cables cruzados se
consideran obsoletos en gran medida debido a la tecnología **Auto-MDIX** que permite a las
**NIC** detectar automáticamente el tipo de cable y realizar la conexión adecuada.
## Cableado de fibra óptica.
### Propiedades del cableado de fibra óptica:
El **cableado de fibra óptica** representa otra opción en las redes, aunque es menos común
debido a su costo más elevado.
Este presenta propiedades que lo convierten en la elección óptima en ciertos escenarios,
aspectos. Transmite **datos** a distancias más extensas y con capacidades de **ancho de
banda** superiores que cualquier otro medio de red.
A diferencia de los **cables de cobre**, la fibra óptica transmite señales con menos atenuación
y es completamente inmune a las interferencias electromagnéticas (**EMI**) y de
radiofrecuencia (**RFI**). Se utiliza para interconectar dispositivos de red.
La **fibra óptica** consiste en un hilo flexible, extremadamente delgado y transparente de
**vidrio** altamente puro, apenas más grueso que un cabello humano.
Los datos se codifican en la fibra como **impulsos de luz**. Funciona como una guía de ondas
o una "tubería de luz", transmitiendo luz entre los extremos con una **pérdida mínima** de la
señal.
### Tipos de medios de fibra:
En términos generales, los cables de **fibra óptica** pueden clasificarse en dos tipos:
- Fibra **monomodo** (**SMF**): Es un tipo de cable de fibra óptica que permite la
transmisión de señales de luz a través de un único modo de propagación. Esto significa que
solo se permite la propagación de una señal de luz en una sola dirección, lo que reduce la
atenuación y **mejora la velocidad** y la **capacidad** de ancho de banda. La **SMF** es
ampliamente utilizada en largas distancias y aplicaciones de alta velocidad, como redes de
larga distancia y conexiones de datos de alta velocidad.
- Fibra **multimodo** (**MMF**): Es un tipo de cable de fibra óptica que permite la
transmisión de múltiples señales de luz a través de **diferentes** modos de propagación. Esto
significa que varias señales de luz se propagan **simultáneamente** por la fibra en distintos
ángulos, lo que puede causar mayor atenuación y dispersión de la señal en comparación con la
fibra monomodo. La **MMF** es comúnmente utilizada en distancias más cortas y redes locales
donde no se requiere una alta capacidad de ancho de banda a largas distancias.
Una de las diferencias destacadas entre **MMF** y **SMF** es la cantidad de dispersión.
La dispersión se refiere a la extensión de los pulsos de luz con el tiempo. El **aumento** de la
**dispersión** significa una mayor **pérdida** de la **intensidad** de la señal. **FMM** tiene
una mayor dispersión que **SMF**. Es por eso que **MMF** sólo puede viajar hasta 500
metros antes de la pérdida de señal.
### Uso del cableado de fibra óptica:
El **cableado de fibra óptica** se utiliza en **cuatro** tipos de industrias:
- **Redes empresariales**: Se utilizan para aplicaciones de cableado backbone y
dispositivos de infraestructura de interconexión.
- **Fibra hasta el hogar** (**FTTH**): Se utiliza para proporcionar servicios de banda
ancha siempre activos a hogares y pequeñas empresas.
- **Redes de larga distancia**: Utilizadas por proveedores de servicios para conectar
países y ciudades.
- **Redes de cable submarino**: Se utilizan para proporcionar soluciones confiables de
alta velocidad y capacidad capaces de sobrevivir en entornos submarinos hostiles a distancias
transoceánicas.
### Conectores de fibra óptica:
Un **conector de fibra óptica** termina el extremo de una **fibra óptica**. Hay una variedad de
conectores de fibra óptica disponibles. Las diferencias principales entre los tipos de conectores
son las dimensiones y los métodos de acoplamiento. Las empresas deciden qué tipos de
conectores utilizarán en base a sus equipos.
- **Conectores de punta directa (ST)**: Son conectores de fibra óptica que utilizan una
terminación tipo bayoneta para su acoplamiento. Son comunes y fáciles de conectar y
desconectar. Tienen una **punta cilíndrica** y se utilizan en aplicaciones de fibra multimodo y
monomodo.
- **Conectores suscriptor (SC)**: Estos son conectores de fibra óptica que se utilizan
ampliamente en aplicaciones de redes. Tienen un mecanismo de enganche tipo **push-pull**
que facilita la conexión y desconexión. Son utilizados tanto para fibra multimodo como
monomodo.
- **Conectores Lucent (LC)**: Son pequeños y altamente utilizados en aplicaciones de
fibra óptica. Utilizan un mecanismo de enganche similar al SC, pero son más compactos, lo que
los hace ideales para espacios limitados. Son comunes en conexiones de fibra óptica de **alta
densidad** y se utilizan para fibra multimodo y monomodo.
- **Conectores Simplex**: Son conectores de fibra óptica que permiten la conexión de
una sola fibra. Son utilizados para conexiones **punto a punto**, donde solo se requiere una
dirección de transmisión. Pueden ser tanto conectores ST, SC, LC, u otros, pero se usan para
una sola fibra.
- **Conectores LC multimodo dúplex**: Estos son conectores de fibra óptica LC que
permiten la conexión de dos fibras en modo multimodo. Son **dúplex**, lo que significa que
permiten la transmisión bidireccional de datos en ambos sentidos. Son comunes en
aplicaciones donde se requiere mayor capacidad de ancho de banda y se utilizan para
**conexiones** de fibra **multimodo**.
### Cables de conexión de fibra:
Los cables de **conexión de fibra óptica** son necesarios para interconectar dispositivos de
infraestructura. El uso de colores distingue entre los cables de conexión **monomodo** y
**multimodo**. El conector amarillo corresponde a los cables de fibra óptica monomodo y el
naranja (o aqua) corresponde a los cables de fibra óptica multimodo.
## Medios inalámbricos.
### Propiedades de los medios inalámbricos:
Estos permiten la **conexión** a la capa física de una red a través de señales
electromagnéticas, usando frecuencias de radio y microondas para representar datos en forma
**binaria**.
La cobertura se ve afectada por **obstáculos** y **materiales de construcción**, son
vulnerables a **interferencias** y plantean **desafíos de seguridad** y de **compartición de
medio**.
### Tipos de medios inalámbricos:
Los estándares de **IEEE** y de la industria de las telecomunicaciones para comunicaciones
inalámbricas abarcan la capa física y de enlace de datos, definiendo especificaciones en áreas
como codificación de señales a radio, frecuencia e intensidad de transmisión, requisitos de
recepción y decodificación de señales, y diseño de antenas. Aquí están los **principales**
estándares inalámbricos:
1. **Wi-Fi** (IEEE 802.11): Tecnología para LAN inalámbrica (**WLAN**) que emplea
acceso múltiple por detección de portadora con prevención de colisiones (**CSMA/CA**).
Wi-Fi se utiliza ampliamente con dispositivos **WLAN** certificados basados en el estándar
IEEE 802.11.
1. **Bluetooth** (IEEE 802.15): Estándar para redes de área personal inalámbrica
(**WPAN**) conocido como "Bluetooth", que utiliza un proceso de emparejamiento de
dispositivos para distancias de 1 a 100 metros.
1. **WiMAX** (IEEE 802.16): También conocido como Interoperabilidad Mundial para el
Acceso por Microondas (**WiMAX**), utiliza una topología punto a multipunto para proporcionar
acceso inalámbrico de ancho de banda.
1. **Zigbee** (IEEE 802.15.4): Especificación para comunicaciones de baja velocidad y
potencia, ideal para aplicaciones con corto alcance, baja velocidad de datos y larga duración de
batería. Se utiliza en entornos industriales e Internet de las cosas (**IoT**), como interruptores
inalámbricos y recopilación de datos de dispositivos médicos.
### LAN inalámbrica:
La implementación común de tecnología inalámbrica **permite** la conexión de dispositivos a
través de una LAN inalámbrica. Para esto, se necesitan los siguientes dispositivos de red:
- **Punto de acceso inalámbrico (AP)**: Concentra las señales inalámbricas de los
usuarios y se conecta a la infraestructura de red existente basada en cobre, como **Ethernet**.
En dispositivos domésticos y de pequeñas empresas, los routers inalámbricos integran las
funciones de un router, switch y punto de acceso en **un solo dispositivo**.
- **Adaptadores NIC inalámbricos**: Proporcionan capacidad de comunicaciones
inalámbricas a los hosts de la red.
Con la evolución de la tecnología, han surgido diversos estándares **WLAN** basados en
**Ethernet**. Al adquirir dispositivos inalámbricos, es importante garantizar la compatibilidad e
interoperabilidad. Los beneficios de las tecnologías inalámbricas de comunicación de datos son
notables, especialmente en la reducción de costos de cableado y en la conveniencia de la
movilidad del host. No obstante, se debe implementar seguridad rigurosa para proteger las
**WLAN** contra el acceso no autorizado y posibles amenazas.