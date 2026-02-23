# SP 3
## LDAP
### Que es LDAP?
**LDAP** (*Lightweight Directory Access Protocol*) és un **protocol** que permet **consultar i gestionar directoris d’informació** a través d’una xarxa.

#### Per a què serveix?
- Gestionar **usuaris i contrasenyes**
- Controlar **permisos i rols**
- Centralitzar l’**autenticació**
#### usuaris
#### Recursos
#### UO

### Instalacio i configuracio 
#### Server:
Editem el fixer hostname i fiquem el nom del nostre server

<img width="420" height="23" alt="image" src="https://github.com/user-attachments/assets/8fa4c5b5-79b9-4914-a248-321b68250b30" />

<img width="730" height="101" alt="image" src="https://github.com/user-attachments/assets/edddcc7c-4111-44a3-abe3-d39b3172c327" />

Ara afegim un host al fixer hosts que sera la IP del nostre servidor, el domini que utilidzarem i el nostre servidor 

<img width="728" height="118" alt="image" src="https://github.com/user-attachments/assets/1c21c1b4-d461-42a6-a52b-7f3de14446b4"/>


Instalem LDAP utilis

<img width="554" height="23" alt="image" src="https://github.com/user-attachments/assets/14e65b3a-ff55-4f01-a112-f428cd78d0a4" />


Ara fem un slapcat

<img width="558" height="269" alt="image" src="https://github.com/user-attachments/assets/c0824959-b40c-4d61-ae22-ac11bbd7ef15"/>

Ara fem el dpkg reconfigure

<img width="571" height="20" alt="image" src="https://github.com/user-attachments/assets/ae7d64b5-e6ed-44f7-9fc5-1dbd5f53fd8b" />


Fiquem el nom del domini

<img width="703" height="274" alt="image" src="https://github.com/user-attachments/assets/9d5627ff-de76-4de3-9395-cec91e56b16f"/>

Nom de l'organitzacio

<img width="703" height="274" alt="image" src="https://github.com/user-attachments/assets/86662991-56d1-4fb1-853b-3aa6d8b3120a" />

Diem que si

<img width="703" height="274" alt="image" src="https://github.com/user-attachments/assets/ad0db8c0-d0a5-4e2d-b76f-44d79d6337f5" />

<img width="703" height="274" alt="image" src="https://github.com/user-attachments/assets/3412757a-babb-40ad-afbf-05c7264f6358" />

Fem un slapcat per a comprobar que la configuracio se a aplicat correctament

<img width="488" height="275" alt="Captura de pantalla de 2026-01-12 12-35-10" src="https://github.com/user-attachments/assets/2c784a67-001e-419c-a874-a27b356ca838" />

Ara modifiquem el fixer uo.ldif

<img width="700" height="172" alt="image" src="https://github.com/user-attachments/assets/4eb087c9-51f7-4ee8-a1f8-d0f132e20e71" />

grup.ldif

<img width="700" height="172" alt="image" src="https://github.com/user-attachments/assets/f82b3dcf-cb58-4b60-aaee-59ec6d8a6632" />

usu.ldif

<img width="722" height="393" alt="image" src="https://github.com/user-attachments/assets/404e41ce-38e5-4c72-9586-b95eccd723f4" />

apliquem les configuracions dels fixers

<img width="650" height="148" alt="Captura de pantalla de 2026-02-04 09-36-27" src="https://github.com/user-attachments/assets/425e76fb-492c-44dd-b1e1-607f8e838a1a" />


#### Client:

instalem els seguents paquets

<img width="496" height="22" alt="image" src="https://github.com/user-attachments/assets/b9f861e9-1a73-4e0b-a6ba-7ecd625cee99" />

configurem elspaquets instalats

fiquem la IP del servidor

<img width="800" height="143" alt="image" src="https://github.com/user-attachments/assets/dd1527fb-a497-44da-a66c-a1f2e2dc41f0" />

