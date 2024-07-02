---
title: Capa de transporte
date: 2024-02-06 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Servicios en red]
tags: [redes locales, teoría, tsmr]
img_path: /assets/img/transporte/
---

### Función de la Capa de Transporte
La Capa de Transporte juega un papel clave al facilitar el intercambio de datos generados por programas de capa de aplicación entre los hosts de origen y destino. Su tarea principal es gestionar las comunicaciones lógicas entre aplicaciones que se ejecutan en diferentes hosts. Esto implica acciones como establecer sesiones temporales entre dos hosts y asegurar la transmisión confiable de información para una aplicación específica.
En el modelo TCP/IP, la Capa de Transporte se muestra como el puente entre la capa de aplicación y las capas inferiores, encargadas de la transmisión a través de la red. En un diagrama, se ilustra cómo los dispositivos utilizan esta capa para mover datos entre aplicaciones.
La Capa de Transporte facilita el traslado de datos entre aplicaciones en dispositivos de la red, sin necesidad de conocer detalles como el tipo de host de destino, el medio de transmisión, la ruta específica de los datos, la congestión en un enlace o el tamaño de la red.
Dentro de esta capa, encontramos dos protocolos esenciales: el Protocolo de Control de Transmisión (TCP), que garantiza una transmisión más detallada y fiable, y el Protocolo de Datagramas de Usuario (UDP), que ofrece una transmisión más ágil pero menos fiable, siendo útil en situaciones específicas.

### Responsabilidades de la Capa de Transporte
* Seguimiento de Conversaciones Individuales: La Capa de Transporte se encarga de hacer un seguimiento de las conversaciones individuales entre aplicaciones en hosts diferentes. Esto implica coordinar el intercambio de datos de manera lógica y asegurar que la información llegue correctamente a su destino.
* Segmentación de Datos y Rearmado de Segmentos: La capa divide los datos en segmentos más pequeños para facilitar la transmisión a través de la red. Además, se encarga de volver a ensamblar estos segmentos en el destino para reconstruir la información original.
* Agregar Información de Encabezado: Agrega información de encabezado a los datos antes de transmitirlos. Esta información incluye detalles como la fuente, el destino, y la secuencia de datos. El encabezado es esencial para el enrutamiento y la entrega correcta de la información.
* Identificación de las Aplicaciones: La Capa de Transporte identifica las aplicaciones asociadas con los datos que está gestionando. Esto permite diferenciar y dirigir los datos a las aplicaciones correspondientes en los hosts de origen y destino.
* Multiplexión de Conversaciones: Realiza la multiplexión, que es la gestión simultánea de múltiples conversaciones o flujos de datos. La capa asigna recursos y prioridades para asegurar la transmisión eficiente de datos de diversas aplicaciones a través de un mismo canal de comunicación.
Estas responsabilidades son esenciales para garantizar la eficiencia, la integridad y la entrega precisa de los datos en entornos de red.

### Protocolos de la Capa de Transporte
Aunque el protocolo IP se encarga de la estructura, direccionamiento y enrutamiento de paquetes, no se involucra directamente en la forma en que se realiza la entrega o el transporte de esos paquetes.
Es aquí donde entran en juego los protocolos de la capa de transporte, que especifican cómo se mueven los mensajes entre hosts y se encargan de cumplir con los requisitos de confiabilidad en una conversación. La capa de transporte incluye dos protocolos clave: TCP (Protocolo de Control de Transmisión) y UDP (Protocolo de Datagramas de Usuario).
Debido a que diferentes aplicaciones tienen distintos niveles de confiabilidad en el transporte de datos, TCP/IP proporciona estos dos protocolos en la capa de transporte para adaptarse a esas necesidades específicas. La figura asociada muestra cómo TCP y UDP coexisten en esta capa, destacando la capacidad del modelo para manejar eficientemente diversos tipos de comunicación.
 
