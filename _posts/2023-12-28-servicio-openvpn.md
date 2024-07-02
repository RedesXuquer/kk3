---
title: Montaje del servicio OpenVPN
date: 2023-12-28 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Servicios en red]
tags: [redes locales, teoría, smr]
img_path: /assets/img/openvpn/linux/  
---

![Alt text](image.png)

**Una red privada virtual (VPN)** es una tecnología que permite establecer una conexión segura y cifrada entre tu dispositivo (como una computadora, teléfono o tablet) y un servidor remoto. El propósito principal de una VPN es proteger tu privacidad y seguridad en línea al cifrar el tráfico de datos entre tu dispositivo y el servidor al que te conectas. Aquí hay una explicación más detallada sobre el uso de una VPN:

1. **Cifrado de Datos:**
   - Cuando te conectas a una VPN, tu tráfico de internet se cifra. Esto significa que la información que envías y recibes mientras estás en línea se transforma en un formato ilegible para cualquiera que intente interceptarla.

2. **Privacidad y Anonimato:**
   - La VPN oculta tu dirección IP real y asigna una nueva dirección IP proporcionada por el servidor al que te conectas. Esto ayuda a mantener tu anonimato en línea, ya que los sitios web y servicios a los que te conectas solo verán la dirección IP de la VPN.

3. **Acceso a Redes Restringidas:**
   - Al conectarte a un servidor en una ubicación específica, puedes eludir las restricciones geográficas impuestas por algunos servicios en línea. Por ejemplo, puedes acceder a contenido bloqueado en tu región.

4. **Seguridad en Redes Públicas:**
   - Cuando te conectas a una red Wi-Fi pública, como la de un café o aeropuerto, tu conexión puede ser vulnerable. Una VPN protege tus datos en estas situaciones al cifrar la comunicación, evitando que terceros accedan a tu información.

5. **Evitar la Monitorización del Proveedor de Internet:**
   - Tu proveedor de servicios de internet (ISP) puede rastrear tu actividad en línea. Al usar una VPN, puedes dificultar que el ISP monitoree tus actividades, ya que solo verá la conexión cifrada a la VPN.

6. **Seguridad en Transacciones en Línea:**
   - Las transacciones en línea, como las compras y la banca, están protegidas por el cifrado de la VPN, lo que reduce el riesgo de que terceros accedan a tu información financiera.

7. **Acceso Remoto Seguro:**
   - Las VPN también se utilizan en entornos empresariales para permitir a los empleados acceder de forma segura a la red de la empresa desde ubicaciones remotas.

8. **Protección contra Vigilancia Gubernamental:**
   - En algunos casos, las VPN se utilizan para proteger la privacidad frente a la vigilancia gubernamental. Sin embargo, es importante tener en cuenta que no todas las VPN proporcionan el mismo nivel de anonimato y privacidad.

Es crucial elegir una VPN confiable y respetable, ya que algunas pueden comprometer tu privacidad en lugar de protegerla. Además, ten en cuenta que el uso de una VPN no garantiza el anonimato total, y debes seguir practicando buenas medidas de seguridad en línea.

**OpenVPN: Una Visión General**

