

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

Creem tres usuaris 

<img width="515" height="56" alt="image" src="https://github.com/user-attachments/assets/017e2cd1-3045-4cea-9359-6c4b344af0af" />

<img width="631" height="42" alt="image" src="https://github.com/user-attachments/assets/929d535e-0f01-47f6-9e3b-77ec8576fbf5" />

<img width="631" height="42" alt="image" src="https://github.com/user-attachments/assets/f0f9a2de-36aa-4bb3-b47b-679b650ef5d1" />

Creem un grup colosrs

<img width="631" height="42" alt="image" src="https://github.com/user-attachments/assets/6405dc3c-e000-4ff9-bb15-0fbbe59e6d55" />


afegim el usuari groc i roig al grup colors
<img width="631" height="42" alt="image" src="https://github.com/user-attachments/assets/e57e0a43-6982-47ce-ab5d-e3c744e76285" />


<img width="691" height="45" alt="image" src="https://github.com/user-attachments/assets/f8ceb788-3737-457d-afd6-aadf990e817b" />

Comprobem que se an creat correctament

<img width="691" height="45" alt="image" src="https://github.com/user-attachments/assets/b73ff897-e4f8-4737-96c8-13aef19a9fc8" />

Modifiquem el fixer smb.conf
<img width="396" height="185" alt="image" src="https://github.com/user-attachments/assets/bcfa0025-b671-4737-8611-6183cd032a25" />

fiquem la seguent configuracio
<img width="702" height="348" alt="image" src="https://github.com/user-attachments/assets/638eca44-ae37-4fc5-97a1-10d8b22d143d" />

reiniciem els serveis i fem un status 
<img width="785" height="616" alt="image" src="https://github.com/user-attachments/assets/f37ca6da-b953-4efd-8547-888afced1243" />
<img width="886" height="758" alt="image" src="https://github.com/user-attachments/assets/67c0ec0e-3f30-4529-b00d-8ebbb565ed21" />








<img width="465" height="300" alt="image" src="https://github.com/user-attachments/assets/7db872b4-b3c8-4c7f-97c2-0ef621418036" />

client
apt install smbclient
ip a 
ping a server

nfs 


Compartir amb autinticacio amb IP  tant ubuntu com windowst
