# Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers (20h)

## Sistemes de fitxers i particions

### Mida de sector
La mida del sector és la unitat mínima **física** on es guarden les dades en un disc. Per defecte és de **512 bytes** (en discs moderns pot ser de 4096 bytes). Aquesta mida **no es pot modificar**.

### Mida de bloc
La mida del bloc (o *cluster*) és la unitat mínima **lògica** on es guarden les dades a nivell de sistema operatiu.  
Per defecte és de **4096 bytes (4 KB)**, equivalent a 8 sectors.  
<img width="853" height="105" alt="image" src="https://github.com/user-attachments/assets/5a5782bf-aee4-4626-8b1e-454b49258725" />

Creem un fixer amb echo.

Despres fem du -b per veure la mida del fixer.

Despres podem comprobar la mida real amb du -sh podem veure que ocupa 4,0k per que es la mida minima dins del sistema opratiu.

<img width="1021" height="234" alt="Captura de pantalla de 2025-10-27 12-29-53" src="https://github.com/user-attachments/assets/e9bb5383-30bd-4600-9848-99d1e5a6e75c" />

Aquesta mida **es pot modificar** quan es formata la partició.  
Cada partició pot tenir el seu **propi sistema de fitxers** i la seva **pròpia mida de bloc**.

### Fragmentació interna
La fragmentació interna es produeix quan la mida dels blocs és més gran que la mida dels arxius que s’hi guarden. Això provoca **desaprofitament d’espai**.

### Fragmentació externa
La fragmentació externa es produeix quan un fitxer **no està guardat en blocs consecutius**. Això fa que els accessos siguin **més lents**, ja que el disc ha de llegir-lo en diferents zones.

### Sistema de fitxers
Hi ha molts tipus de sistemes de fitxers. Cada un està **optimitzat per funcions concretes** i té **limitacions pròpies** (mida màxima d’arxiu, inodes, etc.).

---

### Tipus de formateig

#### Baix nivell
- Elimina tot.  
- Reconstrueix estructures físiques i pot **reparar sectors defectuosos**.  
- Necessita programes específics.  
- No s’usa habitualment en discs moderns.

#### Mig nivell
- Similar a l’alt nivell però **marca sectors defectuosos** per no utilitzar-los.

#### Alt nivell
- No elimina tots els arxius físicament; només **esborra el sistema de fitxers**.  
- Si troba sectors defectuosos, normalment **els ignora**.

---

### Partició
Una partició és un **tros físic del disc dur**.  
Amb eines com **GParted** podem crear, eliminar i redimensionar particions, però **no podem canviar la mida de bloc** sense tornar a formatar.

### Volum
Un volum és una **capa d’abstracció** per damunt de les particions i/o discs, utilitzada per sistemes com LVM o RAID.

---

### Gestió de particions

#### GParted
Eina gràfica per:
- Crear particions  
- Redimensionar  
- Eliminar  
- Formatar  
- Veure sistemes de fitxers
#### Creacio de particions amb GParted
Pera crear una particio amb Gparted podem seguir els seguents pasos
<img width="816" height="561" alt="image" src="https://github.com/user-attachments/assets/6a000586-4d9f-4094-83a3-2f386e563388" />
<img width="602" height="487" alt="image" src="https://github.com/user-attachments/assets/2c6f3529-d029-4396-bc52-5dc414cdf473" />
<img width="902" height="313" alt="image" src="https://github.com/user-attachments/assets/95878d7d-b2ba-42ae-bf43-55fc07c08cc2" />
<img width="602" height="487" alt="image" src="https://github.com/user-attachments/assets/59939785-43e6-4ff9-85a4-2179e4c8848e" />
<img width="799" height="366" alt="image" src="https://github.com/user-attachments/assets/c5c5ece0-27bc-4766-b479-d8c357d53a17" />
<img width="799" height="366" alt="image" src="https://github.com/user-attachments/assets/96e604dc-5ab9-4bc7-8b4d-188c37b5c6ea" />

---

### Comandes (Linux)
#### Creacio de particions amb la mateixa mida de block
per a crear 2 particions amb diferents tamanys de block primer hem de identificar primer el disc que volem formata amb ***lsblk o fdisk -l***

<img width="636" height="103" alt="Captura de pantalla de 2025-10-27 12-48-20" src="https://github.com/user-attachments/assets/c72d962b-b1b2-4da4-b6ce-eb1929bb6fa3" />

