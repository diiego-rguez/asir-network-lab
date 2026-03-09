<img width="783" height="413" alt="interfaces-servidor" src="https://github.com/user-attachments/assets/975aea88-b619-4ff9-a97f-70a67db21e19" />
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
<img width="819" height="424" alt="configuracion-red-servidor" src="https://github.com/user-attachments/assets/cf12b4a3-4f90-4aca-b8ba-94a3b3d0e4bd" />