El domini

<img width="800" height="143" alt="image" src="https://github.com/user-attachments/assets/acb7cdfe-63c6-45f4-b119-ab91cf464340" />

Si a crear la base de dades

<img width="648" height="151" alt="image" src="https://github.com/user-attachments/assets/2393d381-c41a-4e96-bbe9-3d056e4f3755"/>

Fiquem el usuari root que sera admin

<img width="467" height="192" alt="image" src="https://github.com/user-attachments/assets/a2f65e92-a82b-4706-baff-f4fd912951c4" />

Fem un reconfigure

<img width="648" height="26" alt="image" src="https://github.com/user-attachments/assets/39ca6324-3e80-4df0-b7f0-dfd7ddfcd309" />


Elegim el xifratge md5

<img width="748" height="276" alt="image" src="https://github.com/user-attachments/assets/680c919c-3036-4936-b447-70b412e472d3" />


Editem el fixer nsswitch.conf

<img width="470" height="25" alt="image" src="https://github.com/user-attachments/assets/1562c87b-a097-4a77-a24d-129738d886df" />

<img width="449" height="121" alt="image" src="https://github.com/user-attachments/assets/f7f98e4b-06b0-4943-a6b3-893a25e992a9" />


Modifiquem el fixer common-session

<img width="636" height="34" alt="image" src="https://github.com/user-attachments/assets/a4fdae83-2f62-40e7-84e8-f224e967fd2f" />

<img width="706" height="699" alt="image" src="https://github.com/user-attachments/assets/d7d6bf91-b36c-4894-8332-bf52dc30c092" />

Modifiquem el fixer common-password

<img width="741" height="27" alt="image" src="https://github.com/user-attachments/assets/f316a6c7-7827-4626-ac15-f05ca9435169" />


<img width="672" height="470" alt="image" src="https://github.com/user-attachments/assets/e1740c6d-cdc7-4561-93a6-67741283b469" />

Modifiquem el fixer 50-ubuntu.conf

<img width="770" height="30" alt="image" src="https://github.com/user-attachments/assets/da83d1c7-7d89-4696-9127-419f5694ec70" />

<img width="331" height="74" alt="image" src="https://github.com/user-attachments/assets/387d846c-962f-4d34-83e7-864e372306bd" />

Reiniciem la maquina, entrem al usuari "Primer" del LDAP si no surt a qui has de anar a no esteu al llistat

<img width="657" height="556" alt="image" src="https://github.com/user-attachments/assets/f6231891-44ba-43ea-ab87-e4a803869af1" />

### Interficie grafica

#### Instalacio

Instalem el PHP ldap my admin

<img width="685" height="25" alt="Captura de pantalla de 2026-01-13 13-01-25" src="https://github.com/user-attachments/assets/643e0974-9fa6-4131-bd0d-19e723f08c01" />

Editem el fixer config.php

<img width="769" height="52" alt="Captura de pantalla de 2026-01-13 13-02-36" src="https://github.com/user-attachments/assets/11aba6b1-836c-42fb-bec2-8ed700387937" />

<img width="708" height="694" alt="Captura de pantalla de 2026-01-13 13-08-54" src="https://github.com/user-attachments/assets/a6f335bc-0125-4c48-846c-56593dc5d831" />


#### Us del php ldap my admin

Fiquem la ip del nostre servidor per accedir a la configuracio web

<img width="882" height="977" alt="Captura de pantalla de 2026-01-13 13-12-12" src="https://github.com/user-attachments/assets/252df3d7-3083-4d3f-a1fb-e63d523db4c8" />





## Samba
### Què és Samba?

**Samba** és el programari que actua com a **pont de comunicació** entre sistemes Linux/Unix i sistemes Windows.