Una vegada fet aixo podem crear la primera particio en format ext4 amb la opcio -b podem elegir la mida de block en aquest cas sera 2048.

<img width="733" height="299" alt="Captura de pantalla de 2025-10-27 12-54-26" src="https://github.com/user-attachments/assets/69dc7335-36e2-49f3-be0d-e12b2fea6a54" />

Ara formatem l'atra particio com ntfs no especifiquem la mida de block aixo esque per defecte agafara la mida de 4048

<img width="743" height="120" alt="Captura de pantalla de 2025-10-27 12-55-13" src="https://github.com/user-attachments/assets/31c14e55-f831-4b33-98ab-96dc464885b1" />

Ara podem comprobar que la mida de bloc de la primera particio

<img width="743" height="120" alt="Captura de pantalla de 2025-10-27 12-56-36" src="https://github.com/user-attachments/assets/f4a3497e-2795-4c31-8ad6-e67636ea920f" />

#### monta automanicament una particio
Primer creem una carpeta dins de la carpeta /mnt.

<img width="561" height="27" alt="image" src="https://github.com/user-attachments/assets/cde1dd92-be0e-4dc8-a5e7-726bc83b9e9c" />

Una vegada creada accedim a la carpeta i crem un fixer proba.

<img width="550" height="94" alt="image" src="https://github.com/user-attachments/assets/da15097a-21b8-4cdb-8af8-8701f9648f7e" />

Ara montem manualment la particio sda1 dins de la carperta creada. 

<img width="631" height="38" alt="image" src="https://github.com/user-attachments/assets/b7452eae-a411-4214-8552-400a53f669e1" />

Ara tornem a entrar a la carpeta i fem un ls podem comprobar que no nomes hi ha un un directori lost+found i no el archiu creat anterior ment ja que hem montat la particio ahi.

<img width="670" height="73" alt="image" src="https://github.com/user-attachments/assets/73d8328e-de87-4406-a22d-05d1ba971744" />

Ara creem una carpeta dins,

<img width="446" height="59" alt="image" src="https://github.com/user-attachments/assets/50df3b6d-eb41-4f72-94b0-24f8a9d90092" />

Com hem montat la particio manualment si reinciem la maquina, tornem a aquesedir a la carpeta i fem un ls, podrem comprobar que ja no esta montada la particio i que ara esta ahi el fixer creat anteriorment.

<img width="468" height="100" alt="Captura de pantalla de 2025-10-27 13-13-55" src="https://github.com/user-attachments/assets/81c185fc-1d5d-40ae-8473-7cde9a7a4f96" />

Ara tornem a muntar la particio.

<img width="575" height="84" alt="Captura de pantalla de 2025-10-27 13-14-30" src="https://github.com/user-attachments/assets/a196bfc1-8f12-4301-8c47-557ef0914275" />

I comprobem que tormen a tindre la carpeta creada anteriorment.

<img width="575" height="84" alt="Captura de pantalla de 2025-10-27 13-15-16" src="https://github.com/user-attachments/assets/c464d4ee-2170-44b6-b8af-7a8ae86c0d11" />


Ara per a poder tindtre sempre montada la particio, modifiquem el fixer /etc/fstab  i afegim la seguen linea.

<img width="575" height="84" alt="Captura de pantalla de 2025-10-27 13-16-27" src="https://github.com/user-attachments/assets/e0e605d6-af09-408d-8598-f5cbd6b3eae8" />

Ara reiniciem el sistema i comprobem que ja no es necesari mota la particio ja que es fa automaticamnet.

<img width="458" height="121" alt="Captura de pantalla de 2025-10-27 13-18-22" src="https://github.com/user-attachments/assets/f1587aca-bcd8-4130-86f9-8f41f6f681de" />



## Gestió de procesos
## Gestió d'usuaris i grups i permisos

A Ubuntu hi ha una alternativa amb interfície gràfica per fer aquesta tasca de manera més senzilla: gnome-system-tools.

<img width="741" height="444" alt="image" src="https://github.com/user-attachments/assets/3cb7aea4-552a-4cec-8f02-ddb4f158d927" />

### fixers implicats i drectoris 

