# docs-docs-06-apache.md
# Servidor Web Apache

Máquina:

WebApache (Debian 12)

IP asignada por DHCP:

192.168.50.101

Registro DNS:

apache.lab.local

Servicio instalado:

Apache2

## Instalación

apt install apache2

## Comprobación

systemctl status apache2

## Prueba desde cliente

curl apache.lab.local

Resultado:

Servidor web Apache funcionando correctamente.
