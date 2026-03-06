# docs-03-dhcp.md
# Servidor DHCP

Servicio instalado:
ISC DHCP Server

Interfaz utilizada:
enp0s8

Red del laboratorio:
192.168.50.0/24

Rango de direcciones:

192.168.50.100 - 192.168.50.200

Gateway(router):
192.168.50.10

Domain-name-servers:
192.168.50.10(DNS)

Domain-name:
lab.local(dominio interno)

Ver IPs asignadas:
/var/lib/dhcp/dhcpd.leases


## Prueba desde cliente

Cliente1 obtiene IP automáticamente:

ip a
→ 192.168.50.100

Prueba de conectividad:

ping 192.168.50.10