#### Funcions principals
*  **Compartir fitxers:** Permet que ordinadors Windows vegin i utilitzin carpetes d'un servidor Linux com si fossin locals.
*  **Compartir impressores:** Fa que qualsevol impressora de la xarxa sigui accessible per a tots els dispositius.
*  **Gestió d'usuaris:** Pot actuar com a controlador de domini per gestionar permisos i contrasenyes centralitzadament.

#### Per què serveix?
Principalment per a la **interoperabilitat**. Gràcies al protocol **SMB**, permet que dispositius amb sistemes operatius diferents col·laborin en una mateixa xarxa sense conflictes.


### Instalacio i configuracio 
#### Server:
Instalem samba

<img width="439" height="25" alt="image" src="https://github.com/user-attachments/assets/36cfc0e4-f353-4775-a02f-f0bf1afbee7d" />

Creem una carpeta proves

<img width="595" height="17" alt="image" src="https://github.com/user-attachments/assets/7fc88070-9306-46b9-87a3-91e86063111d" />

Creem un fixer de prova 

<img width="197" height="33" alt="image" src="https://github.com/user-attachments/assets/97ef59f1-023d-4bfe-ab5e-e1b80a3d7c9c" />

canviem el usuari i li donem tots els permisos

<img width="533" height="36" alt="image" src="https://github.com/user-attachments/assets/199de517-e21b-4cee-a815-055c8de13c2e" />
<img width="515" height="56" alt="image" src="https://github.com/user-attachments/assets/017e2cd1-3045-4cea-9359-6c4b344af0af" />

Creem tres usuaris 

<img width="631" height="42" alt="image" src="https://github.com/user-attachments/assets/929d535e-0f01-47f6-9e3b-77ec8576fbf5" />

<img width="631" height="42" alt="image" src="https://github.com/user-attachments/assets/f0f9a2de-36aa-4bb3-b47b-679b650ef5d1" />

<img width="631" height="42" alt="image" src="https://github.com/user-attachments/assets/6405dc3c-e000-4ff9-bb15-0fbbe59e6d55" />

Creem un grup colors


<img width="631" height="42" alt="image" src="https://github.com/user-attachments/assets/e57e0a43-6982-47ce-ab5d-e3c744e76285" />

afegim el usuari groc i roig al grup colors


<img width="691" height="45" alt="image" src="https://github.com/user-attachments/assets/f8ceb788-3737-457d-afd6-aadf990e817b" />
<img width="691" height="45" alt="image" src="https://github.com/user-attachments/assets/b73ff897-e4f8-4737-96c8-13aef19a9fc8" />

Comprobem que se an creat correctament

<img width="702" height="348" alt="image" src="https://github.com/user-attachments/assets/638eca44-ae37-4fc5-97a1-10d8b22d143d" />


Modifiquem el fixer smb.conf i fiquem la seguent configuracio

<img width="396" height="185" alt="image" src="https://github.com/user-attachments/assets/bcfa0025-b671-4737-8611-6183cd032a25" />

reiniciem els serveis i fem un status 

<img width="785" height="616" alt="image" src="https://github.com/user-attachments/assets/f37ca6da-b953-4efd-8547-888afced1243" />


Les assignem una contrasenya als usuaris per a poder accedir remotament
ls
<img width="465" height="300" alt="image" src="https://github.com/user-attachments/assets/7db872b4-b3c8-4c7f-97c2-0ef621418036" />

client
apt install smbclient
ip a 
ping a server
Compartir amb autinticacio amb IP  tant ubuntu com windowst

### NFS

NTFS es un protoco que ens permet compartir fixer i directoris (no impresores) atrabes de una xarxa local la autenticacion se fa a nivell de host no de usuari, a diferencia de samba. Poden accedir tant clients windows com Linux.  

#### NFS senese ldap

##### Server

<img width="620" height="26" alt="image" src="https://github.com/user-attachments/assets/726ef888-f870-45ea-a912-f903ae2e6877" />


<img width="745" height="24" alt="image" src="https://github.com/user-attachments/assets/8a3a22ed-31f9-4739-a001-2ba20be6ae11" />


