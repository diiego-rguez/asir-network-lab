# docs-07-dhcp-reservas.md
# Reservas DHCP

Se configuran reservas DHCP para los servidores de la infraestructura del laboratorio, de forma que siempre reciban la misma dirección IP.

Servidor DHCP:

ServidorPrincipal (Debian 12)

Archivo de configuración:

/etc/dhcp/dhcpd.conf

<img width="582" height="560" alt="reservas-dhcp-configuracion" src="https://github.com/user-attachments/assets/0119c35a-7410-44ae-a56f-f185c43d2ca1" />

---

## Reservas configuradas

WebApache

MAC: 08:00:27:76:27:50  
IP asignada: 192.168.50.101

WebNginx

MAC: 08:00:27:76:27:51  
IP asignada: 192.168.50.102

---

## Comprobación

En cada servidor se renueva la dirección IP obtenida mediante DHCP:

dhclient -r  
dhclient

Resultado esperado:

WebApache:

<img width="827" height="342" alt="webapache-ip-reserva" src="https://github.com/user-attachments/assets/78fafd26-c916-4efc-b1c5-89c14da15bdc" />

WebNginx:

<img width="827" height="342" alt="webnginx-ip-reserva" src="https://github.com/user-attachments/assets/9509325f-4dcf-47f7-8ee9-2868431bea33" />