### Protocolo de Control de Transmisión (TCP)
Mientras que IP se encarga de la estructura y el enrutamiento de paquetes, no se preocupa por garantizar la entrega ni por decidir si es necesario establecer una conexión entre el remitente y el receptor.
En cambio, el TCP se destaca como un protocolo confiable y completo en la capa de transporte, asegurando que todos los datos enviados lleguen de manera fiable al destino. TCP incorpora campos específicos que aseguran la entrega de los datos de la aplicación, aunque esto requiera un procesamiento adicional tanto en los hosts de envío como en los de recepción.
Un aspecto clave a tener en cuenta es que TCP divide los datos en segmentos, similar al seguimiento de paquetes desde el origen hasta el destino. Esta división permite que un cliente verifique en tiempo real el orden de entrega cuando un envío se divide en varios paquetes.
Las funciones esenciales de TCP para proporcionar confiabilidad y control de flujo incluyen enumerar y rastrear segmentos de datos, confirmar la recepción de datos, retransmitir información no reconocida después de un tiempo determinado, secuenciar datos desordenados y enviar datos a una velocidad eficiente aceptable por el receptor.
Para mantener el estado de una conversación y realizar un seguimiento de la información, TCP establece inicialmente una conexión entre el remitente y el receptor, por lo que se le conoce como un protocolo orientado a la conexión. La animación asociada ilustra este proceso mediante una conexión a un servidor FTP, donde se inicia una conexión con un protocolo de enlace TCP de 3 vías y se transmiten segmentos de datos junto con confirmaciones.
 
### Protocolo de Datagramas de Usuario (UDP)
UDP es un protocolo de transporte más sencillo que TCP. A diferencia de TCP, no se preocupa por garantizar la entrega segura ni controlar el flujo de datos, lo que se traduce en un encabezado más ligero. Esto permite que los datagramas UDP se procesen de manera más rápida, ya que no hay necesidad de gestionar la confiabilidad y el control de flujo en los procesos de envío y recepción.
Es crucial destacar que UDP divide los datos en datagramas, que son como segmentos más simples. A diferencia de TCP, UDP opera sin la necesidad de establecer una conexión previa, y debido a que no se preocupa por la confiabilidad ni el control de flujo, se le conoce como un protocolo sin conexión. La ausencia de seguimiento de la información entre el cliente y el servidor lleva a que UDP también se denomine un protocolo sin estado.
UDP se considera un protocolo de "mejor esfuerzo" porque no hay confirmación de que los datos hayan llegado al destino. De manera análoga, enviar datos con UDP es como enviar una carta común por correo sin obtener confirmación de entrega. En este contexto, no hay procesos en la capa de transporte que informen al remitente sobre el éxito o el fracaso de la entrega.
La animación asociada ilustra cómo los datagramas UDP se transmiten del remitente al receptor. En esta situación, UDP se asemeja a enviar una carta regular sin registro, donde el remitente no tiene certeza sobre la recepción y no hay mecanismos para informar sobre el estado de la entrega.

### Protocolo de la capa de transporte correcto para la aplicación adecuada
La elección entre UDP (Protocolo de Datagramas de Usuario) y TCP (Protocolo de Control de Transmisión) depende de las necesidades específicas de cada aplicación. UDP es ideal cuando algunas pérdidas de datos son aceptables, pero se requiere una transmisión rápida, como en aplicaciones de Voz sobre IP (VoIP) o servicios de solicitud-respuesta como el sistema de nombres de dominio (DNS). Además, UDP es adecuado para la transmisión de video y audio en tiempo real, donde la pérdida ocasional de datos no es perceptible para el usuario.
En cambio, TCP es la elección cuando es esencial que todos los datos lleguen y se procesen en orden. Aplicaciones críticas, como bases de datos, navegadores web y clientes de correo electrónico, necesitan la entrega completa y precisa de datos, por lo que TCP se utiliza en estas situaciones. Es especialmente importante en transacciones en línea, como las operaciones bancarias, donde la integridad de la información es crucial.
Los desarrolladores deben considerar detenidamente los requisitos específicos de sus aplicaciones al decidir entre TCP y UDP. Por lo general, aplicaciones que transmiten audio y video almacenado prefieren TCP para garantizar la integridad de los datos. En contraste, las aplicaciones de videoconferencia pueden optar por UDP para evitar retrasos en la transmisión. La elección entre TCP y UDP se basa en factores como la tolerancia a la pérdida de datos, la prioridad de la entrega y la naturaleza única de cada aplicación. La figura proporciona una representación visual de las diferencias entre UDP y TCP.