[OpenVPN](https://openvpn.net/) es una solución de software de código abierto que proporciona una implementación segura de redes privadas virtuales (VPN). Como protocolo VPN, OpenVPN es conocido por su robustez, flexibilidad y capacidad para operar en una variedad de entornos.

### Características Principales de OpenVPN:

1. **Código Abierto:**
   - OpenVPN es un proyecto de código abierto, lo que significa que su código fuente está disponible para el público. Esto facilita la revisión de seguridad por parte de la comunidad y contribuye a la transparencia del sistema.

2. **Seguridad:**
   - OpenVPN utiliza protocolos y algoritmos criptográficos sólidos para proporcionar una capa segura sobre las conexiones de red. Utiliza tanto el protocolo de seguridad SSL/TLS para la autenticación como el cifrado para proteger la comunicación.

3. **Flexibilidad en la Configuración:**
   - OpenVPN es altamente configurable, lo que permite adaptarse a diversas necesidades y entornos. Puede ser implementado tanto en conexiones punto a punto como en redes más complejas.

4. **Compatibilidad Multiplataforma:**
   - OpenVPN es compatible con una amplia gama de sistemas operativos, incluyendo Windows, Linux, macOS, Android e iOS. Esto facilita su implementación en una variedad de dispositivos y sistemas.

5. **Modos de Funcionamiento:**
   - Ofrece modos de funcionamiento tanto en modo puente como en modo de red. El modo puente permite conectar redes físicas separadas, mientras que el modo de red facilita la conexión de dispositivos individuales a través de una red pública.

6. **Escalabilidad:**
   - OpenVPN es escalable y puede manejar tanto pequeñas implementaciones empresariales como grandes despliegues a nivel de proveedor de servicios. Es adecuado para casos de uso que van desde conexiones remotas de empleados hasta la implementación de VPN a nivel de empresa.

7. **Implementación Segura en Redes Wi-Fi Públicas:**
   - Debido a su capacidad para cifrar el tráfico de datos, OpenVPN es especialmente útil para garantizar la seguridad en redes Wi-Fi públicas, donde la amenaza de accesos no autorizados es mayor.

8. **Comunidad Activa:**
   - OpenVPN cuenta con una comunidad activa de desarrolladores y usuarios que contribuyen al desarrollo continuo de la tecnología. Además del proyecto de código abierto, existe una versión comercial llamada "Access Server" que proporciona una interfaz de usuario web y otras características adicionales.

En resumen, OpenVPN es una opción popular para aquellos que buscan una solución de VPN robusta y altamente personalizable. Su enfoque en la seguridad, la flexibilidad y la compatibilidad multiplataforma lo convierten en una opción sólida para implementaciones tanto a nivel individual como empresarial.

## Empecemos

Entramos en modo superusuario:
```
sudo -s
```

Instalamos ciertas dependencias:
```
apt update && apt -y install ca-certificates wget net-tools gnupg
```

Este tipo de operación es común en sistemas basados en Debian y Ubuntu, donde se utiliza GPG (GNU Privacy Guard) para gestionar claves y firmas de paquetes. 
```
wget https://as-repository.openvpn.net/as-repo-public.asc -qO /etc/apt/trusted.gpg.d/as-repository.asc
```

Añadimos el siguiente repositorio:
```
echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/as-repository.asc] http://as-repository.openvpn.net/as/debian jammy main" >/etc/apt/sources.list.d/openvpn-as-repo.list
```

Instalamos el servidor propiamente dicho:
```
apt update && apt -y install openvpn-as
```

Una vez instalado nos saldrá algo similar a esto:
```
+++++++++++++++++++++++++++++++++++++++++++++++
Access Server 2.13.0 has been successfully installed in /usr/local/openvpn_as
Configuration log file has been written to /usr/local/openvpn_as/init.log


Access Server Web UIs are available here:
Admin  UI: https://192.168.0.201:943/admin
Client UI: https://192.168.0.201:943/
To login please use the "openvpn" account with "80IgjLjNu1O2" password.
(password can be changed on Admin UI)
+++++++++++++++++++++++++++++++++++++++++++++++
```

Una vez lo tengamos todo instalado tenemos que nos dirigimos a nuestro navegador y poner lo siguiente:

https://NUESTRA IP/admin .- Es muy importante poner todo el enlace incluyendo https://

Aparecerá algo como esto, aceptamos y continuamos:

![Alt text](Screenshot_2023-12-28_22-05-43.png)

Como se puede observar tenemos un menú en nuestra parte izquierda, en este manual vamos a añadir usuarios y permitir hacer un NAT a nuestra subred

### Configuramos nuestras subredes

![Alt text](Screenshot_2023-12-28_22-10-08.png)
![Alt text](Screenshot_2023-12-28_22-10-27.png)
### Configuramos el NAT

![Alt text](Screenshot_2023-12-28_22-07-55.png)

Añadimos nuestra subred:

![Alt text](Screenshot_2023-12-28_22-08-19.png)

Guardamos:

![Alt text](Screenshot_2023-12-28_22-08-36.png)

Reiniciamos el servicio:

![Alt text](Screenshot_2023-12-28_22-08-55.png)

### Añadir usuarios

![Alt text](Screenshot_2023-12-29_18-36-32.png)
![Alt text](Screenshot_2023-12-29_18-37-05.png) 

### Conectarnos desde un cliente

![Alt text](<Captura de pantalla 2023-12-29 184303.png>)

![Alt text](<Captura de pantalla 2023-12-29 184317.png>)

![Alt text](<Captura de pantalla 2023-12-29 184344.png>)

![Alt text](<Captura de pantalla 2023-12-29 184402.png>)

Comprobamos:

![Alt text](<Captura de pantalla 2023-12-29 184755.png>)

## Otra forma de configuración a través del script directamente

Nos descargamos el siguiente script
```
wget https://git.io/vpn -O openvpn-install.sh
```

Le damos permisos de ejecución
```
sudo chmod +x openvpn-install.sh
```

Lo instalamos
```
sudo bash openvpn-install.sh
```

Debemos de obtener un salida algo similar a lo siguiente
```
Welcome to this OpenVPN road warrior installer!

This server is behind NAT. What is the public IPv4 address or hostname?
Public IPv4 address / hostname [**Aquí saldrá nuestra IP externa**]: **NUESTRA IP EXTERNA**

Which protocol should OpenVPN use?
   1) UDP (recommended)
   2) TCP
Protocol [1]: 1

What port should OpenVPN listen to?
Port [1194]: 1194

Select a DNS server for the clients:
   1) Current system resolvers
   2) Google
   3) 1.1.1.1
   4) OpenDNS
   5) Quad9
   6) AdGuard
DNS server [1]: 2

Enter a name for the first client:
Name [client]: alumno

OpenVPN installation is ready to begin.
Press any key to continue...
```

Después de esto nos habrá generado un archivo en /root/ con el nombre que le hayamos puesto
```
sudo cp /root/alumno.ovpn /home/alumno/
```

Este archivo se le hacemos llegar a nuestro cliente y probamos