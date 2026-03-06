# docs-docs-07-dhcp-reservas.md
# Reservas DHCP

Se configuran reservas DHCP para servidores de la infraestructura.

Servidor DHCP:
ServidorPrincipal (Debian 12)

Archivo de configuración:
/etc/dhcp/dhcpd.conf

## Reservas configuradas

WebApache

MAC: 08:00:27:76:27:50  
IP asignada: 192.168.50.101

WebNginx

MAC: 08:00:27:76:27:51   
IP asignada: 192.168.50.102

## Comprobación

En cada servidor se renueva la IP:

dhclient -r  
dhclient

Resultado esperado:

WebApache → 192.168.50.101  
WebNginx → 192.168.50.102