# Descripción general de TCP:
### Características de TCP
TCP (Protocolo de Control de Transmisión) es un protocolo de la capa de transporte que se diferencia de UDP al proporcionar una conexión confiable y orientada a la sesión. Además de las funciones básicas de dividir y reensamblar datos, TCP ofrece servicios adicionales:
1.	Establecimiento de Sesión:
-	TCP, al ser orientado a la conexión, inicia y acuerda una conexión permanente entre los dispositivos antes de comenzar la transmisión de datos.
-	Durante este proceso, se negocia la cantidad de tráfico que puede transmitirse en un momento específico, permitiendo un control preciso de la comunicación.
2.	Entrega Confiable:
-	TCP se asegura de que cada segmento enviado por la fuente llegue de manera segura al destino.
-	Si hay segmentos corruptos o perdidos durante la transmisión, TCP se encarga de retransmitirlos para garantizar la integridad de la entrega.
3.	Entrega en el Mismo Orden:
-	Utilizando numeración y secuenciación de segmentos, TCP asegura que los datos se reensamblen en el orden correcto en el destino, incluso si llegan desordenados debido a las diversas rutas de red.
4.	Control de Flujo:
-	TCP detecta limitaciones de recursos en los hosts de la red y, cuando es necesario, solicita a la aplicación emisora reducir la velocidad del flujo de datos.
-	El control de flujo regula la cantidad de datos transmitidos, evitando la necesidad de retransmitir datos cuando los recursos del host receptor están bajo presión.

Estos servicios hacen que TCP sea una elección apropiada para aplicaciones que requieren confiabilidad, entrega ordenada y regulación del flujo de datos. Para obtener detalles adicionales sobre TCP, se puede buscar el RFC 793 en Internet.

### Encabezado TCP
TCP, siendo un protocolo con estado, mantiene un registro del estado de la sesión de comunicación. Este seguimiento implica el registro de la información enviada y reconocida durante la sesión. La sesión con estado inicia con el establecimiento de la conexión y concluye con la finalización de la sesión.
Cada segmento TCP agrega 20 bytes (equivalentes a 160 bits) de sobrecarga al encapsular los datos de la capa de aplicación. La figura ilustra los campos presentes en un encabezado TCP.

### Aplicaciones que utilizan TCP
TCP desempeña un papel crucial al manejar diversas tareas asociadas con la transmisión de datos en el conjunto de protocolos TCP/IP. Se encarga de dividir el flujo de datos en segmentos, proporciona confiabilidad, controla el flujo y reordena segmentos, liberando a las aplicaciones de estas responsabilidades. Las aplicaciones, como HTTP, FTP, SMTP y SSH, pueden simplemente enviar su flujo de datos a la capa de transporte y aprovechar los servicios proporcionados por TCP. La figura ilustra cómo estas aplicaciones se conectan a través de TCP, demostrando la dirección bidireccional desde las aplicaciones hacia TCP y luego desde TCP hacia IP.
 
# Visión general de UDP:
### Características de UDP
UDP es un protocolo de transporte "mejor esfuerzo" que, a diferencia de TCP, no ofrece confiabilidad ni control de flujo. Es liviano y se caracteriza por reconstruir datos en el orden de recepción, no reenviar segmentos perdidos, no establecer sesiones y no informar sobre la disponibilidad de recursos. Es adecuado para situaciones donde la pérdida ocasional de datos es aceptable. Consulte el RFC para más detalles sobre UDP.

### Encabezado UDP
UDP, al ser un protocolo sin estado, no rastrea el estado de la sesión de comunicación ni en el cliente ni en el servidor. La confiabilidad en la transmisión de datos a través de UDP debe ser gestionada por la aplicación.
Para transmitir video en vivo y voz de manera eficiente, donde la velocidad de flujo de datos es crucial, UDP es ideal. Las aplicaciones de video y voz en vivo, que pueden tolerar cierta pérdida de datos, se adaptan bien a UDP.
Los bloques de comunicación en UDP se llaman datagramas o segmentos, enviados como "mejor esfuerzo" por el protocolo de transporte. El encabezado UDP es más simple que el de TCP, con solo cuatro campos y un total de 8 bytes (64 bits). Los campos incluyen puerto de origen, puerto de destino, longitud y suma de comprobación. La figura muestra estos campos en un encabezado UDP, junto con los datos de la capa de aplicación sin encabezado, en un diagrama de datagramas UDP.

