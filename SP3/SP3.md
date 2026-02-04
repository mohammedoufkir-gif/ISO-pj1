# Sprint 3: Administració de Dominis i Seguretat 
## LDAP
### Que es LDAP?
**LDAP** (*Lightweight Directory Access Protocol*) és un **protocol** que permet **consultar i gestionar directoris d’informació** a través d’una xarxa.

#### Per a què serveix?
- Gestionar **usuaris i contrasenyes**
- Controlar **permisos i rols**
- Centralitzar l’**autenticació**
  
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

<img width="703" height="274" alt="image" src="https://github.com/user-attachments/assets/9d5627ff-de76-4de3-9395-cec91e56b16f" />

Nom de l'organitzacio

<img width="703" height="274" alt="image" src="https://github.com/user-attachments/assets/86662991-56d1-4fb1-853b-3aa6d8b3120a" />

Diem que si

<img width="703" height="274" alt="image" src="https://github.com/user-attachments/assets/ad0db8c0-d0a5-4e2d-b76f-44d79d6337f5" />
<img width="703" height="274" alt="image" src="https://github.com/user-attachments/assets/3412757a-babb-40ad-afbf-05c7264f6358" />

Fem un slapcat per a comprobar que la configuracio se a aplicat correctament

<img width="488" height="275" alt="Captura de pantalla de 2026-01-12 12-35-10" src="https://github.com/user-attachments/assets/2c784a67-001e-419c-a874-a27b356ca838" />


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

<img width="465" height="300" alt="image" src="https://github.com/user-attachments/assets/7db872b4-b3c8-4c7f-97c2-0ef621418036" />

client
apt install smbclient
ip a 
ping a server

nfs 


Compartir amb autinticacio amb IP  tant ubuntu com windowst
