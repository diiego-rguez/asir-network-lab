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
