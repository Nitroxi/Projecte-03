# **T01: Gestor de Contrasenya**
**CFGM Sistemes Microinformàtics i Xarxes 2B**  
**Autor:** Nezar Mghari Boussaada  

---

## **Fase 1: Anàlisi i Justificació (Document d'Informe)**

### **1. Introducció i Justificació**

Les contrasenyes febles o reutilitzades suposen un risc molt important per a qualsevol empresa. Aquestes poden ser fàcilment descifrades mitjançant atacs de diccionari o *credential stuffing*, on s’utilitzen llistes automàtiques de contrasenyes comunes o ja filtrades per accedir als sistemes.  
Quan això passa, posa en perill la seguretat de l’empresa i pot afectar tot el negoci.

Per això, **l’ús d’un gestor de contrasenyes és fonamental** per mantenir una bona seguretat. Aquestes eines permeten generar i emmagatzemar contrasenyes úniques per a cada servei, reduint així la possibilitat de vulneracions causades per contrasenyes febles o repetides.

---

### **2. Anàlisi i Comparativa Tècnica de les Alternatives**

Ara compararem els dos gestors de contrasenyes més populars actualment:

#### **Bitwarden**
Bitwarden és un gestor de contrasenyes en línia molt còmode i accessible. És útil per a equips que necessiten accés ràpid i sincronitzat des de diferents dispositius.  
Té una seguretat molt robusta, però depèn del núvol, que pot tenir vulnerabilitats o caigudes (ja sigui per atacs o per causes normals).

#### **KeePassXC**
KeePassXC és un gestor de contrasenyes fora de línia (*offline*), i això també té avantatges, com ara tenir un control total sobre les dades i evitar dependències externes.  
Això sí, és més manual i cal fer diverses còpies de seguretat per assegurar que no es perdi cap dada.

---

#### **Taula comparativa**

| **Característica** | **Bitwarden (Online / Núvol)** | **KeePassXC (Offline / Escriptori)** |
|--------------------|----------------------------------|---------------------------------------|
| **Sincronització** | Automàtica entre tots els dispositius (mòbil, web, PC). | No automàtica; cal sincronitzar manualment o amb eines externes. |
| **Model de seguretat** | Xifratge *end-to-end*, model *zero-knowledge* (el proveïdor no pot veure les dades). | Xifratge local (AES-256). L’arxiu es guarda al dispositiu de l’usuari. |
| **Accés multi-dispositiu** | Fàcil i immediat amb aplicacions i extensions de navegador. | Possible mitjançant còpies de l’arxiu o sincronització manual. |
| **Cost / Llicència** | Freemium: versió gratuïta amb opcions de pagament per a funcions avançades. | Gratuït i de codi obert (*open source*). |
| **Emmagatzematge** | En el núvol (Bitwarden o servidor propi si s’auto-hospeda). | Arxiu local (.kdbx) sota control de l’usuari o empresa. |
| **Funcionalitats corporatives** | Polítiques d’empresa, compartició d’equips, autenticació 2FA, registre d’activitat. | Limitades; no hi ha gestió centralitzada ni control d’usuaris. |
| **Dependència del núvol** | Sí, però amb alta disponibilitat i còpies de seguretat automàtiques. | No; total independència del núvol. |
| **Continuïtat del negoci** | Alta: fàcil recuperació i accés remot. | Depèn de les còpies de seguretat locals i la gestió interna. |

---

### **3. Avantatges i Inconvenients**

#### **Bitwarden (Núvol)**
**Avantatges:**
- Molt pràctic i fàcil d’utilitzar.  
- Sincronització automàtica entre dispositius.  
- Opcions útils per a equips (compartició segura, verificació en dos passos).  
- Alta disponibilitat i còpies de seguretat automàtiques.

**Inconvenients:**
- Depèn del núvol i de la connexió a Internet.  
- Algunes funcions avançades són de pagament.  
- Si es perd la contrasenya mestra, no hi ha manera de recuperar les dades.

---

#### **KeePassXC (Offline / Escriptori)**
**Avantatges:**
- Control total de les dades (no depèn del núvol).  
- Totalment gratuït i de codi obert.  
- Major privacitat i independència.

**Inconvenients:**
- Sincronització manual entre dispositius.  
- Necessitat de fer còpies de seguretat periòdiques.  
- Més tècnic i menys còmode per a usuaris no avançats.  
- Sense funcions corporatives automàtiques.

---

### **Recomanació**
Es recomana utilitzar **Bitwarden**, ja que és **fàcil d’utilitzar, segur i permet tenir totes les contrasenyes sincronitzades** a qualsevol dispositiu sense complicacions.  
A més, permet **compartir credencials amb l’equip** de manera controlada i **activar la verificació en dos passos** per augmentar la seguretat.  
En resum: **pràctic, fiable i perfecte per al dia a dia de l’empresa.**

---

## **Fase 2: Guia d'Ús Tècnica (Manual Operatiu)**

### **1. Instal·lació**

1. Accedeix a la pàgina oficial de **Bitwarden** i entra a l’apartat **“Downloads”**.  
2. Descarrega l’instal·lador de l’aplicació per al teu sistema operatiu.  
3. Durant la instal·lació, selecciona si vols instal·lar-lo només per a l’usuari actual o per a tots els usuaris de l’ordinador (segons les necessitats de l’empresa).  
4. Un cop instal·lat, obre l’aplicació i inicia sessió amb el teu compte de Bitwarden. Si no en tens cap, pots registrar-te fàcilment.  
5. Amb l’aplicació oberta, podràs gestionar no només comptes, sinó també **targetes, informació personal, notes segures i claus SSH**.

---

### **2. Generador de Contrasenyes**

1. Ves a l’apartat **“Entrada”** dins de l’aplicació.  
2. Aquí podràs classificar les diferents entrades en carpetes per mantenir-ho tot ben organitzat.  
3. Introdueix:
   - **Usuari:** el nom d’usuari o correu de la web o aplicació.  
   - **URL:** la direcció del lloc web (perquè Bitwarden pugui autocompletar).  
4. Pel que fa a la contrasenya, pots:
   - Escriure-la manualment, o  
   - Fer servir el **generador automàtic** de Bitwarden.  

5. Pots configurar la generació de la contrasenya:
   - Tipus (frase llarga o caràcters aleatoris).  
   - Longitud desitjada.  
   - Incloure o no símbols, números, majúscules/minúscules.  

6. A més, pots **consultar l’historial de contrasenyes generades** per revisar o reutilitzar-ne alguna si cal.

---

> **Conclusió:**  
> Bitwarden proporciona una solució segura, eficient i fàcil d’utilitzar per a la gestió de contrasenyes en entorns corporatius.  
> La seva adopció millorarà significativament la seguretat de l’empresa davant possibles filtracions i atacs cibernètics.

