# Planificación de Sprint 2: Configuración Avanzada de Windows

## Índex
1. [Fase 1: Preparació del sistema](#fase-1---preparació-del-sistema)
2. [Fase 2: Quotes i usuaris](#fase-2---quotes-i-usuaris)
3. [Fase 3: Script de còpia i automatització](#fase-3---script-de-còpia-i-automatització)
4. [Fase 4: Verificació i documentació](#fase-4---verificació-i-documentació)
5. [Fase 5: Gestió de processos i serveis](#fase-5---gestió-de-processos-i-serveis)
6. [Fase 6: Gestió de permisos (ACLs)](#fase-6---gestió-de-permisos-acls)

---

## Fase 1 - Preparació del sistema
* [cite_start]**Configuració de discs:** Afegir un nou disc virtual, inicialitzar-lo i crear les particions "Dades" (NTFS) i "Portable" (FAT32)[cite: 101, 102, 103].
* [cite_start]**Verificació:** Assignar lletres d'unitat i comprovar la configuració mitjançant l'eina `diskpart`[cite: 104].

## Fase 2 - Quotes i usuaris
* [cite_start]**Control de l'espai:** Activar les quotes de disc a la partició Dades amb un límit de 300 MB per usuari i avisos de notificació[cite: 106, 107].
* [cite_start]**Gestió d'usuaris:** Creació dels usuaris locals `alumne1` i `alumne2` i la seva assignació al grup "Limitats"[cite: 108, 109].
* [cite_start]**Proves de quota:** Verificació del bloqueig d'escriptura en superar el límit de dades[cite: 110].

## Fase 3 - Script de còpia i automatització
* [cite_start]**Unitat de Backup:** Configuració d'un tercer disc en NTFS anomenat "Backups" amb la carpeta `CòpiesUsuaris`[cite: 112, 113].
* [cite_start]**Desenvolupament d'Scripts:** Creació d'un fitxer `.bat` per copiar el perfil de l'usuari a la unitat de seguretat[cite: 114, 115].
* [cite_start]**Automatització:** Ús de `gpedit.msc` per assignar l'script a l'inici de sessió dels alumnes[cite: 116, 117].

## Fase 4 - Verificació i documentació
* [cite_start]**Comprovació final:** Validació que l'script realitza la còpia correctament i que les quotes bloquegen l'accés quan toca[cite: 119].

## Fase 5 - Gestió de processos i serveis
* [cite_start]**Monitorització:** Llistat de processos actius (`tasklist`) i exportació a un fitxer de text[cite: 121, 124, 125].
* [cite_start]**Optimització:** Identificació i eliminació manual de processos prescindibles com `OneDrive.exe` o `Teams.exe`[cite: 128, 130, 137].
* [cite_start]**Millora del rendiment:** Automatització del tancament de processos no essencials a l'inici de sessió per estalviar recursos[cite: 139, 140, 144].

## Fase 6 - Gestió de permisos (ACLs)
* [cite_start]**Conceptes:** Introducció a les llistes de control d'accés (ACL) i les entrades de control d'accés (ACE)[cite: 146, 147, 149].
* [cite_start]**Configuració de permisos:** Creació de la carpeta `Projectes`, desactivació de l'herència i assignació de control total al grup "Limitats"[cite: 159, 162, 164].
* [cite_start]**Excepcions detallades:** Ús de la comanda `icacls` per restringir a `alumne2` a només lectura, mantenint el control total per a la resta del grup[cite: 171, 172, 177].
