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

/etc/bind/db.lab.local

Registros:

serverprincipal.lab.local → 192.168.50.10  
web.lab.local → 192.168.50.10  
cliente1.lab.local → 192.168.50.100

---

## Comprobación desde servidor

dig serverprincipal.lab.local

Resultado esperado:

192.168.50.10

---

## Comprobación desde cliente

nslookup web.lab.local

Resultado esperado:

192.168.50.10
