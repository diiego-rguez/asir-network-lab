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

Red principal:

192.168.50.0/24

Red secundaria:

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

Para que el sistema funcione como router se habilita el reenvío de paquetes IP.

Editar archivo:
/etc/sysctl.conf

Añadir o descomentar:
net.ipv4.ip_forward=1

<img width="831" height="469" alt="sysctl_conf_relay" src="https://github.com/user-attachments/assets/b5a3fc04-c083-4fff-86da-cfc8c3a7b327" />

Aplicar cambios:
sudo sysctl -p

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
