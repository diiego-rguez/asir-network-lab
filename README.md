# asir-network-lab
# ASIR Network Lab

Laboratorio de administración de sistemas realizado con máquinas virtuales para simular una infraestructura de red en un entorno controlado.

El proyecto tiene como objetivo practicar la configuración de servicios esenciales en redes Linux.

---

## Servicios implementados

- DHCP
- DNS
- DNS inverso
- Reservas DHCP
- Servidor web Apache
- Servidor web Nginx

---

## Tecnologías utilizadas

- Debian 12
- Ubuntu Server 24.04
- ISC DHCP Server
- BIND9
- Apache2
- Nginx
- VirtualBox

---

## Topología de red

Red interna del laboratorio:

192.168.50.0/24

Servidor principal:

192.168.50.10

Los clientes obtienen dirección IP automáticamente mediante DHCP.

---

## Mapa de red
       ┌─────────────────────┐
       │ ServerPrincipal     │
       │ Debian 12           │
       │ DHCP + DNS          │
       │ 192.168.50.10       │
       └─────────┬───────────┘
                 │
         Red interna DiegoRed
           192.168.50.0/24
    ┌────────────┼────────────┐
    │            │            │
    Cliente1  WebApache    WebNginx

---

## Máquinas del laboratorio

ServidorPrincipal  
Debian 12  
192.168.50.10  

WebApache  
Debian 12  
192.168.50.101  

WebNginx  
Debian 12  
192.168.50.102  

Cliente1  
Ubuntu Server 24.04  
IP obtenida por DHCP  

---

## Documentación

Configuración detallada disponible en:

- docs-02-configuracion-red.md
- docs-03-dhcp.md
- docs-04-dns.md
- docs-05-dns-inverso.md
- docs-06-apache.md
- docs-07-dhcp-reservas.md
- docs-08-nginx.md

---

## Autor

Proyecto realizado como práctica de administración de sistemas (ASIR).
