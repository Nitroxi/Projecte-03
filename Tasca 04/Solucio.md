# **T04: SERVEIS DE DIRECTORI. LDAP**

**CFGM SISTEMES MICROINFORMÀTICS I XARXES 2B**

**Nezar Mghari Boussaada**

Per començar, la xarxa tindrà dues interfícies: una per comunicar-se i
una altra perquè es pugui comunicar amb el client. A la interfície 1
posarem NAT i a la interfície 2 posarem Host Only.

![img2](img/img2.png)

![img3](img/img3.png)

Després haurem d'executar el comandament "ip a" per veure la seva IP. Si
la interfície enp0s8 no té IP, la configurarem activant el DHCP editant
l'arxiu netplan.

![img4](img/img4.png)

Primer començarem configurant el nom i el domini del servidor.

Després instal·larem LDAP amb la comanda apt install slapd ldap-utils
-y, i ens tocarà posar-li una contrasenya.

A continuació, comprovem que el servei funcioni amb la comanda
"systemctl status slapd".

![img5](img/img5.png)

Després comprovem amb la comanda "slapcat" si hi ha l'usuari que
necessitem.

![img6](img/img6.png)

Si el nom no coincideix amb allò que volem, l'haurem de tornar a
configurar amb la comanda dpkg-reconfigure slapd. Posem el nom del DNS
que volem. En el meu cas és innovatech20.test.

![img7](img/img7.png)

Li posem que sí.

![img8](img/img8.png)

Li posem una contrasenya segura, en aquest cas p@ssw0rd.

També li posem que sí.

![img9](img/img9.png)

Un cop fet, tornem a comprovar amb "slapcat" si s'ha configurat
correctament.

Ara crearem un fitxer LDIF per definir una OU. En aquest arxiu posarem
l'OU d'usuaris i de grups. Hauria de quedar més o menys així:

![img10](img/img10.png)

Després utilitzarem la comanda "ldapadd" per crear entrades al servidor
i posarem la contrasenya.

![img11](img/img11.png)

![img12](img/img12.png)

Després consultarem amb "ldapsearch" per mostrar les OUs creades.

Ara instal·lem el ldap account manager amb la següent comanda: sudo apt
install ldap-account-manager -y

![img13](img/img13.png)

Ara comprovem entrant al panell LDAP

![img14](img/img14.png)

Ara configurem les següents coses:

En preferències del servidor, a Direcció del servidor, posem l'adreça IP
del nostre servidor i la llista d'usuaris vàlids.

Aquí només canviem el sufix de l'arbre.

![img15](img/img15.png)

Ara canviem els sufixos LDAP dels grups i usuaris.

![img16](img/img16.png)

Per últim, si vols, pots canviar la contrasenya.

![img17](img/img17.png)

Ara entrem i creem els usuaris i els grups (és el mateix procés per a
tots dos, així que només posarem les captures de l'usuari).

Li hem de fer clic a "Nou usuari"

![img18](img/img18.png)

Posem com a cognom el nom que vulguem; en el meu cas serà "usuari".

![img19](img/img19.png)

Cliquem a l'apartat Unix. Aquí podem modificar el nom comú, usuari, grup
i altres paràmetres. Jo no modificaré res; només editaré el grup perquè
tingui el que he creat prèviament.

![img20](img/img20.png)

I, per últim, li assignem una contrasenya; s'ubica a la part de dalt.

I creem la contrasenya i la guardem.

![img21](img/img21.png)

Ara haurem de configurar el client ZORIN; el primer serà posar dos
adaptadors: NAT i "Adaptador només anfitrió".

![img22](img/img22.png)

Un cop dins del client, haurem de configurar el nom de l'equip perquè
sigui igual al domini del servidor. Si s'han aplicat els canvis
correctament, s'haurà de veure el nou nom de l'equip.

![img23](img/img23.png)

Ara també instal·larem al client l'LDAP perquè es pugui comunicar amb el
servidor amb: sudo apt install libnss-ldap libpam-ldap nss-pam-ldapd
nscd -y

La configuració és pràcticament igual que la primera vegada, excepte per
tres apartats: aquí poses l'última versió disponible.

![img24](img/img24.png)

Posa que sí

Posa que no

![img25](img/img25.png)

Per comprovar si es connecta bé amb el servidor, farem una consulta amb
ldapsearch; ens hauria de sortir alguna cosa així:

Ara configurarem una sèrie d'arxius començant amb nsswitch.conf

![img26](img/img26.png)

Ara haurem d'eliminar una part de la comanda que posi
use_authok.

Ara haurem d'escriure una nova línia a l'arxiu common-session perquè es puguin crear comandes automàtiques.

![img27](img/img27.png)

Ara reiniciem el servei amb la comanda "sudo systemctl restart nscd" i
verifiquem l'estat amb "systemctl status nscd".

Després haurem de comprovar si s'han creat els usuaris que vam crear amb
"getent passwd | tail"

![img28](img/img28.png)

I ja estaria 👍

