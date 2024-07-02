---
title: Comandos switch CISCO
date: 2023-10-10 12:00:00 +0100
categories: [Sistemas Microinformáticos y Redes, Redes Locales]
tags: [redes locales, teoría, tsmr]
img_path: /assets/img/CISCO/
---

# Introducción

Los conmutadores (switches) de Cisco utilizan un sistema operativo llamado Cisco IOS (Internetwork Operating System), que ofrece una amplia variedad de comandos para configurar y administrar estos dispositivos de red.

## Comandos

Pasar a modo superusuario
```
Switch> enable
Switch#
```

Cambiar el nombre de un dispositivo
```
Switch# configure terminal
Switch(config)# hostname *Sw-Floor-1*
Sw-Floor-1(config)#
```

Establecer contraseña para el usuario estándar
```
Sw-Floor-1# configure terminal
Sw-Floor-1(config)# line console 0
Sw-Floor-1(config-line)# password *cisco*
Sw-Floor-1(config-line)# login
SW-Floor-1(config-line)# end
Sw-Floor-1#
```

Para asegurar el acceso privilegiado a superusuario
```
Sw-Floor-1# configure terminal
Sw-Floor-1(config)# enable secret *class*
Sw-Floor-1(config)# exit
Sw-Floor-1#
```

Proteger las líneas de conexión
```
Sw-Floor-1# configure terminal
Sw-Floor-1(config)# line vty 0 15
Sw-Floor-1(config-line)# password *cisco* 
Sw-Floor-1(config-line)# login 
SW-Floor-1(config-line)# end
Sw-Floor-1#
```

Encriptación de las contraeñas
```
Sw-Floor-1# configure terminal
Sw-Floor-1(config)# service password-encryption
Sw-Floor-1(config)#
```

Estado de nuestro switch
```
show running-config
```

Mensaje de aviso
```
Sw-Floor-1# configure terminal
Sw-Floor-1(config)# banner motd *#Authorized Access Only#*
```

Establecer IP en el switch
```
CCNA# configure terminal
CCNA(config)# interface vlan 1
CCNA(config-if)# ip address *192.168.1.100 255.255.255.0*
CCNA(config-if)# no shutdown
00:35:07: %LINK-3-UPDOWN: Interface Vlan1, changed state to up
00:35:08: %LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed
state to up
CCNA(config-if)# exit
CCNA(config)# ip default-gateway *192.168.1.1*
```

Configuración DHCP
```
CCNA# show dhcp lease
Temp IP addr: 192.168.1.101 for peer on Interface: Vlan1
Temp sub net mask: 255.255.255.0
   DHCP Lease server: 192.168.1.1, state: 3 Bound
   DHCP transaction id: 1966
   Lease: 86400 secs, Renewal: 43200 secs, Rebind: 75600 secs
Temp default-gateway addr: 192.168.1.1
   Next timer fires after: 11:59:45
   Retry count: 0 Client-ID: cisco-0019.e86a.6fc0-Vl1
   Hostname: Emma
CCNA# show interfaces vlan 1
Vlan1 is up, line protocol is up
   Hardware is EtherSVI, address is 0019.e86a.6fc0 (bia 0019.e86a.6fc0)
   Internet address is 192.168.1.101/24
   MTU 1500 bytes, BW 1000000 Kbit, DLY 10 usec,
      reliability 255/255, txload 1/255, rxload 1/255
! lines omitted for brevity
CCNA# show ip default-gateway
192.168.1.1
```

Conexión por SSH
```
# Configuración de hostname y nombre de dominio
Switch(config)#hostname *eclassvirtual-sw*
eclassvirtual-sw(config)#ip domain-name *eclassvirtual.com*

# Generación de llaves RSA
eclassvirtual-sw(config)# crypto key generate rsa

# Cambiar SSH versión 1 a la 2 (la versión 2 es más segura)
eclassvirtual-sw(config)#ip ssh version 2

# Configuración de Line VTY
eclassvirtual-sw(config)# line vty 0 15
eclassvirtual-sw(config-line)# transport input ssh
eclassvirtual-sw(config-line)# login local

# Crear nombre de usuario y password
eclassvirtual-sw(config)# username *eclassvirtual* privilege 15 secret *cisco123*

# Habilitar enable secret
eclassvirtual-sw(config)# enable secret *cisco123*
```

Revisión de conexión SSH en el Switch
```
eclassvirtual-sw# show ssh
```

Habilitar SSH en Router Cisco
```
Router#conf t
Router(config)#hostname *eclassvirtual-router*
eclassvirtual-router(config)#interface vlan 1
eclassvirtual-router(config-if)#ip address *192.168.0.1 255.255.255.0*
eclassvirtual-router(config-if)#no shutdown
eclassvirtual-router(config-if)#exit
eclassvirtual-router (config)#ip domain-name *cisco.com*
eclassvirtual-router(config)#username eclassvirtual privilege 15 secret *cisco123*
eclassvirtual-router(config)#crypto key generate rsa
The name for the keys will be: eclasvirtual-router.cisco.com Choose the size of the key modulus in the range of 360 to 2048 for your General Purpose Keys. Choosing a key modulus greater than 512 may take a few minutes. How many bits in the modulus [512]: 2048 % Generating 2048 bit RSA keys, keys will be non-exportable…[OK]
eclassvirtual-router(config)#ip ssh version 2
eclassvirtual-router(config)#enable secret *cisco123*
eclassvirtual-router(config)#line vty 0 15
eclassvirtual-router(config-line)#transport input ssh
eclassvirtual-router(config-line)#login local
eclassvirtual-router#show ip ssh C:\>ssh -l eclassvirtual 192.168.0.1 Open Password:
```

## Creación de VLAN 

Entramos en superusuario:
```console
enable
```
Entramos en la configuración del terminal:
```console
configure terminal
```
Creamos la VLAN 10 y le ponemos nombre:
```console
vlan 10
name Mesa1
exit
```
Creamos la VLAN 20 y le ponemos nombre:
```console
vlan 20
name Mesa2
exit
```
exit

Mostramos la información pertinente de a las VLANs
```console
show vlan
```

Asignamos que interfaces pertenecen a cada VLAN
```console
configure terminal
interface range f0/10-14
switchport mode access
switchport access vlan 10
exit
```
```console
interface range f0/15-19
switchport mode access
switchport access vlan 20
exit
```