# docs-02-configuracion-red.md
# Configuración de red del servidor

Servidor: ServerPrincipal  
Sistema operativo: Debian 12  

Este servidor actúa como máquina principal del laboratorio y aloja los servicios de red (DHCP y DNS).

---

## Interfaces de red

El servidor dispone de dos interfaces de red:

enp0s3 → NAT (acceso a internet para instalación de paquetes)  
enp0s8 → Red interna del laboratorio (DiegoRed)

---

## Configuración de red

IP del servidor:  
192.168.50.10

Máscara de red:  
255.255.255.0

Red interna:  
192.168.50.0/24

---

## Archivo de configuración

Archivo utilizado:

/etc/network/interfaces

Contenido configurado:
auto lo
iface lo inet loopback

auto enp0s3
iface enp0s3 inet dhcp

auto enp0s8
iface enp0s8 inet static
address 192.168.50.10
netmask 255.255.255.0

---

## Comprobación

Se comprueba la configuración de red del servidor utilizando:
ip a


La interfaz enp0s8 debe mostrar la dirección:

192.168.50.10