<img width="376" height="28" alt="image" src="https://github.com/user-attachments/assets/be4b9942-5a2a-479b-8840-f8390ba2c703" />


Per a compartir la capeta editem el fixer exports i fiquem primer la nostra carpeta i al constat el filtre el filtre que hem ficat amb el asterisc per met el acces a tots el equips per xarxa.

<img width="376" height="28" alt="image" src="https://github.com/user-attachments/assets/a8312a4b-f63a-4780-ac75-2de8e1501f94" />

<img width="521" height="21" alt="image" src="https://github.com/user-attachments/assets/610079b7-d625-41b5-bfb0-b9c14fdf2c17" />


<img width="846" height="214" alt="image" src="https://github.com/user-attachments/assets/47a373db-fe56-4e38-b537-e534e83be30f" />

<img width="448" height="66" alt="image" src="https://github.com/user-attachments/assets/3317021b-6a4d-4906-a88e-a88608b37cea" />


##### client

<img width="643" height="22" alt="image" src="https://github.com/user-attachments/assets/ce18a698-22bf-401e-b6a0-ddba647bc99e" />


<img width="435" height="43" alt="image" src="https://github.com/user-attachments/assets/b987ddaf-fcb9-4894-9f94-0f86ded521ee" />

<img width="440" height="37" alt="image" src="https://github.com/user-attachments/assets/8e72343c-5cf2-4746-bafd-9bf814ed52d6" />

<img width="596" height="25" alt="image" src="https://github.com/user-attachments/assets/1251fc60-8e2b-4783-9bef-861fa2c01633" />

<img width="375" height="39" alt="image" src="https://github.com/user-attachments/assets/6bb52844-8192-445b-8ce4-c4e5c1d94703" />

<img width="844" height="54" alt="image" src="https://github.com/user-attachments/assets/1b484dd0-106c-423f-a99b-73474a617664" />

<img width="885" height="19" alt="image" src="https://github.com/user-attachments/assets/af060ad8-9f32-4c2b-ab75-0f7bbf618d60" />

<img width="556" height="47" alt="image" src="https://github.com/user-attachments/assets/d04b53f9-c3ce-442e-9589-40b9b9df0639" />


#### exercici 2

<img width="495" height="64" alt="image" src="https://github.com/user-attachments/assets/d0e1af30-0253-48c1-a3eb-8861ad8eeed9" />


<img width="478" height="22" alt="image" src="https://github.com/user-attachments/assets/7ae5b7c0-db75-4a2f-8188-cad5d6d07b4e" />


<img width="557" height="42" alt="image" src="https://github.com/user-attachments/assets/bbf894a9-2820-4974-b6d5-9d17b5262a5d" />



<img width="609" height="62" alt="image" src="https://github.com/user-attachments/assets/b4788932-64b5-4970-b9b9-cf27aed00981" />


<img width="723" height="279" alt="image" src="https://github.com/user-attachments/assets/90f0db2d-04d5-457f-beab-66ac314ed068" />


<img width="628" height="29" alt="image" src="https://github.com/user-attachments/assets/6a366fea-66c3-4ab4-bada-beb401170ddb" />


<img width="836" height="518" alt="image" src="https://github.com/user-attachments/assets/9b6e1aa4-f761-4d01-b4f9-0d1f5bfc36ee" />

<img width="867" height="70" alt="image" src="https://github.com/user-attachments/assets/92ec30f5-dc1d-46d5-af07-71ec6f6e557b" />

fem un ls a vans de inicia secio al client
<img width="596" height="58" alt="image" src="https://github.com/user-attachments/assets/ca9e2660-4d02-497b-8caa-bc61cd221b65" />


##### client

<img width="490" height="47" alt="image" src="https://github.com/user-attachments/assets/3d99132e-4239-4340-9a41-9d0e001e311b" />