Passwd 
/etc/passwd: Guarda la informació bàsica de l'usuari (nom, identificadors UID/GID, directori home i shell d'inici).

<img width="831" height="515" alt="Captura de pantalla de 2025-11-04 12-52-30" src="https://github.com/user-attachments/assets/bb4e3da7-0f5d-46a4-bacc-3c1e411e6f93" />

Group 
/etc/group: Guarda la definició dels grups (nom del grup, GID) i la llista dels membres de cada grup.

<img width="831" height="515" alt="Captura de pantalla de 2025-11-04 12-55-32" src="https://github.com/user-attachments/assets/32d0024e-372e-4442-a22a-b709cee31483" />

Shadow 
/etc/shadow: Guarda la contrasenya xifrada (hash) de l'usuari i les polítiques de caducitat (quan es va canviar, quan s'ha de canviar, etc.).

<img width="831" height="515" alt="Captura de pantalla de 2025-11-04 12-56-54" src="https://github.com/user-attachments/assets/1dca2ba6-aa7c-468b-9168-e338479dc707" />
gshadow 
/etc/gshadow: Guarda la contrasenya xifrada del grup (si se n'utilitza) i la llista dels administradors del grup.

<img width="831" height="515" alt="Captura de pantalla de 2025-11-04 12-58-20" src="https://github.com/user-attachments/assets/d4dc965a-589b-4558-9394-85bdc6147971" />
Skel
Quan un administrador crea un compte d'usuari nou, el sistema operatiu copia automàticament tots els fitxers i subdirectoris que hi ha a /etc/skel

### Comandes basiques
La comanda adduser serveix per a crear usuari humans, la carpeta hom no es creara fins que el usuari inici secio. 

<img width="1306" height="586" alt="image" src="https://github.com/user-attachments/assets/f2722db5-ba9d-4fc2-b176-e3b9ce1b0e5c" />

Ara utilidzarem la comanda useradd la comanda useradd sol ser mol util per a crear scripts, ara la diferencia amb l'anterior es que aquesta hem de assigan una contrasenya per a poder inicia secio i no es copiaran els fixer de skel

<img width="725" height="38" alt="image" src="https://github.com/user-attachments/assets/bffda872-ac99-4b08-a19e-d34ada2e0854" />

Assignem una contrasenya

<img width="569" height="32" alt="image" src="https://github.com/user-attachments/assets/86e05c4a-3c0f-4484-af10-91f5a8db9fc0" />

i creem un home 

<img width="569" height="32" alt="image" src="https://github.com/user-attachments/assets/d73d384f-27bf-4fb1-bf55-ed19b52f79c6" />

<img width="569" height="32" alt="image" src="https://github.com/user-attachments/assets/aa857f12-d7c7-4617-99e5-637c38e850c1" />

deluser sense elminar la carpeta home 

<img width="569" height="32" alt="image" src="https://github.com/user-attachments/assets/d381781b-16af-4e27-99ae-dfc4e7ddb5c4" />

userdel -r per eleminar el usuari amb la carpeta home

<img width="569" height="32" alt="image" src="https://github.com/user-attachments/assets/53fa1587-8e2e-4119-8b77-213bccce24a0" />

per a crear un grup utilidzem groupadd

<img width="624" height="45" alt="image" src="https://github.com/user-attachments/assets/35554188-14b2-4325-b512-c27694e36c85" />

desactivar usuari

***sudo passwd -u nom_d'usuari***

activar usuari

***sudo passwd -l nom_d'usuari***

renombra el nom del grup

***sudo groupmod -n nou_nom_grup antic_nom_grup***

afegir grups a un usuari

***sudo usermod -aG nom_del_grup nom_usuari***
Eliminar un usuari d'un grup suplementari amb deluser
***sudo deluser nom_usuari nom_del_grup***

al fixer  /etc/skel/.profile podem determina la ubicacio del usuari al inicia secio

<img width="638" height="301" alt="image" src="https://github.com/user-attachments/assets/4c55a90f-bbad-4ae0-9a31-2f5935027b6d" />

### gestio de permisos

en la seguent imatge podem veure el orden que segeix linux per a assigna els permisos r: lectura w: escritora x: execucio, cada un equival e un 1 bit per exemple si nomes volem lectura  seria 4.

Lectura (r) = 4

Escritura (w) = 2

Ejecución (x) = 1

<img width="472" height="196" alt="image" src="https://github.com/user-attachments/assets/56b0c1d6-d63b-463d-ae73-d2282983e84d" />

ls -la ens permet veure els permisos que te un fixer

<img width="567" height="128" alt="image" src="https://github.com/user-attachments/assets/9400f52c-8349-42ba-8a46-55949b764974" />

per a modificar els permisos podem utilidzar chmod

<img width="619" height="114" alt="image" src="https://github.com/user-attachments/assets/5da3f0c9-b421-4bb5-806a-e1c50e17f2c8" />

---
per a fer les proves creemun grup palomes

<img width="725" height="98" alt="Captura de pantalla de 2025-11-18 13-43-43" src="https://github.com/user-attachments/assets/462617c6-9d13-406f-8047-76126d39525c" />

creem els 4 usuaris 

<img width="540" height="32" alt="image" src="https://github.com/user-attachments/assets/382e9bb2-9dfe-4c46-9b0e-6780fc373ac0" />


<img width="494" height="25" alt="image" src="https://github.com/user-attachments/assets/d353b512-5820-4fd8-8ea2-af7294ad3617" />


<img width="494" height="25" alt="image" src="https://github.com/user-attachments/assets/168ecce7-fff4-47e9-a20b-9b2dd706832c" />


<img width="725" height="98" alt="Captura de pantalla de 2025-11-18 13-45-00" src="https://github.com/user-attachments/assets/d3f7902e-67b6-4a36-b9ba-5642664d1fd7" />

ara creem una carpeta palomes 

<img width="725" height="98" alt="Captura de pantalla de 2025-11-18 13-45-46" src="https://github.com/user-attachments/assets/53036a96-0240-4aca-a3bf-b40c4857265a" />

el propetari sera nick

<img width="393" height="33" alt="image" src="https://github.com/user-attachments/assets/890b685b-29c4-4a2f-b6c5-65bbeb186bbb" />

<img width="735" height="47" alt="Captura de pantalla de 2025-11-18 13-47-58" src="https://github.com/user-attachments/assets/c8a80a48-ca5b-4b66-9be3-c024596c968c" />


ara afegim a cire al grup de paloma

<img width="734" height="75" alt="Captura de pantalla de 2025-11-18 13-51-09" src="https://github.com/user-attachments/assets/afa861ec-2195-4bcd-911a-5a7e948dbb66" />

donem els seguents permisos

<img width="543" height="54" alt="image" src="https://github.com/user-attachments/assets/751fc412-61c9-4ecc-ad92-3a73d84d564b" />

Ara podem comprovar si entem com a nick ens permet llistar archius crer archius aixo per que es propetari i te els permisos 7 rwx

<img width="599" height="124" alt="image" src="https://github.com/user-attachments/assets/79d07317-b357-470e-bed3-945fa32aa18c" />

En canvi cire com es membre del grup palomes nomes te els permisos 5 r-x, nomes podra llista els archius pero ni crear ni elminar

<img width="593" height="138" alt="image" src="https://github.com/user-attachments/assets/a5f2f7f5-43a0-4937-aacd-d6506ab25d1b" />

en canvi ferran no pot ni accedir a la carpeta ni llistarla desde fora

<img width="577" height="118" alt="image" src="https://github.com/user-attachments/assets/8d81da5c-a38a-482f-bac1-45ea1ea339db" />

ara afegim a ferran i deivi a paloma

<img width="503" height="78" alt="image" src="https://github.com/user-attachments/assets/7459682a-3e90-4b75-8669-8e760c600d2b" />

ara canviem els permisos per 770
<img width="304" height="31" alt="image" src="https://github.com/user-attachments/assets/6ced047d-ec70-4e0b-9d63-ff415ecd4d9a" />
<img width="773" height="80" alt="Captura de pantalla de 2025-11-18 13-56-39" src="https://github.com/user-attachments/assets/7f399c1f-ef1e-4dc5-9dd7-51b1af1242d3" />

Una vegada fet podrem comprobar que desde els comptes de ferran i deivi podem fer tot lo anterior 
<img width="745" height="278" alt="Captura de pantalla de 2025-11-18 13-57-30" src="https://github.com/user-attachments/assets/ca194cae-d51f-4edb-b297-ee523f198938" />

## Còpies de seguretat i automatització de tasques
## Quotes d'usuari

