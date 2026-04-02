# asir-network-lab
# ASIR Network Lab

Laboratorio de administración de sistemas realizado con máquinas virtuales para simular una infraestructura de red en un entorno controlado.

El proyecto tiene como objetivo practicar la configuración de servicios esenciales en redes Linux, incluyendo enrutamiento entre redes, distribución de direcciones IP mediante DHCP y despliegue de servicios web.

---

## Servicios implementados

- DHCP
- DHCP Relay
- DNS
- DNS inverso
- Reservas DHCP
- Enrutamiento entre redes
- NAT para salida a internet
- Servidor web Apache
- Servidor web Nginx

---

## Tecnologías utilizadas

- Debian 12
- Debian 13
- Ubuntu Server 24.04
- ISC DHCP Server
- ISC DHCP Relay
- BIND9
- Apache2
- Nginx
- iptables (NAT)
- VirtualBox

---

## Topología de red

El laboratorio está compuesto por **dos redes internas** conectadas mediante routers.

Red principal (servidores):

192.168.50.0/24

Red de clientes:

192.168.60.0/24

El acceso a internet se realiza a través de un router con NAT.

---

## Mapa de red

                                                   INTERNET
                                                      │
                                                (NAT VirtualBox)
                                                      │
                                            ┌─────────────────┐
                                            │ RouterPrincipal │
                                            │ Debian 13       │
                                            │ NAT + Routing   │
                                            │ 192.168.50.1    │
                                            └─────────┬───────┘
                                                      │
                                              Red interna DiegoRed
                                                192.168.50.0/24
                               ┌───────────────┬───────────────┬───────────────┐
                               │               │               │               │

                            ServerPrincipal   WebApache     WebNginx       RouterRelay
                            Debian 12         Debian 12      Debian 12      Ubuntu 24.04
                            DHCP + DNS        Apache          Nginx          DHCP Relay
                            192.168.50.10   192.168.50.101   192.168.50.102  192.168.50.100
                                                                                │
                                                                                │
                                                                             Red ClienteRed
                                                                             192.168.60.0/24
                                                                                │
                                                                             Cliente2
                                                                             Ubuntu Server 24.04
                                                                             IP obtenida por DHCP
