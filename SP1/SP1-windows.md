# [cite_start]GUIA PRÀCTICA: Instal·lació i configuració de Windows [cite: 3, 4]

## Índex
1. [Fase 1: Instal·lació del sistema operatiu](#fase-1-installació-del-sistema-operatiu)
2. [Fase 2: Punts de restauració](#fase-2-punts-de-restauració)
3. [Fase 3: Llicències de Windows](#fase-3-llicències-de-windows)
4. [Fase 4: Gestor d'arrencada](#fase-4-gestor-darrencada)
5. [Fase 5: Xarxa bàsica](#fase-5-xarxa-bàsica)
6. [Fase 6: Comandes generals](#fase-6-comandes-generals)
7. [Fase 7: Instal·lació d'aplicacions](#fase-7-installació-daplicacions)

---

## [cite_start]Fase 1 - Instal·lació del sistema operatiu [cite: 5]
* [cite_start]**Crear màquina virtual** amb VirtualBox[cite: 6].
* [cite_start]**Assignar recursos:** Memòria RAM mínima de 4 GB i disc de 40 GB[cite: 7].
* [cite_start]**Carregar ISO** de Windows 10 o Windows 11[cite: 7].
* [cite_start]**Instal·lar el sistema:** Configuració d'idioma, usuari i contrasenya[cite: 13].

## [cite_start]Fase 2 - Punts de restauració [cite: 14]
* [cite_start]**Activació:** Cercar "Crear un punt de restauració" i activar la protecció al disc C:[cite: 15].
* [cite_start]**Gestió:** Crear un punt manual, realitzar un canvi (instal·lar app) i restaurar per comprovar[cite: 15, 16].

## [cite_start]Fase 3 - Llicències de Windows [cite: 17]
* [cite_start]**Verificació:** Consultar l'estat des de Sistema → Activació i executar `slmgr /xpr` al cmd[cite: 18, 19, 21].
* [cite_start]**Investigació:** Explicar el llicenciament i consultar preus en webs oficials[cite: 22, 23].

## [cite_start]Fase 4 - Gestor d'arrencada [cite: 24]
* [cite_start]**Anàlisi tècnica:** Obrir Command Prompt com a administrador i executar `bcdedit`[cite: 25].
* [cite_start]**Identificació:** Diferenciar entre el **Boot Manager** (qui decideix l'arrencada) i el **Boot Loader** (qui carrega el sistema)[cite: 25, 42].
* [cite_start]**Dades clau:** Identificar el `default`, el `timeout` i la ruta del fitxer `winload.efi`[cite: 32, 33, 36].

## [cite_start]Fase 5 - Xarxa bàsica [cite: 45]
* [cite_start]**Consulta:** Obrir configuració i utilitzar `ipconfig`[cite: 46, 47].
* [cite_start]**Configuració:** Alternar entre IP dinàmica (DHCP) i IP fixa (manual)[cite: 48, 49].
* [cite_start]**Comprovació:** Validar la connexió amb `ping google.com`[cite: 50].

## [cite_start]Fase 6 - Comandes generals [cite: 51]
* [cite_start]**Eines:** Diferenciar entre **cmd** (bàsic) i **PowerShell** (més potent, objectes i automatització)[cite: 53, 54, 55].
* [cite_start]**Comandes de fitxers:** Ús de `dir`, `cd`, `mkdir`, `echo` i `del`[cite: 58, 60, 61, 62, 63].
* [cite_start]**Gestió del sistema:** `tasklist` (processos), `systeminfo` (informació sistema), `hostname` i `whoami`[cite: 65, 71, 72, 73].
* [cite_start]**Xarxa i utilitats:** `netstat -an` (connexions), `tree` (estructura), `help` i `shutdown`[cite: 77, 80, 82, 84].

## [cite_start]Fase 7 - Instal·lació d'aplicacions [cite: 90]
* [cite_start]**Descàrrega:** Obtenir programes via navegador o des de la Microsoft Store[cite: 91, 94].
* [cite_start]**Manteniment:** Instal·lar mitjançant l'assistent i realitzar la desinstal·lació des de Configuració → Aplicacions[cite: 92, 96].
