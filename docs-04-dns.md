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

---

## Comprobación desde servidor

Desde el propio servidor DNS se comprueba la resolución utilizando:

dig apache.lab.local

Resultado esperado:

192.168.50.101

---

## Comprobación desde cliente

Desde Cliente1 se comprueba la resolución del dominio:

nslookup nginx.lab.local

Resultado esperado:

192.168.50.102
