# docs-04-dns.md
# Configuración del servidor DNS

Software utilizado:

BIND9

Servidor DNS:

192.168.50.10

Dominio configurado:

lab.local

---

## Archivo de zona

Archivo de configuración de la zona:

/etc/bind/db.lab.local

Registros configurados:

serverprincipal.lab.local → 192.168.50.10  
apache.lab.local → 192.168.50.101  
nginx.lab.local → 192.168.50.102  

<img width="573" height="312" alt="zona-dns-lab-local" src="https://github.com/user-attachments/assets/bf2a7f39-c01e-426b-a418-a1288e05fa16" />

---

## Comprobación desde servidor

Desde el propio servidor DNS se comprueba la resolución utilizando:

dig apache.lab.local

Resultado esperado:

192.168.50.101

<img width="632" height="447" alt="dig-apache" src="https://github.com/user-attachments/assets/18bdaa3c-e84b-47d1-a867-f49d95611c20" />

---

## Comprobación desde cliente

Desde Cliente1 se comprueba la resolución del dominio:

nslookup nginx.lab.local

Resultado esperado:

192.168.50.102

<img width="524" height="212" alt="nslookup-nginx" src="https://github.com/user-attachments/assets/578a1233-42f4-4659-920d-424364330d65" />

