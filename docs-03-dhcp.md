# Servidor DHCP

Servicio instalado:

ISC DHCP Server

El servidor DHCP se ejecuta en la máquina **ServerPrincipal** y se encarga de asignar direcciones IP automáticamente a los clientes de la red interna del laboratorio.

---

## Interfaz utilizada

enp0s8

---

## Red del laboratorio

192.168.50.0/24

---

## Rango de direcciones

192.168.50.100 - 192.168.50.200

---

## Gateway (router)

192.168.50.10

---

## Servidor DNS

192.168.50.10

---

## Dominio interno

lab.local

---

## Archivo de concesiones

Las direcciones IP asignadas por el servidor DHCP se registran en el archivo:

/var/lib/dhcp/dhcpd.leases

---

## Prueba desde cliente

El cliente obtiene dirección IP automáticamente mediante DHCP.

Comprobación en Cliente1:

ip a

Resultado esperado:

192.168.50.100

---

## Prueba de conectividad

Desde Cliente1:

ping 192.168.50.10

El cliente puede comunicarse con el servidor principal de la red.
