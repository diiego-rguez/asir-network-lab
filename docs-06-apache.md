# docs-06-apache.md
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

Para instalar Apache se habilita temporalmente un adaptador NAT en la máquina para permitir acceso a los repositorios.

apt update  
apt install apache2

Una vez instalado el servicio, la máquina vuelve a utilizar únicamente la red interna del laboratorio.

---

## Comprobación del servicio

Se comprueba que el servicio está activo:

systemctl status apache2

También se verifica que el servidor está escuchando en el puerto 80:

ss -tulpn | grep 80

<img width="1177" height="434" alt="apache-servicio-activo-y-puerto-80" src="https://github.com/user-attachments/assets/cdd1fba0-8767-456a-8b21-3b005d284bee" />

---

## Página de prueba

Se modifica la página web por defecto:

/var/www/html/index.html

Con contenido personalizado para comprobar el funcionamiento del servidor web.

---

## Prueba desde cliente

Desde Cliente1 se comprueba la resolución DNS y el acceso al servidor web:

curl apache.lab.local

<img width="490" height="306" alt="curl-apache-lab-local" src="https://github.com/user-attachments/assets/7d151248-e67b-4731-b89b-271debbbc0ae" />
