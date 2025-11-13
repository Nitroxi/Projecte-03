![img](img/img1.png)

# T03: GESTIÓ FLEXIBLE DE DISCOS

**CFGM SISTEMES MICROINFORMÀTICS I XARXES 2B**  
**Nezar Mghari Boussaada**

## Configuració inicial

Primer afegirem els **3 discos virtuals** a la màquina virtual.

![img](img/img2.png)

Un cop creats els discos, **iniciem la màquina**. Quan Windows s'hagi iniciat, hem d'anar al **Panell de control** i buscar la secció **Espais d'emmagatzematge**.

![img](img/img3.png)

Allà seleccionarem **Crear un nou grup i espais d'emmagatzematge**.

Windows ens mostrarà els discos disponibles. En aquest primer pas **només seleccionarem 2 discos** i acceptarem.

![img](img/img4.png)

Això crea el **Storage Pool**, que és el contenidor on es poden crear volums amb diferents nivells de resiliència.

## Configuracions (Mirror)

Un cop creat el Storage Pool ens sortirà una secció tal i així:

![img](img/img5.png)

Un cop creat el Storage Pool, ens apareixerà una secció com aquesta: ara configurarem el disc. En el meu cas he escollit:

- **Sistema d'arxius :** NTFS
- **Tipus de resiliència :** Reflex doble (Mirror)
- **Mida :** màxima disponible

Hem de recordar que, encara que hem posat **dos discos de 10 GB cadascun**, el reflex doble fa una clonació en temps real, així que la capacitat útil serà només **10 GB** (la resta es fa servir per la còpia).

Per provar la resiliència, crearem un arxiu anomenat **prueba** dins la nova unitat.

![img](img/img6.png)

Ara apagarem l'ordinador i **eliminarem un dels dos discos** de la màquina virtual per simular un error.

![img](img/img7.png)

En tornar a iniciar Windows, apareixerà una **advertència indicant que el disc s'ha reduït**.

![img](img/img8.png)

Tot i així, encara podrem obrir l'arxiu sense cap problema.

Això demostra que el *mirror* realment protegeix contra la fallada d'un disc.

![img](img/img9.png)

## Configuració (paritat)

Abans de continuar, cal entendre què és la **paritat**:

> La paritat és un mètode de protecció de dades que permet recuperar la informació encara que un dels discos falli, **sense haver de duplicar tota la informació** com passa amb el mirall.

Ara tornarem a activar el disc que havíem tret, iniciarem la màquina i repetirem els passos inicials, però aquesta vegada **seleccionant 3 discos**.

Provarem la resiliència de tipus **Paritat**.

![img](img/img10.png)

La paritat només utilitza l'espai d'un disc per guardar la informació de protecció.

Això vol dir que, si utilitzem **3 discos de 10 GB**, obtindrem aproximadament **20 GB útils**, ja que 10 GB es destinen a la informació de paritat.

Aquesta configuració és més eficient en espai que el mirall.

## Configuració (Triple Mirror)

Ara, amb la màquina apagada, hem d'afegir **2 discos més** per provar la següent resiliència.

![img](img/img11.png)

Iniciarem la màquina i repetirem la configuració inicial una altra vegada.

![img](img/img12.png)

Ara Windows detectarà els **dos discos nous** i els podrem seleccionar tots.

Un cop seleccionats tots els discos, crearem un **nou grup d'emmagatzematge** i tornarem a configurar-lo.

![img](img/img13.png)

Amb 3 discos ja es podria fer una configuració de resiliència, però per al **Triple Mirror** (reflex triple) es recomana tenir **un mínim de 5 discos** per disposar d'un espai d'emmagatzematge útil i estable.

![img](img/img14.png)

Per comprovar-ho, podem treure 2 discos i tornar a iniciar la màquina.

![img](img/img15.png)

Apareixerà un avís indicant que hi ha hagut una reducció, però el «disc» virtual continuarà funcionant correctament.

