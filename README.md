# asir-network-lab
# ASIR Network Lab

Laboratorio de administración de sistemas realizado con máquinas virtuales para practicar la configuración de servicios de red en un entorno controlado.

El objetivo del proyecto es simular una pequeña infraestructura de red con servicios habituales en entornos de sistemas.

---

# Infraestructura

Servicios configurados actualmente:

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

# Topología de red

Servidor principal:

192.168.50.10

Red interna:

192.168.50.0/24

Los clientes reciben dirección IP automáticamente mediante DHCP.

---

# Mapa de red
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

# Máquinas del laboratorio

ServidorPrincipal  
Debian 12  
192.168.50.10  
Servicios: DHCP + DNS

WebApache  
Debian 12  
192.168.50.101  
Servicio: Apache

WebNginx  
Debian 12  
192.168.50.102  
Servicio: Nginx

Cliente1  
Ubuntu Server 24.04  
IP obtenida por DHCP

---

# Configuración DHCP

Servidor: ServidorPrincipal

Rango asignado:

192.168.50.100 - 192.168.50.200

Gateway:

192.168.50.10

Servidor DNS:

192.168.50.10

También se han configurado **reservas DHCP** para los servidores web.

---

# Configuración DNS

Servidor: BIND9

Dominio interno:

lab.local

Registros configurados:

serverprincipal.lab.local → 192.168.50.10  
apache.lab.local → 192.168.50.101  
nginx.lab.local → 192.168.50.102  

---

# Pruebas de funcionamiento

Resolución DNS desde el servidor:
