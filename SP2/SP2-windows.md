# Planificació de Sprint 2: Configuració Avançada de Windows

## Índex
1. [Fase 1: Preparació del sistema](#fase-1---preparació-del-sistema)
2. [Fase 2: Quotes i usuaris](#fase-2---quotes-i-usuaris)
3. [Fase 3: Script de còpia i automatització](#fase-3---script-de-còpia-i-automatització)
4. [Fase 4: Verificació i documentació](#fase-4---verificació-i-documentació)
5. [Fase 5: Gestió de processos i serveis](#fase-5---gestió-de-processos-i-serveis)
6. [Fase 6: Gestió de permisos (ACLs)](#fase-6---gestió-de-permisos-acls)

---

## Fase 1 - Preparació del sistema
* Afeggim un dis vdi a la nostra maquina
  
<img width="742" height="450" alt="image" src="https://github.com/user-attachments/assets/5e1d2f73-8eb3-41a3-9121-57265d613fa1" />
  
* Creacio de partcions

NTFS DADES

<img width="499" height="394" alt="image" src="https://github.com/user-attachments/assets/069e517f-08a8-4ef9-8b64-e23613c36cff" />

FAT32 PORTABLE

<img width="499" height="394" alt="image" src="https://github.com/user-attachments/assets/a7aa07a4-b0ed-4ac3-9fb2-ea162e0edaca" />

<img width="762" height="106" alt="image" src="https://github.com/user-attachments/assets/d1209893-3525-4995-906b-d3296025d370" />



* Assignar lletres d'unitat i comprovar la configuració final mitjançant la comanda `diskpart`.
  
Assignem les lletres

<img width="489" height="342" alt="image" src="https://github.com/user-attachments/assets/356f4c00-5b5f-4476-81b2-ff572a34ec64" />

<img width="388" height="273" alt="image" src="https://github.com/user-attachments/assets/89526098-e86a-44cd-a7a0-a93603b4dd98" />

Comprobem amb diskpart les particions creades al disk

<img width="581" height="162" alt="image" src="https://github.com/user-attachments/assets/db0f33f7-f651-45ac-9c9d-5d8f1537d461" />

Surt una particio mes per que hem elegit la taula de particions GPT aixo lo que fa es que windows cree una nova particio que es diu MSR (Microsoft Reserved Partition).


## Fase 2 - Quotes i usuaris
* Activar les quotes de disc a la partició Dades, establint un límit de 300 MB per usuari amb notificació d'advertència.

Per actva les quotes hem de fer clic dret al volum que li volem fica alguna quota

<img width="470" height="511" alt="image" src="https://github.com/user-attachments/assets/11aa8058-7a66-434f-b9b1-6967bc10a486" />

<img width="376" height="503" alt="image" src="https://github.com/user-attachments/assets/947b3a51-5b17-4a0f-aa23-bf807cc34d0d" />

Ara anem a cuota

<img width="376" height="503" alt="image" src="https://github.com/user-attachments/assets/e9416f5f-2e9b-4657-bcc6-aaefc67c4364" />

Mostra configuracio de couota i assegnim 300MB de cuota i 200 MB per la advertencia

<img width="376" height="503" alt="image" src="https://github.com/user-attachments/assets/c7062179-ea37-4545-a371-25f22679bb5d" />


* Crear els usuaris locals `alumne1` i `alumne2` i afegir-los al nou grup "Limitats".

Per a crear els usuaris anem a administracio d'equips

<img width="298" height="582" alt="image" src="https://github.com/user-attachments/assets/7cab2625-6eeb-472a-9271-5d5a90e93b2c" />

Usuaris i grups locals > usuaris

<img width="185" height="81" alt="image" src="https://github.com/user-attachments/assets/a7e874b3-7abc-4828-bd2f-e12ecf1eadf0" />

Ara adins podem fer clic dret i usuari nou

<img width="264" height="226" alt="image" src="https://github.com/user-attachments/assets/6976805b-82d5-4b52-bd37-9f58fa391dfd" />

Creem primer el usuari alumne1 

<img width="436" height="404" alt="image" src="https://github.com/user-attachments/assets/f7f61474-18ea-44c1-8458-570fdeadb3ab" />

I alumne2

<img width="436" height="404" alt="image" src="https://github.com/user-attachments/assets/54e6f138-13fc-46fe-b842-f42b81d17890" />

* Provar la còpia de fitxers fins a superar el límit per verificar que la quota bloqueja l'escriptura.
Entrem desde un dels usuaris  creats

<img width="240" height="232" alt="image" src="https://github.com/user-attachments/assets/9b427976-386e-4bae-828e-0668bfe8e83e" />

Per a fer les proves he agafat un fixer de 90MB 

<img width="277" height="172" alt="image" src="https://github.com/user-attachments/assets/a76c446e-46b5-4e84-86db-4b91bc2bc7cb" />

Podem comprobar que al supera el limit de 300 MB no hem deixa pujar mes fixers

<img width="594" height="469" alt="image" src="https://github.com/user-attachments/assets/5865dc20-92c3-416b-b209-ff24d58c2b23" />


## Fase 3 - Script de còpia i automatització
* Afegir un tercer disc virtual (Backups) en format NTFS i crear la carpeta `CòpiesUsuaris`.
  
Affegim un nou disc virtual

<img width="892" height="553" alt="Captura de pantalla de 2026-05-05 08-46-18" src="https://github.com/user-attachments/assets/79f0f683-e280-4279-9cd3-93480aa5e4bc" />

Ara el fortem com a NTFS

<img width="606" height="464" alt="image" src="https://github.com/user-attachments/assets/9b226d71-ef59-4227-8068-5d486dad2475" />

Creem la carpeta CòpieUsuaris a dins del disc de Backup

<img width="785" height="612" alt="image" src="https://github.com/user-attachments/assets/867848b8-05fd-46fd-93b4-3af0bb817683" />


* Crear un fitxer `script.bat` que copiï el contingut de la carpeta de l'usuari actual cap a la unitat de Backups.

Fixer 

<img width="750" height="517" alt="image" src="https://github.com/user-attachments/assets/cf877ea4-45ba-41ee-b3b5-b79efc862013" />

Comprobacio del funcionament

<img width="790" height="595" alt="image" src="https://github.com/user-attachments/assets/c98cb7c1-059a-44d8-98b2-d60e691650ff" />

*  Utilitzar `gpedit.msc` per configurar l'script perquè s'executi automàticament en l'inici de sessió.


Per a configura que el escript es ejecuta cada que iniciem anem a Gpedit >Configguracio d'equip> Configuracio de windows> Scripts> Inici

<img width="761" height="552" alt="image" src="https://github.com/user-attachments/assets/8b466b9a-8077-4be2-b67f-67cc3dbce2e1" />

Ara fem clic a affegir

<img width="394" height="458" alt="image" src="https://github.com/user-attachments/assets/61202a48-5594-439f-85d9-a790c2f2588f" />

cerquem el fixer

<img width="623" height="496" alt="image" src="https://github.com/user-attachments/assets/29324146-31e8-4b36-97b1-916e6c2100f3" />

per ultim fem clic a accesptar

<img width="444" height="464" alt="image" src="https://github.com/user-attachments/assets/36cd8570-828e-4984-93ea-f4ae7bf81579" />





## Fase 4 - Verificació i documentació
* Iniciar sessió amb els usuaris creats per comprovar que l'automatització funciona i que les restriccions d'espai s'apliquen correctament.

Comprobem el funcionamen del script, podem veure que al inicia  amb un dels usuaris creat anteriorment se fa la copia de seguretat automaticament

<img width="831" height="615" alt="image" src="https://github.com/user-attachments/assets/9c1c2cae-edcb-4987-8b1c-3556e6ef5a8e" />


## Fase 5 - Gestió de processos i serveis
*  Llistar i exportar els processos actius a un fitxer de text mitjançant `tasklist > procesos_inici.txt`.

Ara amb la comanda  asklist > procesos_inici.txt gener un fixer de text amb els procesos actius

<img width="355" height="17" alt="image" src="https://github.com/user-attachments/assets/7fb486a7-1dcf-49bd-91cd-4c4c014658e3" />

fixer generat

<img width="746" height="516" alt="image" src="https://github.com/user-attachments/assets/f7de0c0b-677c-4ab4-8788-7853603562ca" />


* Identificar processos no essencials (OneDrive, Teams, Skype) i eliminar-los manualment amb la comanda `taskkill /IM [nom] /F`.
  
Eleminarem el seguent process

<img width="725" height="25" alt="image" src="https://github.com/user-attachments/assets/027444df-5af0-41d2-a3f4-fb8426c13d29" />

ara amb la comanda  taskkill /IM M365Copilot.exe /F

<img width="533" height="31" alt="image" src="https://github.com/user-attachments/assets/2725faa0-3a85-4f84-bcaf-b0c7c76623d0" />

* Automatitzar el tancament d'aquests processos a l'script d'inici i documentar la millora de rendiment a la màquina virtual.

  
Ara incorporem lla comanda taskill al script per cuan inicie el windows es tanquen automaticament els procesos no esencials de Onedrive, Teams, Skype

<img width="513" height="746" alt="image" src="https://github.com/user-attachments/assets/640d3a98-72de-4307-af9a-7c8da9ffa513" />

## Fase 6 - Gestió de permisos (ACLs)
### ACLs a Windows (Access Control Lists)

Les **ACLs** són el mecanisme de seguretat de Windows per gestionar qui pot accedir a fitxers i carpetes.

1. Components
* **ACE (Access Control Entry):** Les entrades individuals que formen la llista (Usuari + Permís).
* **DACL (Discretionary ACL):** Defineix qui té permís d'accés.
* **SACL (System ACL):** Registra intents d'accés (auditoria).

2. Regles d'Or
1.  **La Denegació mana:** Si un usuari té un permís de "Denegar", aquest ignora qualsevol altre permís de "Permetre".
2.  **Herència:** Els permisos solen baixar de les carpetes pare als fills.
3.  **Acumulació:** Els permisos d'usuari i de grup se sumen (excepte si hi ha una denegació).

3. Permisos Bàsics
| Permís | Descripció |
| :--- | :--- |
| **Llegir (R)** | Permet veure el contingut. |
| **Escriure (W)** | Permet fer canvis. |
| **Modificar (M)** | Inclou lectura, escriptura i eliminació. |
| **Control Total (F)** | Permet fer-ho tot, fins i tot canviar els permisos. |

4. Gestió per Terminal
Es pot utilitzar la comanda `icacls` per visualitzar i modificar aquestes llistes ràpidament.*

**Pas 24 i 25:** Crear la carpeta `Projectes`, desactivar l'herència de permisos i donar "Control total" al grup "Limitats".

Primer creo un grup que es dira limitats per alumne1 i 2

<img width="432" height="390" alt="image" src="https://github.com/user-attachments/assets/0b240287-cc34-4f30-a283-ea5bc6e185b4" />

Creem la carpeta

<img width="627" height="60" alt="image" src="https://github.com/user-attachments/assets/0cafc954-2132-4a4f-9d69-165b94b5f17c" />

Afegim el grup a la carpeta Projectes

<img width="362" height="277" alt="image" src="https://github.com/user-attachments/assets/d31346b2-7c48-4d13-8f6b-b88c86c939a1" />

Deshabilitem la herencia

<img width="769" height="173" alt="image" src="https://github.com/user-attachments/assets/f3ad621e-e2f6-4370-a461-b73ef60a2c4d" />

I donem control total al grup limitats

<img width="327" height="226" alt="image" src="https://github.com/user-attachments/assets/1cd0151d-8fb3-4d01-ac09-4922452de117" />



*  Aplicar una excepció per a `alumne2` mitjançant `icacls`, restringint el seu accés a "Només lectura" mentre la resta del grup manté el control total.

Affegim una exepcio al alumne2 per que nomes tingui permis de lectura

<img width="600" height="67" alt="image" src="https://github.com/user-attachments/assets/df74f372-89a0-4562-9962-4c717d05fecf" />

Provem de crear un fixer desde el usuari alumne2 com podem veure no ensdeixa

<img width="591" height="330" alt="image" src="https://github.com/user-attachments/assets/ffd8852b-c5f3-4e1c-a683-67bf2d7f6c47" />


* Consultar i verificar els permisos finals aplicats amb la comanda `icacls "E:\Projectes"`.
<img width="616" height="97" alt="image" src="https://github.com/user-attachments/assets/ea6e7727-4ceb-4e0e-a178-74bc4ac0cc12" />
