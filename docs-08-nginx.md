# docs-08-nginx.md
# Servidor Web Nginx

Máquina:

WebNginx (Debian 12)

IP reservada mediante DHCP:

192.168.50.102

Registro DNS:

nginx.lab.local

Servicio instalado:

Nginx

---

## Instalación

Para instalar Nginx se habilita temporalmente un adaptador NAT para acceder a los repositorios.

apt update
apt install nginx

Tras la instalación se vuelve a utilizar únicamente la red interna del laboratorio.

---

## Comprobación del servicio

systemctl status nginx

También se comprueba que el servidor escucha en el puerto 80.

---

## Página de prueba

Se modifica la página por defecto:

/var/www/html/index.nginx-debian.html

---

## Prueba desde cliente

curl nginx.lab.local

Resultado esperado:

El cliente recibe la página servida por el servidor Nginx.