### Aplicaciones que utilizan UDP
UDP es más adecuado para tres tipos específicos de aplicaciones:
1.	Video y Multimedia en Vivo:
-	Aplicaciones que pueden tolerar cierta pérdida de datos y requieren una transmisión rápida. Ejemplos: VoIP y transmisión de video en vivo.
2.	Solicitudes y Respuestas Simples:
-	Aplicaciones con transacciones simples, donde un host envía una solicitud y puede o no recibir una respuesta. Ejemplos: DNS y DHCP.
3.	Manejo Interno de Confiabilidad:
-	Comunicaciones unidireccionales donde el control de flujo, la detección de errores, los reconocimientos y la recuperación de errores no son necesarios o pueden ser gestionados por la aplicación. Ejemplos: SNMP y TFTP.

# Números de puerto:
### Comunicaciones Múltiples Separadas
Tanto TCP como UDP utilizan números de puerto para gestionar múltiples conversaciones simultáneas. Los campos de encabezado TCP y UDP contienen números de puerto de origen y destino, cada uno de 2 bytes. El número de puerto de origen se asocia con la aplicación de origen en el host local, mientras que el número de puerto de destino se asocia con la aplicación de destino en el host remoto. Este enfoque permite establecer varias conversaciones simultáneas, y el número de puerto de destino identifica el tipo de servicio solicitado al servidor. Por ejemplo, el puerto 80 indica servicios web. Un servidor puede ofrecer múltiples servicios simultáneamente en diferentes puertos.

### Pares de Sockets
En la comunicación de red, los pares de sockets juegan un papel esencial. Los puertos de origen y destino, combinados con las direcciones IP, forman lo que se conoce como socket. Este último identifica la combinación única de la dirección IP y el número de puerto asociado, ya sea para la dirección de origen o destino.
En un ejemplo práctico, un PC realiza solicitudes simultáneas de servicios FTP y web al mismo servidor de destino. Cada solicitud utiliza direcciones MAC y IP, junto con números de puerto de origen y destino específicos. Estos elementos forman sockets distintos que identifican las conexiones FTP y web.
Los sockets permiten a los procesos en un cliente diferenciarse y facilitan la identificación de diversas conexiones en un servidor. El número de puerto de origen actúa como dirección de retorno para la aplicación solicitante, permitiendo que la capa de transporte dirija las respuestas a la aplicación correcta. En conjunto, estos pares de sockets, como "192.168.1.5:1099, 192.168.1.7:80", son fundamentales para el direccionamiento preciso en la red.

### Grupos de números de puerto
La Autoridad de Números Asignados de Internet (IANA) administra los números de puerto de 16 bits, dividiéndolos en tres grupos:
1.	Puertos Bien Conocidos (0 a 1,023): Reservados para servicios comunes como navegadores web y correo electrónico.
2.	Puertos Registrados (1,024 a 49,151): Asignados a entidades para aplicaciones específicas, ej. Cisco RADIUS.
3.	Puertos Privados/Dinámicos (49,152 a 65,535): Conocidos como puertos efímeros, asignados dinámicamente al iniciar conexiones.

Ejemplos de Puertos Bien Conocidos:
•	FTP Datos: 20 (TCP)
•	FTP Control: 21 (TCP)
•	SSH: 22 (TCP)
•	Telnet: 23 (TCP)
•	SMTP: 25 (TCP)
•	DNS: 53 (UDP, TCP)
•	DHCP - Servidor: 67 (UDP)
•	DHCP - Cliente: 68 (UDP)
•	TFTP: 69 (UDP)
•	HTTP: 80 (TCP)
•	POP3: 110 (TCP)
•	IMAP: 143 (TCP)
•	SNMP: 161 (UDP)
•	HTTPS: 443 (TCP)
Algunas aplicaciones usan tanto TCP como UDP; por ejemplo, DNS usa UDP para solicitudes y TCP para comunicación entre servidores DNS. El registro completo está disponible en el sitio web de IANA.

