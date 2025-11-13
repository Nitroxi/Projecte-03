# 🧩 Servei de Directori LDAP

Configuració i gestió d’un servidor **LDAP** (Lightweight Directory Access Protocol) amb clients **Zorin OS**.  
Pràctica tècnica **T04**.

---

## 1. 🌐 Configuració inicial de la xarxa

Per començar, la xarxa tindrà **dues interfícies**: una per comunicar-se i una altra perquè el client es pugui comunicar amb el servidor.  
- A la **interfície 1** posarem **NAT**.  
- A la **interfície 2** posarem **Host Only**.

Configura els adaptadors a la màquina virtual segons correspongui.

<p align="center"><img src="img/img2.png"></p>

---

## 2. 🛠️ Configuració d’IP i DHCP

Un cop engegat el servidor, podem comprovar la IP amb:

```bash
ip a
```

Si la interfície `enp0s8` no té IP, la configurarem activant el **DHCP** i editant el fitxer de **netplan**:

```bash
sudo nano /etc/netplan/50-cloud-init.yaml
sudo netplan apply
```

<p align="center"><img src="img/img3.png"></p>

---

## 3. 🔧 Instal·lació del servidor LDAP

Instal·lem els paquets necessaris:

```bash
sudo apt update
sudo apt install slapd ldap-utils -y
```

Durant la instal·lació, ens demanarà una contrasenya per a l’administrador de LDAP.

<p align="center"><img src="img/img4.png"></p>

Per comprovar que el servei funciona:

```bash
sudo systemctl status slapd
```

<p align="center"><img src="img/img5.png"></p>

Consultem les entrades amb:

```bash
sudo slapcat | grep dn
```

<p align="center"><img src="img/img6.png"></p>

---

## 4. 🧾 Reconfiguració i domini

Per ajustar el domini LDAP:

```bash
sudo dpkg-reconfigure slapd
```

<p align="center"><img src="img/img7.png"></p>

Acceptem la reconfiguració:

<p align="center"><img src="img/img8.png"></p>

Posem la contrasenya:

<p align="center"><img src="img/img9.png"></p>

Comprovació:

```bash
sudo slapcat
```

---

## 5. 🗂️ Creació de l’estructura LDAP (LDIF)

Fitxer base LDIF:

<p align="center"><img src="img/img10.png"></p>

Aplica’l:

```bash
sudo ldapadd -x -D "cn=admin,dc=ldap,dc=local" -W -f base.ldif
```

---

## 6. 🔍 Comprovació de OUs i ús de LAM

Consulta de dades LDAP:

```bash
ldapsearch -x -b dc=ldap,dc=local
```

<p align="center"><img src="img/img11.png"></p>

Instal·lació del **LDAP Account Manager**:

```bash
sudo apt install ldap-account-manager -y
```

<p align="center"><img src="img/img12.png"></p>

Accés via navegador:

<p align="center"><img src="img/img13.png"></p>

Configuració del servidor:

<p align="center"><img src="img/img14.png"></p>

Modificació del sufix del servidor:

<p align="center"><img src="img/img15.png"></p>

Configuració de grups i usuaris:

<p align="center"><img src="img/img16.png"></p>

Opció de canvi de contrasenya:

<p align="center"><img src="img/img17.png"></p>

---

## 7. 👥 Creació d’usuaris i grups

Crear nou usuari:

<p align="center"><img src="img/img18.png"></p>

Afegim el cognom *usuari*:

<p align="center"><img src="img/img19.png"></p>

Configuració Unix:

<p align="center"><img src="img/img20.png"></p>

Assignem contrasenya:

<p align="center"><img src="img/img21.png"></p>

---

## 8. 💻 Configuració del client Zorin

Configura NAT + Host Only:

<p align="center"><img src="img/img22.png"></p>

Nom del client:

<p align="center"><img src="img/img23.png"></p>

---

## 9. 🧰 Instal·lació del client LDAP

```bash
sudo apt install libnss-ldap libpam-ldap nss-pam-ldapd nscd -y
```

<p align="center"><img src="img/img24.png"></p>

Configuració: posar **sí** on toca.

<p align="center"><img src="img/img25.png"></p>

---

## 10. 📄 Configuració d’arxius del sistema

Fitxer `nsswitch.conf`:

<p align="center"><img src="img/img26.png"></p>

Fitxer `common-session`:

```bash
session required pam_mkhomedir.so skel=/etc/skel umask=077
```

<p align="center"><img src="img/img27.png"></p>

Reinicia:

```bash
sudo systemctl restart nscd
sudo systemctl status nscd
```

---

## 11. ✅ Verificació final

Comprovació d’usuaris:

```bash
getent passwd | tail
```
<p align="center"><img src="img/imgend.png"></p>

<p align="center"><img src="img/img28.png"></p>

---

# ✔️ Conclusió

Si tot ha anat bé, el servidor LDAP i el client Zorin funcionen correctament i els usuaris LDAP es poden autenticar sense problemes.

🧩 *Pràctica T04 – Serveis de Directori LDAP completada.*

