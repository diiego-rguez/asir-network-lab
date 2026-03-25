# Router principal y salida a internet

Para proporcionar acceso a internet a la red del laboratorio se añade un router dedicado.

Inicialmente los servidores tenían un adaptador NAT para acceder a internet.  
En esta fase se modifica la arquitectura para que todo el tráfico salga a través de un router central.

---

## Máquina utilizada

RouterPrincipal

Sistema operativo:
Debian 13

---

## Interfaces de red

El router tiene dos interfaces:

enp0s3 → NAT (salida a internet)

enp0s8 → red interna DiegoRed

---

## Configuración de red

Archivo configurado:

/etc/network/interfaces

Configuración aplicada:


<img width="695" height="354" alt="ip_router" src="https://github.com/user-attachments/assets/9dc9029c-7438-4c0b-b4c2-912e8c83fa19" />


<img width="645" height="387" alt="router-ip-buena" src="https://github.com/user-attachments/assets/f2d99414-4922-4482-b503-21251a679326" />


<img width="648" height="179" alt="router-internet" src="https://github.com/user-attachments/assets/550dac40-db6f-462a-828a-1e57ed67c721" />


La interfaz enp0s8 se conecta a la red interna DiegoRed y actuará como puerta de enlace para los clientes.

---

## Habilitar el reenvío de paquetes (IP Forwarding)

Para que el router pueda reenviar tráfico entre interfaces se habilita el forwarding.

Archivo utilizado:

/etc/sysctl.d/router.conf

Contenido:

net.ipv4.ip_forward=1

Aplicar configuración:

sysctl --system

Comprobación:

<img width="734" height="142" alt="net ipv4 ip_forward router" src="https://github.com/user-attachments/assets/567bf2bc-66da-42fe-8f79-065aa14dae31" />


---

## Instalación de iptables

Para permitir la traducción de direcciones (NAT) se instala iptables.

apt update  
apt install iptables

Comprobación:

iptables --version

---

## Configuración NAT

Se configura NAT para que los equipos de la red interna puedan salir a internet.

Reglas aplicadas:

iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE

Permitir tráfico desde la red interna hacia internet:

iptables -A FORWARD -i enp0s8 -o enp0s3 -j ACCEPT

Permitir tráfico de retorno desde internet:

iptables -A FORWARD -i enp0s3 -o enp0s8 -m state --state RELATED,ESTABLISHED -j ACCEPT

Comprobación:

iptables -L  
iptables -t nat -L


<img width="968" height="673" alt="instalación_configuración_iptables" src="https://github.com/user-attachments/assets/dfe5b9fe-3205-44a7-b13b-74956e93bba9" />

---

## Guardar reglas iptables

Para que las reglas persistan tras reiniciar el sistema se instala:

apt install iptables-persistent

Guardar configuración:

netfilter-persistent save o durante la instalación:


<img width="963" height="680" alt="iptables_persistent" src="https://github.com/user-attachments/assets/7ad43e30-6113-44d7-a85e-f75bbdd95527" />


---

## Modificación del servidor DHCP

El servidor DHCP se ejecuta en ServerPrincipal (192.168.50.10).

Al introducir el router se modifica el gateway entregado a los clientes.

Archivo modificado:

/etc/dhcp/dhcpd.conf

Configuración actualizada:

subnet 192.168.50.0 netmask 255.255.255.0 {

range 192.168.50.100 192.168.50.200;

option routers 192.168.50.1;

option domain-name-servers 192.168.50.10;

option domain-name "lab.local";

}

El gateway ahora es:

192.168.50.1

---

## Reinicio del servicio DHCP

systemctl restart isc-dhcp-server

Comprobación:

systemctl status isc-dhcp-server

---

## Renovación de dirección en cliente

En Cliente1 se renueva la dirección IP:

dhclient -r  
dhclient

Comprobación de gateway:

ip route

Resultado esperado:

default via 192.168.50.1

---

## Pruebas de conectividad

Conectividad con el router:

ping 192.168.50.1

Conectividad a internet:

ping 8.8.8.8

Resolución DNS:

ping google.com

---

## Resultado

Los equipos de la red interna pueden:

- obtener dirección IP mediante DHCP
- resolver nombres mediante DNS
- acceder a servicios web internos
- salir a internet a través del router principal

---

## Capturas recomendadas

sysctl net.ipv4.ip_forward

iptables -t nat -L

ip route

ping 8.8.8.8

ping google.com
