# Servidor Web Apache

Máquina:

WebApache (Debian 12)

IP reservada mediante DHCP:

192.168.50.101

Registro DNS:

apache.lab.local

Servicio instalado:

Apache2

---

## Instalación

Para instalar Apache se habilita temporalmente un adaptador NAT para permitir acceso a los repositorios.

apt update  
apt install apache2

Una vez instalado el servicio, la máquina vuelve a utilizar únicamente la red interna del laboratorio.

---

## Comprobación del servicio

systemctl status apache2

También se comprueba que el servidor escucha en el puerto 80:

ss -tulpn | grep 80

---

## Página de prueba

Se modifica la página web por defecto:

/var/www/html/index.html

Contenido de prueba para verificar el funcionamiento del servidor.

---

## Prueba desde cliente

Desde Cliente1 se comprueba la resolución DNS y el acceso al servidor web:

curl apache.lab.local

Resultado esperado:

El cliente recibe la página servida por el servidor Apache.