### El comando netstat
Netstat es una herramienta esencial para examinar las conexiones TCP activas en un host de red y puede ayudar a identificar posibles amenazas de seguridad. Al ingresar el comando "netstat", se obtiene una lista detallada de conexiones TCP activas, que incluyen información sobre los protocolos, direcciones local y extranjera, números de puerto y estado de la conexión. El comando también puede ejecutarse con la opción "-n" para mostrar direcciones IP y números de puerto en su forma numérica, sin resolver nombres de dominio ni aplicaciones conocidas.

# Proceso de comunicación TCP:
### Procesos del Servidor TCP
En TCP, cada proceso de aplicación en un servidor se asocia con un número de puerto, que puede asignarse automáticamente o configurarse manualmente. Un servidor no puede tener dos servicios con el mismo número de puerto. Una aplicación de servidor activa asignada a un puerto se considera "abierta", lo que significa que la capa de transporte acepta y procesa los segmentos dirigidos a ese puerto. Pueden existir varios puertos abiertos simultáneamente en un servidor, uno para cada aplicación de servidor activa. En el proceso de comunicación TCP, los clientes envían solicitudes a puertos de destino específicos, y el servidor responde a puertos de origen correspondientes en los clientes.

### Establecimiento de Conexiones TCP
En las conexiones TCP, el proceso de establecimiento de conexión es similar a saludar al conocerse. El cliente host inicia la conexión con el servidor a través del proceso de enlace de tres vías, que consta de los siguientes pasos:
1.	Paso 1 (SYN): El cliente envía un mensaje de solicitud (SYN) al servidor para iniciar la conexión.
2.	Paso 2 (ACK y SYN): El servidor responde con un mensaje de confirmación (ACK) junto con su propia solicitud (SYN) al cliente.
3.	Paso 3 (ACK): El cliente envía un mensaje de confirmación (ACK) al servidor, finalizando el proceso de enlace de tres vías y estableciendo la conexión TCP.

### Terminación de Sesión
Para cerrar una conexión TCP, se utiliza el marcador de control de finalización (FIN) en el encabezado del segmento. El proceso de finalización de una sesión TCP de dos vías implica cuatro pasos, que son los siguientes:
1.	Paso 1 (FIN): Se envía un segmento con el marcador FIN para indicar la intención de cerrar la conexión.
2.	Paso 2 (ACK): El receptor envía un segmento de reconocimiento (ACK) en respuesta al segmento FIN, indicando que ha recibido la solicitud de finalización.
3.	Paso 3 (FIN): El receptor, que también puede ser el iniciador de la terminación, envía un segmento con FIN para indicar su propia intención de cerrar la conexión.
4.	Paso 4 (ACK): El iniciador original envía un segmento de reconocimiento (ACK) en respuesta al segundo segmento FIN, completando así el proceso de finalización de la sesión TCP de dos vías.
 
### Análisis del enlace de tres vías de TCP
TCP, siendo un protocolo full-duplex, realiza el seguimiento de cada segmento de datos dentro de una sesión y utiliza un enlace de tres vías para establecer la conexión. El proceso de enlace de tres vías utiliza seis bits de control en el encabezado TCP, conocidos como marcadores o banderas, que cumplen funciones específicas:
*	URG (Urgent): Indica que el campo de puntero urgente es significativo.
*	ACK (Acknowledgment): Utilizado en el establecimiento de conexión y la terminación de la sesión para indicar el reconocimiento de datos recibidos.
*	PSH (Push): Indica la función de empuje, que sugiere a la capa de transporte que entregue los datos al destinatario tan pronto como estén disponibles.
*	RST (Reset): Restablece la conexión en caso de error o tiempo de espera.
*	SYN (Synchronize): Sincroniza números de secuencia durante el establecimiento de la conexión.
*	FIN (Finish): Indica que el remitente no enviará más datos y se utiliza en la terminación de la sesión.
Estos indicadores informan sobre el progreso y estado de la conexión TCP, y la secuencia de estos indicadores en el apretón de manos de tres vías permite establecer y finalizar la comunicación de manera confiable.

