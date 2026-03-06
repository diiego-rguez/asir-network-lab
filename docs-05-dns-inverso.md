# docs-docs-05-dns-inverso.md
# DNS Inverso (PTR)

Se configura una zona inversa para permitir la resolución de IP a nombre.

Red del laboratorio:

192.168.50.0/24

Zona inversa:

50.168.192.in-addr.arpa

Archivo de zona:

/etc/bind/db.192

## Registros configurados

192.168.50.10 → serverprincipal.lab.local

192.168.50.100 → cliente1.lab.local

## Prueba en servidor

nslookup 192.168.50.10

Resultado esperado:

serverprincipal.lab.local

## Prueba desde cliente

nslookup 192.168.50.10
