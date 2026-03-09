# docs-05-dns-inverso.md
# DNS Inverso (PTR)

Se configura una zona DNS inversa para permitir la resolución de direcciones IP a nombres de host.

---

## Red del laboratorio

192.168.50.0/24


## Zona inversa

50.168.192.in-addr.arpa


## Archivo de zona

/etc/bind/db.192


## Registros configurados

192.168.50.10 → serverprincipal.lab.local

<img width="526" height="257" alt="zona-dns-inversa" src="https://github.com/user-attachments/assets/6f4d6288-bec9-4c60-9aea-54c42a381239" />

---

## Prueba en servidor

Desde el servidor se comprueba la resolución inversa:

nslookup 192.168.50.10 y dig -x 192.168.50.10

<img width="606" height="481" alt="nslookup-inverso-servidor" src="https://github.com/user-attachments/assets/b9dfb214-2ece-404e-8aa5-924dbff53af5" />

---

## Prueba desde cliente

Desde Cliente1 también se comprueba la resolución:

nslookup 192.168.50.10

<img width="539" height="167" alt="nslookup-inverso-cliente" src="https://github.com/user-attachments/assets/9bd0d6bd-77ad-41f4-bee4-79e685aa81cb" />