# Confiabilidad y control de flujo:
### Fiabilidad de TCP: Entrega Garantizada y Ordenada
TCP destaca como el protocolo ideal para ciertas aplicaciones debido a sus capacidades para reenviar paquetes descartados, numerar paquetes y mantener un flujo de paquetes eficiente, a diferencia de UDP. Estas características son clave para garantizar la fiabilidad y el orden en la transmisión de datos.
Cuando los segmentos TCP no alcanzan su destino o llegan desordenados, TCP emplea números de secuencia en el encabezado de cada paquete. Durante la configuración de la sesión, se establece un número de secuencia inicial (ISN), representando el valor inicial de los bytes transmitidos. A medida que los datos fluyen, el número de secuencia aumenta según la cantidad de bytes transmitidos, permitiendo la identificación única y el reconocimiento de cada segmento.
El ISN, aunque inicia como un número aleatorio, no comienza en uno para evitar ciertos ataques maliciosos. Este método de numeración facilita la identificación y reconstrucción de segmentos perdidos, incluso si toman rutas diferentes o llegan desordenados al destino. La capacidad de reordenar y reensamblar los segmentos TCP asegura la integridad y coherencia de los datos en la capa de aplicación.
 
### Fiabilidad de TCP: Pérdida y Retransmisión de Datos
TCP ofrece mecanismos para gestionar la pérdida de segmentos, incluyendo la retransmisión de datos no reconocidos. El número de secuencia (SEQ) y el número de acuse de recibo (ACK) colaboran para confirmar la recepción de los datos transmitidos. Anteriormente, TCP solo podía reconocer el siguiente byte esperado, lo que resultaba en la retransmisión de segmentos innecesarios.
Para abordar esto, algunos sistemas operativos implementan la característica TCP opcional llamada reconocimiento selectivo (SACK), que permite al receptor reconocer explícitamente los segmentos recibidos, incluyendo segmentos discontinuos. Si ambos hosts admiten SACK, el emisor solo retransmite los datos faltantes, evitando duplicaciones innecesarias y mejorando la eficiencia.
El reconocimiento selectivo se ilustra con un ejemplo en el que, tras el envío de 10 segmentos, solo los segmentos 3 y 4 no llegan. El receptor con SACK envía un ACK 3 y un SACK 5-10, indicando que ha recibido los segmentos 1 y 2, y de manera selectiva, los segmentos 5 a 10. El emisor solo necesita retransmitir los segmentos 3 y 4.
TCP utiliza temporizadores para determinar cuánto tiempo esperar antes de retransmitir un segmento no reconocido. Estos mecanismos de control de pérdidas y retransmisión son fundamentales para mantener la integridad y la eficiencia en las transmisiones TCP.

### Control de Flujo de TCP: Tamaño de la Ventana y Reconocimientos
TCP incorpora estrategias de control de flujo para asegurar una transmisión fiable al ajustar la velocidad del flujo de datos entre el emisor y el receptor. Este ajuste se realiza mediante el "tamaño de la ventana", un campo de 16 bits en el encabezado TCP.
En un ejemplo, con un tamaño de ventana de 10,000 bytes y una PC A que envía segmentos de hasta 1,460 bytes, la ventana de envío de la PC A se adapta según los acuses de recibo del PC B, creando así una "ventana deslizante". La ventana de envío indica cuántos bytes el receptor puede procesar simultáneamente.
La configuración inicial de la ventana se establece al inicio de la sesión TCP, y el emisor ajusta la cantidad de datos enviados según la ventana del receptor. A medida que el receptor procesa los bytes, envía acuses de recibo, permitiendo al emisor ajustar su ventana de envío en consecuencia.
El concepto de ajuste continuo de la ventana de envío del emisor según las confirmaciones del receptor se denomina "ventanas deslizantes". Este enfoque optimiza la transmisión de datos, permitiendo al emisor enviar segmentos de manera continua mientras el receptor acusa recibo de los segmentos anteriores.
 
