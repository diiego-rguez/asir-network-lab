# DHCP Relay

Se añade una segunda red al laboratorio utilizando un router intermedio que actúa como DHCP Relay.

Esto permite que el servidor DHCP situado en la red principal entregue direcciones IP a clientes de otra red.

Servidor DHCP:

ServerPrincipal  
192.168.50.10

---

## Máquina utilizada

RelayDHCP

Sistema operativo:

Ubuntu Server 24.04

---

## Interfaces de red

El router tiene dos interfaces conectadas a redes distintas.

enp0s3 → red interna DiegoRed  
enp0s8 → red interna ClienteRed

---

## Configuración de red

Red principal(DiegoRed):

192.168.50.0/24

Red secundaria(ClienteRed):

192.168.60.0/24

Gateway de la red secundaria:

192.168.60.1

Archivo de configuración:

/etc/netplan/50-cloud-init.yaml

Configuración aplicada:

<img width="644" height="323" alt="conifguración_relay" src="https://github.com/user-attachments/assets/215d4ac9-47ed-4116-8b19-2ac85a0cef82" />

Aplicar configuración:
sudo netplan apply

<img width="644" height="323" alt="ip_relay" src="https://github.com/user-attachments/assets/4bbf7c35-162a-4966-bf29-19c6ec376a6d" />

---

## Habilitar enrutamiento

Para que el sistema funcione como router, se habilita el reenvío de paquetes IP.

Editar archivo:
/etc/sysctl.conf

Añadir o descomentar:
net.ipv4.ip_forward=1

<img width="831" height="469" alt="sysctl_conf_relay" src="https://github.com/user-attachments/assets/b5a3fc04-c083-4fff-86da-cfc8c3a7b327" />

Aplicar cambios:
sudo sysctl -p

---

## Ruta hacia la segunda red en RouterPrincipal

Para que la red principal pueda comunicarse con la red ClienteRed se añade una ruta estática en el router principal.

Archivo de configuración:

/etc/network/interfaces

Configuración utilizada:

<img width="603" height="454" alt="enrutamiento_router" src="https://github.com/user-attachments/assets/095391a6-96eb-41c6-87e1-8c20f29c504e" />

Esta ruta indica que para llegar a la red 192.168.60.0/24 se debe enviar el tráfico al RouterRelay

---

## Configuración de DHCP para la segunda red

El servidor DHCP se configura para entregar direcciones también a la red ClienteRed.

Archivo de configuración:

/etc/dhcp/dhcpd.conf

Configuración añadida: subnet 192.168.60.0 netmask 255.255.255.0 {}

<img width="777" height="679" alt="ajuste_dhcpd_conf" src="https://github.com/user-attachments/assets/2c4aa9f6-d15f-4a52-a81c-a18aeb604972" />

Se reinicia el servicio DHCP para aplicar la nueva configuración y se comprueba su estado:

<img width="860" height="464" alt="status_dhcp_server" src="https://github.com/user-attachments/assets/dcc9352e-c7f3-4d68-b58f-174449ee1f86" />


---

## Instalación del servicio DHCP Relay

El router relay reenvía las peticiones DHCP al servidor situado en la red principal.

Instalación:


sudo apt update

sudo apt install isc-dhcp-relay

<img width="1148" height="674" alt="instalación_relay" src="https://github.com/user-attachments/assets/ae92e764-f4d6-4a09-87a7-036db933ac6c" />

<img width="1153" height="667" alt="instalación_relay_interfaces" src="https://github.com/user-attachments/assets/f8cd5ecd-c58d-4f90-94d4-efb3c8a63a58" />

---

## Configuración del servicio

Archivo de configuración:

/etc/default/isc-dhcp-relay


Parámetros configurados:

Servidor DHCP:


192.168.50.10


Interfaces utilizadas:


enp0s3 enp0s8

<img width="784" height="344" alt="default_relay" src="https://github.com/user-attachments/assets/2b30d3ee-6e8d-44ba-a119-706118d87a5d" />

---

## Reiniciar servicio


sudo systemctl restart isc-dhcp-relay


Comprobación:


systemctl status isc-dhcp-relay


<img width="928" height="639" alt="status_relay" src="https://github.com/user-attachments/assets/b40e0246-ac42-4636-9550-10853a93e391" />


---

## Verificación del relay en logs

Para comprobar que el relay está reenviando peticiones DHCP se consultan los logs del sistema.


journalctl -u isc-dhcp-relay

<img width="733" height="702" alt="journalctl_Relay" src="https://github.com/user-attachments/assets/0b266063-5003-4dec-b33e-2f63521828e0" />


---

## Comprobación de tabla de rutas

Se verifica que el router conoce ambas redes.


ip route


Resultado:

<img width="670" height="181" alt="ip_r_relay" src="https://github.com/user-attachments/assets/c2fe8415-6b0d-4ee2-9a9c-868d44483643" />


---

## Cliente en la segunda red

Máquina utilizada:

Cliente 2

Sistema operativo:

Ubuntu Server 24.04

Configuración de red:

DHCP automático.

Red conectada:

ClienteRed --> 192.168.60.0/24

---

## Obtención de dirección IP

En el cliente se solicita dirección IP al servidor DHCP a través del relay.

<img width="768" height="263" alt="cliente_cogiendo_ip" src="https://github.com/user-attachments/assets/020ec65d-529c-45b1-8ff8-ed35b8a2e95f" />

<img width="823" height="631" alt="todo_correcto_cliente2" src="https://github.com/user-attachments/assets/3ba3d32c-bfc9-4d1d-9b8a-f3be535fa0e4" />


Comprobación de comunicación con el servidor principal:

ping 192.168.50.10


---

## Prueba de resolución DNS y acceso web

El cliente de la segunda red debe poder resolver nombres utilizando el servidor DNS.
Desde el cliente se accede a los servidores web de la red principal.

<img width="552" height="685" alt="todo_correcto_cliente22" src="https://github.com/user-attachments/assets/c508b893-e09c-4371-a6fc-aa1fa62753c5" />

---

## Concesiones DHCP registradas

El servidor DHCP guarda las direcciones entregadas a los clientes en el archivo:

/var/lib/dhcp/dhcpd.leases

Esto permite verificar qué direcciones han sido asignadas.

Comando:

cat /var/lib/dhcp/dhcpd.leases
