# Sprint 4: Configuració del Programari de Base i Sistemes d’Emmagatzematge en Windows (8h)

## Índex
1. [Introducció](#1-introducció)
2. [Desenvolupament de la Pràctica Pas a Pas](#2-desenvolupament-de-la-pràctica-pas-a-pas)
   * [Pas 1: Preparació de la màquina virtual](#pas-1-preparació-de-la-màquina-virtual)
   * [Pas 2: Inicialització i configuració dels discs](#pas-2-inicialització-i-configuració-dels-discs)
   * [Pas 3: Creació del volum RAID 5 des del Gestor de discs](#pas-3-creació-del-volum-raid-5-des-del-gestor-de-discs)
   * [Pas 4: Proves de funcionalitat i accés](#pas-4-proves-de-funcionalitat-i-accés)
   * [Pas 5: Simulació de primera fallada (Un disc Offline)](#pas-5-simulació-de-primera-fallada-un-disc-offline)
   * [Pas 6: Simulació de segona fallada (Dos discs Offline)](#pas-6-simulació-de-segona-fallada-dos-discs-offline)
   * [Pas 7: Recuperació del sistema](#pas-7-recuperació-del-sistema)
3. [Conclusions i Observacions](#3-conclusions-i-observacions)

---

## 1. Introducció
Els RAIDs (Redundant Array of Independent Disks) són sistemes que permeten combinar diversos discos discos físics en una sola unitat lògica per aconseguir millores en rendiment, capacitat o seguretat. Aquests sistemes poden ser gestionats tant per maquinari (controladores RAID) com per programari, sent aquest últim el cas dels sistemes operatius moderns com Windows Server. Cada nivell de RAID ofereix característiques diferents segons si l'objectiu és millorar la velocitat, oferir redundància o combinar ambdues coses.

El RAID 5 és un dels nivells més utilitzats en entorns professionals perquè aconsegueix un equilibri òptim entre rendiment, capacitat i tolerància a fallades. Aquest sistema distribueix tant les dades com la informació de paritat entre tots els discos de la matriu. La paritat té la funció de reconstruir la informació en cas que un dels discos falli, permetent que el sistema segueixi funcionant i garantint la disponibilitat en entorns crítics com els servidors. Per a la seva configuració es requereix un mínim de tres discos durs, i la capacitat útil total és la suma de tots els discos menys un, ja que l'espai equivalent a una unitat es dedica a la paritat.

---

## 2. Desenvolupament de la Pràctica Pas a Pas

### Pas 1: Preparació de la màquina virtual
Abans d'iniciar el sistema operatiu, cal configurar el maquinari virtual necessari per implementar la matriu de discos:
* A la màquina virtual com Windows Server 2022, s'afegeixen un mínim de 3 discos addicionals de la mateixa mida (per exemple, 10 GB cadascun).
* Una vegada connectats els suports d'emmagatzematge, s'inicia la màquina virtual.

<img width="883" height="534" alt="image" src="https://github.com/user-attachments/assets/9a6f4a93-cb97-4821-96fc-bc89c4b8bcb4" />

### Pas 2: Inicialització i configuració dels discs
Un cop arrencat el sistema, s'obre l'eina de **Gestió de discs** mitjançant l'execució de la comanda `diskmgmt.msc`.

<img width="406" height="220" alt="image" src="https://github.com/user-attachments/assets/d3963112-f13f-4245-829a-11fa119e0572" />

Quan es mostri l'assistent automàtic, s'inicialitzen els nous discos triant l'estil de partició MBR o GPT (es recomana GPT si la mida és superior a 2TB, tot i que en aquest cas no afecta).
   
<img width="450" height="322" alt="image" src="https://github.com/user-attachments/assets/ed1d5ba7-d606-4e69-9b12-8b6de6ae1e3a" />

Es mantenen els discos en l'estat inicial, sans formatar-los ni crear-hi cap tipus de partició.

<img width="1207" height="358" alt="image" src="https://github.com/user-attachments/assets/5d30d5ba-215f-4b4b-b787-88642399d258" />


### Pas 3: Creació del volum RAID 5 des del Gestor de discs
Es fa clic amb el botó dret del ratolí sobre un dels nous discos buits i es selecciona l'opció **"New RAID-5 Volume"**.
   
<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/1a1cd729-2ea0-4a2f-a72a-cc52646b845d" />

Dips de l'assistent, s'afegeixen els altres 2 discos restants a la configuració per formar la matriu.
   
<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/b5fd1d0b-ef73-4f31-9e82-56572ca31f34" />

S'assigna una lletra d'unitat al volum.

<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/454ceb04-4ffe-4f97-ad48-d9b19b38e21f" />

7. Es formata el volum utilitzant el sistema de fitxers **NTFS** i s'estableix l'etiqueta de volum: **RAID5-Test**.
   
<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/89e07d9e-e83e-4519-b3cf-be78cf8c1b30" />

9. S'espera que finalitzi el procés de format i es verifica que es mostra com a un volum únic al sistema (amb una capacitat útil de 20 GB, corresponent a la suma dels discos menys l'espai de paritat).

<img width="1277" height="369" alt="image" src="https://github.com/user-attachments/assets/4d6b6ef2-9a68-4308-b0b2-65ec8ca1c124" />


### Pas 4: Proves de funcionalitat i accés
1. S'obre l'Explorador de fitxers de Windows i es desplaça fins al volum `R:\`.
2. Es copien arxius de prova a l'arrel de la unitat (per exemple, una carpeta amb imatges o documents).
3. S'obren i es comprova que els fitxers són completament accessibles i es llegeixen sense problemes.

> **📸 [INSERIR CAPTURA]:** *Mostra l'interior de la unitat R:\ amb els fitxers de prova que has copiat col·locats correctament.*

### Pas 5: Simulació de primera fallada (Un disc Offline)
1. Es torna a accedir a l'eina **Disk Management**.
2. Es fa clic dret sobre un dels tres discos que configuren el RAID i es selecciona l'opció **Offline** per simular una fallada crítica de la unitat.
3. S'observa el comportament del sistema: Windows Server mostrarà un advertiment indicant que el volum es troba en estat degradat, però que segueix estant accessible.
4. Es torna a comprovar que es poden obrir els fitxers de forma normal gràcies a la reconstrucció en temps real per paritat.

> **📸 [INSERIR CAPTURA]:** *Mostra el Gestor de discs reflectint l'estat de "Failed Redundancy" (Redundància fallada) en color groc i el disc seleccionat marcat com a Offline.*

### Pas 6: Simulació de segona fallada (Dos discs Offline)
1. Es procedeix a forçar una segona fallada col·locant un **segon disc en estat Offline**.
2. Atès que el RAID 5 només té tolerància per suportar la fallada d'un sol disc de forma simultània, el volum sencer deixarà de funcionar immediatament.
3. S'intenta accedir de nou a la unitat `R:\` i es comprova que l'accés als arxius queda totalment bloquejat.

> **📸 [INSERIR CAPTURA]:** *Mostra l'Administrador de discs amb l'estat del volum en color vermell i el text "Failed" (Fallat), confirmant la pèrdua de disponibilitat de la matriu.*

### Pas 7: Recuperació del sistema
1. Es fa clic dret sobre un dels discos desconnectats prèviament i es torna a posar en estat **Online**.
2. El volum inicia de forma automàtica la seva recuperació o entra en un procés actiu de reconstrucció de les dades.
3. Es torna a intentar l'accés als arxius de la unitat i es comprova que la integritat de les dades s'ha mantingut.

> **📸 [INSERIR CAPTURA]:** *Mostra l'estat de reconstrucció ("Resynching" o "Regenerating") en el Gestor de discs o el volum completament sanejat un cop acabat el procés.*

---

## 3. Conclusions i Observacions
* **Distribució de paritat:** S'ha comprovat com el RAID 5 distribueix de manera eficient la paritat i les dades entre tots els components de la matriu.
* **Tolerància limitada:** El sistema ofereix redundància i tolera correctament la fallada d'un sol disc dur, mantenint els serveis operatius en entorns de producció.
* **Penalització d'escriptura:** Atès que la paritat es calcula i s'escriu automàticament cada vegada que es graven dades, s'ha de tenir en compte que hi ha una petita penalització en el rendiment d'escriptura, encara que la lectura és molt eficient.
* **No és un backup:** Tot i la seva resistència davant de la pèrdua d'una unitat, **el RAID 5 no substitueix una còpia de seguretat**. Si dues unitats fallen simultàniament o es produeix corrupció de dades, es perdran tots els fitxers de forma irreversible. A més, el procés de reconstrucció pot ser llarg i estressant per a la resta de discos de la matriu.
* **Recomanació:** No és adequat per a entorns on la màxima disponibilitat o protecció total sigui crítica; en aquests casos és obligatori combinar-lo amb sistemes de backup externs o avaluar alternatives com RAID 6 o RAID 10.
