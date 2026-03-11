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

Para instalar Nginx se habilita temporalmente un adaptador NAT en la máquina para permitir acceso a los repositorios.

apt update  
apt install nginx

Tras la instalación se vuelve a utilizar únicamente la red interna del laboratorio.

---

## Comprobación del servicio

Se comprueba que el servicio está activo:

systemctl status nginx

También se verifica que el servidor está escuchando en el puerto 80.

<img width="1130" height="413" alt="nginx-servicio-activo" src="https://github.com/user-attachments/assets/be19b10d-f7c0-4fb5-966d-bae546c26866" />

---

## Página de prueba

Se modifica la página web por defecto:

/var/www/html/index.nginx-debian.html

Con contenido personalizado para verificar el funcionamiento del servidor web.

---

## Prueba desde cliente

Desde Cliente1 se comprueba el acceso al servidor web:

curl nginx.lab.local

Resultado esperado:

<img width="799" height="303" alt="curl-nginx" src="https://github.com/user-attachments/assets/39235bc6-9dea-4a86-bc88-e57dfa21fd9f" />
