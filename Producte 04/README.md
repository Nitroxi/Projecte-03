# P04: Documentació Servidor DNS

## Breu Descripció

Benvinguts, consultors!

Com a membres de l'equip de sistemes d’EverPia, heu configurat un servidor DNS com a prova de concepte per al client **Digicore**.  
Actualment, la configuració funciona dins d'una màquina virtual, però l’objectiu final és **publicar-la a GitHub** per tal de facilitar-ne la replicació.

Això permetrà que, quan es necessiti recrear el servidor DNS, només calgui clonar el repositori, copiar els fitxers al servidor Linux i reiniciar el servei — aconseguint un servidor DNS operatiu de manera ràpida i fiable.

---

# Fase 1: Preparació de la Connectivitat i Extracció dels Arxius

## Pas 1.1: Configuració de la Interfície Host-Only

1. A la configuració de la màquina virtual Ubuntu Server, afegiu una **segona interfície de xarxa** en mode **Host-Only**.  
2. Activeu-la i configureu una IP compatible amb la vostra xarxa Host-Only.
3. Comproveu la connectivitat fent un *ping* des de la màquina física:

```
ping 192.168.X.X
```

---

## Pas 1.2: Còpia Segura dels Fitxers Clau amb SCP

Un cop establerta la connectivitat, utilitzareu **scp** per traslladar els fitxers de configuració DNS des del servidor cap a la vostra màquina física.

### Fitxers a copiar

```
/etc/bind/named.conf.options
/etc/bind/named.conf.local
/etc/bind/zones/    (tots els arxius de zona)
```

### Exemple de comanda SCP (executada des del vostre PC)

```
scp usuario@192.168.X.X:/etc/bind/named.conf.options .
scp usuario@192.168.X.X:/etc/bind/named.conf.local .
scp -r usuario@192.168.X.X:/etc/bind/zones .
```

> El punt final (.) indica que els arxius es copiaran al directori actual del vostre PC.

---

# Fase 2: Integració a GitHub

## Pas 2.1: Crear carpeta i arxiu README.md

1. Al vostre repositori GitHub, creeu el fitxer:
   ```
   producte04/README.md
   ```
2. Aquest directori es crearà automàticament en indicar el nom complet.
3. Dins `README.md`, afegiu una explicació del contingut i de l'objectiu del producte.

---

## Pas 2.2: Pujar Arxius

1. Creeu la carpeta `zones` dins `producte04`.
2. Per poder crear carpetes des de GitHub, podeu usar un fitxer temporal:

   ```
   producte04/zones/esborrar
   ```

3. Pugeu tots els fitxers de configuració DNS.
4. Elimineu el fitxer temporal `esborrar`.

---

# Objectius Específics de la Tasca

- Documentar configuracions de servidors utilitzant GitHub com a repositori tècnic.
- Facilitar la **repetibilitat**: poder replicar configuracions de manera ràpida, segura i consistent.
- Evitar haver de reconfigurar servidors des de zero.
- Disposar d’un repositori permanent per a consultes i desplegaments futurs.