### Control de Flujo TCP - Tamaño Máximo de Segmento (MSS)
En el contexto del Control de Flujo TCP y el Tamaño Máximo de Segmento (MSS), se destaca que la fuente transmite 1,460 bytes en cada segmento TCP. El MSS, parte del campo de opciones del encabezado TCP, indica la máxima cantidad de datos que un dispositivo puede recibir en un solo segmento TCP, excluyendo el encabezado TCP. Se enfatiza que el MSS se establece típicamente durante el protocolo de enlace de tres vías.
En IPv4, un MSS común es de 1,460 bytes. Los hosts determinan este valor restando los encabezados IP y TCP de la Máxima Unidad de Transmisión (MTU) de Ethernet. Con un MTU predeterminado de 1500 bytes en Ethernet, al restar los encabezados IP (20 bytes) y TCP (20 bytes), se obtiene un MSS de 1460 bytes. Se presenta un diagrama que ilustra un marco Ethernet completo, con una MTU de 1500 bytes, siendo 20 bytes el encabezado IP, 20 bytes el encabezado TCP, y 1460 bytes la carga útil del TCP MSS.

### Control de flujo de TCP: Prevención de Congestiones
Cuando se produce congestión en una red, los routers sobrecargados pueden comenzar a descartar paquetes, incluyendo aquellos que contienen segmentos TCP. Si estos segmentos no llegan a su destino y no son confirmados, el origen, al determinar la tasa de pérdida, puede asumir la presencia de congestión en la red.
Para gestionar la congestión, TCP implementa mecanismos, temporizadores y algoritmos específicos. Cuando se detecta congestión, el origen puede reducir la cantidad de bytes enviados antes de recibir un reconocimiento. En la ilustración, se muestra cómo PC A, al notar congestión, ajusta la cantidad de bytes enviados antes de obtener un acuse de recibo de PC B.
Es esencial destacar que es el origen el que realiza la reducción de bytes no reconocidos, y no el tamaño de ventana determinado por el destino. Cabe mencionar que los detalles específicos de los mecanismos y algoritmos de manejo de la congestión están fuera del alcance de este curso.

# Comunicación UDP:
### Comparación de baja sobrecarga y confiabilidad de UDP
UDP es ideal para comunicaciones que requieren rapidez, como VoIP. A diferencia de TCP, UDP no establece una conexión y proporciona un transporte de datos con baja sobrecarga gracias a su pequeño encabezado de datagrama, sin tráfico de administración de red. Esto se ilustra con un remitente de host que envía datos de voz y video mediante UDP, sin necesidad de una conexión previamente negociada.
 
### Reensamblaje de datagramas de UDP
Al igual que los segmentos en TCP, los datagramas enviados mediante UDP a menudo siguen diferentes rutas y pueden llegar desordenados. A diferencia de TCP, UDP no realiza un seguimiento de los números de secuencia ni reordena los datagramas. UDP simplemente reensambla los datos en el orden en que se recibieron y los entrega a la aplicación. Si la secuencia de datos es crucial para la aplicación, esta debe identificar la secuencia correcta y determinar cómo procesar los datos. La falta de seguimiento y reordenamiento en UDP se ilustra con datagramas enviados en orden pero que llegan fuera de servicio debido a las diferentes rutas que pueden tomar al llegar al destino.

### Procesos y solicitudes del servidor UDP
Las aplicaciones de servidor basadas en UDP se les asignan números de puerto conocidos o registrados. Estos procesos, al ejecutarse en un servidor, aceptan datos coincidentes con el número de puerto asignado. Cuando UDP recibe un datagrama destinado a uno de esos puertos, envía los datos de aplicación a la aplicación correspondiente según su número de puerto. En la figura, se muestra un servidor UDP que escucha solicitudes, donde una aplicación de servidor RADIUS utiliza UDP para recibir solicitudes en el puerto 1812, mientras que las solicitudes DNS del cliente se reciben en el puerto 53.

### Procesos de cliente UDP
En la comunicación cliente-servidor con UDP, la aplicación cliente inicia la comunicación y selecciona dinámicamente un número de puerto como puerto de origen. El puerto de destino suele ser el número de puerto asignado al proceso de servidor. Después de seleccionar los puertos, se utilizan en el encabezado de todos los datagramas de la transacción. Para la devolución de datos del servidor al cliente, se invierten los números de puerto de origen y destino en el encabezado del datagrama. En la ilustración, se muestra un ejemplo con dos hosts solicitando servicios al servidor DNS y RADIUS.