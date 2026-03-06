# docs-02-configuracion-red.md
# Configuración de red del servidor

Servidor: ServerPrincipal  
Sistema operativo: Debian 12

## Interfaces

enp0s3 → NAT (internet)

enp0s8 → red interna (DiegoRed)

## Configuración

IP servidor: 192.168.50.10  
Máscara: 255.255.255.0

## Contenido del archivo /etc/network/interfaces

auto lo  
iface lo inet loopback  

auto enp0s3  
iface enp0s3 inet dhcp  

auto enp0s8  
iface enp0s8 inet static  
      address 192.168.50.10  
      netmask 255.255.255.0  
