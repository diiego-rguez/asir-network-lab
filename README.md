# asir-network-lab
# ASIR Network Lab

Laboratorio de administración de sistemas realizado con máquinas virtuales.

## Infraestructura

Servicios configurados:

- DHCP
- DNS
- Red interna

Tecnologías utilizadas:

- Debian 12
- Ubuntu Server 24.04
- ISC DHCP Server
- BIND9
- VirtualBox

---

## Topología de red

Servidor principal:

192.168.50.10

Red interna:

192.168.50.0/24

Los clientes reciben IP automáticamente mediante DHCP.

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
     Cliente1       WebApache     WebNginx
    Ubuntu 24.04     Debian 12     Debian 12
    DHCP              Apache        Nginx
 
---

## Servicios configurados

### DHCP

Rango asignado:

192.168.50.100 - 192.168.50.200

Gateway:

192.168.50.10

DNS:

192.168.50.10

---

### DNS

Dominio interno:

lab.local

Registros configurados:

serverprincipal.lab.local → 192.168.50.10  
web.lab.local → 192.168.50.10  
cliente1.lab.local → 192.168.50.100

---

## Pruebas de resolución

Servidor:

dig serverprincipal.lab.local

Cliente:

nslookup web.lab.local

Resultado esperado:

192.168.50.10

---

## Autor

Laboratorio realizado para prácticas de ASIR.
