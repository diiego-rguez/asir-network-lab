# Servidor DHCP

Servicio instalado:

ISC DHCP Server

El servidor DHCP se ejecuta en la máquina **ServerPrincipal** y se encarga de asignar direcciones IP automáticamente a los clientes de la red interna del laboratorio.

<img width="757" height="247" alt="dhcp-servicio-activo" src="https://github.com/user-attachments/assets/6d96c0e0-d036-49f5-b148-384042c00928" />

---

## Interfaz utilizada

enp0s8


## Red del laboratorio

192.168.50.0/24


## Rango de direcciones

192.168.50.100 - 192.168.50.200


## Gateway (router)

192.168.50.10


## Servidor DNS

192.168.50.10


## Dominio interno

lab.local

<img width="578" height="379" alt="configuracion-dhcp" src="https://github.com/user-attachments/assets/09329655-f81f-481a-b9b5-93f60380c44b" />

---

## Archivo de concesiones

Las direcciones IP asignadas por el servidor DHCP se registran en el archivo:

/var/lib/dhcp/dhcpd.leases

<img width="614" height="484" alt="dhcp-leases" src="https://github.com/user-attachments/assets/0a8c3586-6833-4123-8ce9-0c7bc87d0cf9" />


---

## Prueba desde cliente

El cliente obtiene dirección IP automáticamente mediante DHCP.

Comprobación en Cliente1:

ip a

Resultado esperado:

192.168.50.100

<img width="812" height="429" alt="cliente-ip-dhcp" src="https://github.com/user-attachments/assets/b981b7e6-0579-425d-9650-78143880b454" />


---

## Prueba de conectividad

Desde Cliente1:

ping 192.168.50.10

El cliente puede comunicarse con el servidor principal de la red.

<img width="517" height="244" alt="prueba-conectividad-cliente1" src="https://github.com/user-attachments/assets/9ab36661-f4ac-4b8d-b782-27f05937a799" />

