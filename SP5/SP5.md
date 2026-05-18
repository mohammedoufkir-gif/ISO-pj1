
# Sprint 5: Monitoratge, Auditories i Programari Client/Servidor (20h)

## Rendiment

<img width="983" height="916" alt="image" src="https://github.com/user-attachments/assets/2f02a6d1-54c4-4290-a2ab-28b46b5fc37e" />

<img width="971" height="909" alt="image" src="https://github.com/user-attachments/assets/508c9305-617f-4884-915a-9aadac5f345a" />

<img width="957" height="612" alt="image" src="https://github.com/user-attachments/assets/411a3696-e2ec-4430-b02d-cff6a880af2b" />

<img width="968" height="521" alt="image" src="https://github.com/user-attachments/assets/0bfb3b95-fe0c-4d63-b673-2d177df5a4d0" />

<img width="980" height="339" alt="image" src="https://github.com/user-attachments/assets/cee970e2-2ec6-47f1-9b6d-c32a4c54083b" />

<img width="999" height="904" alt="image" src="https://github.com/user-attachments/assets/90f4a49e-3ee2-474f-8beb-b43c6cc61dc7" />

<img width="999" height="904" alt="image" src="https://github.com/user-attachments/assets/12e551b8-2df9-47a2-8199-fffaeb0f5917" />

<img width="735" height="195" alt="image" src="https://github.com/user-attachments/assets/4ebf7e1e-475f-4989-82c8-d9d0905c76a7" />

## Servidor d'actualitzacions

### 1. Instal·lació dels paquets necessaris



Es realitza la instal·lació dels serveis bàsics per al funcionament del repositori local: el propi gestor de rèpliques i el servidor web Apache per a servir els fitxers.  

<img width="292" height="17" alt="image" src="https://github.com/user-attachments/assets/41e8f17f-9c2b-4dd5-b508-0434477d409d" />

Modifiquem el fitxer /etc/apt/mirror.list amb l'editor nano per definir quins repositoris volem clonar s'afegeix exclusivament el repositori oficial de Google Chrome de 64 bits:

<img width="305" height="25" alt="image" src="https://github.com/user-attachments/assets/0949e85f-b12b-4579-8fba-6ffdbb6ba0d8" />


Executem l'ordre apt-mirror per iniciar la sincronització. El sistema processa els índexs i calcula que es descarregaran 474.7 MiB d'arxius cap al nostre disc local en 4 fils dedicats per a la secció d'índexs:

<img width="766" height="501" alt="Captura de pantalla de 2026-03-09 12-28-49" src="https://github.com/user-attachments/assets/42d71fd7-1562-4e69-9a8c-c368087aad94" />


Els fitxers es descarreguen per defecte a la ruta /var/spool/apt-mirror/mirror/dl.google.com/. Perquè el servidor Apache pugui servir-los, creem un enllaç simbòlic cap al directori d'arrel web /var/www/html/.

<img width="1286" height="596" alt="Captura de pantalla de 2026-03-09 12-29-21" src="https://github.com/user-attachments/assets/e28891d1-d814-4876-932a-f966853f0361" />

Comprovem amb un llistat (ls) que l'enllaç s'ha creat correctament al costat del fitxer index.html per defecte d'Apache

<img width="1797" height="314" alt="Captura de pantalla de 2026-03-09 12-38-03" src="https://github.com/user-attachments/assets/23041470-6462-4da5-b53a-ee205abde2dc" />

La URL resultant per als clients de la nostra xarxa interna (on la IP del nostre servidor és 10.0.2.6) serà:

<img width="855" height="43" alt="Captura de pantalla de 2026-03-09 12-42-24" src="https://github.com/user-attachments/assets/6523bef5-f865-4ae1-ac6a-bd66262a307e" />

Perquè el client confiï en els paquets del repositori, descarreguem i afegim la clau pública oficial de signatura de Google:

<img width="890" height="138" alt="Captura de pantalla de 2026-03-09 12-45-06" src="https://github.com/user-attachments/assets/1c21ac8e-94bd-4d66-ae80-dcaf4940168e" />

Un cop afegida la línia del repositori local al fitxer del client i actualitzat el sistema, procedim a instal·lar el navegador Google Chrome:

Podem veure que se instala desde el nostre servidor local

<img width="877" height="939" alt="Captura de pantalla de 2026-03-09 12-48-05" src="https://github.com/user-attachments/assets/5031d4d2-3396-4acc-b660-de61ae53a61a" />




