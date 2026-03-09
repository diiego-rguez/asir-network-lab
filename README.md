# asir-network-lab
# ASIR Network Lab

Laboratorio de administración de sistemas realizado con máquinas virtuales para practicar la configuración de servicios de red en un entorno controlado.

El objetivo del proyecto es simular una pequeña infraestructura de red con varios servidores y clientes dentro de una red interna.

---

## Infraestructura

Servicios configurados:

- DHCP
- DNS
- DNS inverso
- Servidor web Apache
- Servidor web Nginx

Tecnologías utilizadas:

- Debian 12
- Ubuntu Server 24.04
- ISC DHCP Server
- BIND9
- Apache2
- Nginx
- VirtualBox

---

## Topología de red

Servidor principal:

192.168.50.10

Red interna:

192.168.50.0/24

Los clientes de la red obtienen su dirección IP automáticamente mediante DHCP.

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

WebNginx  
Debian 12  

Cliente1  
Ubuntu Server 24.04  

---

## Documentación

La configuración detallada de cada servicio se encuentra en los siguientes documentos:

- docs-02-configuracion-red.md
- docs-03-dhcp.md
- docs-04-dns.md
- docs-05-dns-inverso.md
- docs-06-apache.md
- docs-07-dhcp-reservas.md
- docs-08-nginx.md

---

## Autor

Laboratorio realizado como práctica de administración de sistemas (ASIR).
