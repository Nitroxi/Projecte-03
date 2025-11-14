# T03: Gestió flexible de discos (LVM i Espais d’emmagatzematge)

## Breu descripció
Un cop superada la fase de formació, ja esteu preparats per afrontar el repte dels nostres clients. Com ja es va explicar, tenim un nou i important client, el bufet d’advocats Garriga i associats un dels més prestigiosos de la ciutat, ha requerit els serveis de la nostra consultora. Gestiona una gran quantitat d'informació legal sensible, per la qual cosa la integritat, la disponibilitat (alta redundància) i la facilitat de gestió del seu emmagatzematge són d'importància crítica.

La direcció de "Garriga i Associats" ha expressat la necessitat urgent de renovar els seus sistemes de servidors per garantir que la informació estigui protegida contra fallades de disc i que l'espai pugui ser ampliat sense interrupcions.

Com a tècnics d'Everpia, teniu l'encàrrec de dissenyar i documentar les solucions d'emmagatzematge que compliran aquests requisits tant en entorns Linux com Windows. Aquest disseny permetrà presentar al client una proposta de solució.

![img](img/imggg.png)

L'objectiu principal és dissenyar i documentar dues solucions d'emmagatzematge (una per servidors Linux i una per servidors Windows) que compleixin amb els principis d'alta disponibilitat, redundància i escalabilitat per al client. Com ha de ser una prova de concepte, no treballareu amb servidors, sinó que, per facilitat, usareu màquines virtuals de sistemes operatius clients per documentar els procediments.

---

## 1. Part Linux: LVM amb Zorin OS
S'ha d'utilitzar la distribució Zorin OS (o una alternativa Linux compatible) per demostrar la utilitat del Logical Volume Manager (LVM).

### Requisits de la Implementació i Demostració:

#### **Configuració Inicial**
Crear un grup de volums (VG) i un volum lògic (LV) utilitzant inicialment un mínim de dos discs durs (simulats) de 10 GB de capacitat. Aquest volum haurà estar formatat i muntat automàticament al sistema mitjançant l’edició de l’arxiu `/etc/fstab`.

#### **Alta Disponibilitat**
Implementar la configuració d’un mirall (lvm_mirror) que protegeixi la informació davant la fallada d'un disc.

#### **Instantànies (snapshots)**
Crear i afegir dos discos de 10 GB al grup de volums. Crear un volum (`lvm_dades`) amb el primer disc afegit, formatar-lo i muntar-lo. A continuació afegir arxius al volum (poden ser imatges d’Internet). Usar el segon disc afegit per crear un snapshot (`lv_snapshot`) i documentar com es pot restaurar aquest snapshot, si per exemple, la informació del volum original es danyés.

#### **Escalabilitat**
Demostrar el procés d'ampliació. Usar l’espai que quedi lliure dins el grup de volums per ampliar el volum `lv_dades`.

---

## 2. Part Windows: Espais d'Emmagatzematge (Storage Spaces)
S'ha d'utilitzar Windows 11 (per demostrar les configuracions possibles mitjançant els Espais d'Emmagatzematge (Storage Spaces).

### Requisits de la Implementació i Demostració:

#### **Configuració inicial: Creació d'un Storage Pool**
Crear un pool d'emmagatzematge inicialment amb tres discos de 10 GB (simulats).

### **Estudi de Configuracions**
Demostrar i documentar la creació d'un Espai d'Emmagatzematge utilitzant:

#### **Resiliència de Mirall (Mirroring)**
Usar dos dels discos. Comprovar que ofereix alta disponibilitat.

#### **Resiliència de Paritat (Parity)**
Explicant la seva eficiència d'espai en comparació amb el mirall. Cal usar els tres discos.

#### **Resiliència de mirall triple**
Afegir tant discos de 10 GB com siguin necessaris.

### **Demostració de la Gestió**
Mostrar com es visualitza l'estat dels discos i del pool des de la consola de gestió de Windows, simulant la facilitat de manteniment.

---

## Com treballareu i què lliurareu?
El treball serà en grup. En primer lloc, us dividireu en dos equips, un d’ells haurà de resoldre la gestió en els equips Linux mitjançant LVM, mentre que el segon ho farà en els equips Windows usant la tecnologia anàloga Espais d’Emmagatzematge. Un cop ja us heu dividit, individualment preparareu el guió de la tasca a realitzar, cercant les comandes, consultant el enllaços de documentació, etc. Posteriorment, cada parella realitzarà la seva part de la demostració. Finalment, la totalitat del grup revisa la documentació generada i cada membre la puja al seu repositori.

La documentació dels dos casos es farà en format Markdown, incloent imatges, explicacions, etc. dins una carpeta anomenada `tasca03` dins del projecte. Com en casos anteriors, l’arxiu `README.md` de la carpeta, ha de contenir la descripció de la tasca i els enllaços per accedir als dos documents. 

La nota de la tasca és conjunta al grup, per tant, organitzeu-vos i tingueu una bona comunicació interna.  
Penseu que posteriorment, haureu de presentar al client les conclusions de la vostra feina en una presentació conjunta.

---

## Material de classe (disponible al Moodle)
- LVM Linux  
- Espais d’emmagatzematge (Windows)

