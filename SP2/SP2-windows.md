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
* **Pas 1 i 2:** Afegir un nou disc virtual a la màquina virtual i iniciar Windows per obrir la "Gestió de discs".
<img width="742" height="450" alt="image" src="https://github.com/user-attachments/assets/5e1d2f73-8eb3-41a3-9121-57265d613fa1" />
  
* **Pas 3:** Inicialitzar el disc i crear dues particions: una NTFS anomenada "Dades" i una FAT32 anomenada "Portable".
  <img width="499" height="394" alt="image" src="https://github.com/user-attachments/assets/069e517f-08a8-4ef9-8b64-e23613c36cff" />
<img width="499" height="394" alt="image" src="https://github.com/user-attachments/assets/a7aa07a4-b0ed-4ac3-9fb2-ea162e0edaca" />
<img width="762" height="106" alt="image" src="https://github.com/user-attachments/assets/d1209893-3525-4995-906b-d3296025d370" />



* **Pas 4:** Assignar lletres d'unitat i comprovar la configuració final mitjançant la comanda `diskpart`.
<img width="489" height="342" alt="image" src="https://github.com/user-attachments/assets/356f4c00-5b5f-4476-81b2-ff572a34ec64" />
<img width="581" height="162" alt="image" src="https://github.com/user-attachments/assets/db0f33f7-f651-45ac-9c9d-5d8f1537d461" />
<img width="388" height="273" alt="image" src="https://github.com/user-attachments/assets/89526098-e86a-44cd-a7a0-a93603b4dd98" />

## Fase 2 - Quotes i usuaris
* **Pas 5 i 6:** Activar les quotes de disc a la partició Dades, establint un límit de 300 MB per usuari amb notificació d'advertència.
* **Pas 7 i 8:** Crear els usuaris locals `alumne1` i `alumne2` i afegir-los al nou grup "Limitats".
* **Pas 9:** Provar la còpia de fitxers fins a superar el límit per verificar que la quota bloqueja l'escriptura.

## Fase 3 - Script de còpia i automatització
* **Pas 10 i 11:** Afegir un tercer disc virtual (Backups) en format NTFS i crear la carpeta `CòpiesUsuaris`.
* **Pas 12:** Crear un fitxer `script.bat` que copiï el contingut de la carpeta de l'usuari actual cap a la unitat de Backups.
* **Pas 13 i 14:** Utilitzar `gpedit.msc` per configurar l'script perquè s'executi automàticament en l'inici de sessió.

## Fase 4 - Verificació i documentació
* **Pas 15:** Iniciar sessió amb els usuaris creats per comprovar que l'automatització funciona i que les restriccions d'espai s'apliquen correctament.

## Fase 5 - Gestió de processos i serveis
* **Pas 19:** Llistar i exportar els processos actius a un fitxer de text mitjançant `tasklist > procesos_inici.txt`.
* **Pas 20 i 21:** Identificar processos no essencials (OneDrive, Teams, Skype) i eliminar-los manualment amb la comanda `taskkill /IM [nom] /F`.
* **Pas 22 i 23:** Automatitzar el tancament d'aquests processos a l'script d'inici i documentar la millora de rendiment a la màquina virtual.

## Fase 6 - Gestió de permisos (ACLs)
* **Teoria:** Comprendre el funcionament de les ACL (Access Control List) i les ACE (entrades de control d'accés) per a permisos detallats.
* **Pas 24 i 25:** Crear la carpeta `Projectes`, desactivar l'herència de permisos i donar "Control total" al grup "Limitats".
* **Pas 26 al 28:** Aplicar una excepció per a `alumne2` mitjançant `icacls`, restringint el seu accés a "Només lectura" mentre la resta del grup manté el control total.
* **Pas 29:** Consultar i verificar els permisos finals aplicats amb la comanda `icacls "D:\Projectes"`.
