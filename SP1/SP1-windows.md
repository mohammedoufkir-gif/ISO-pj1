# GUIA PRÀCTICA: Instal·lació i configuració de Windows

## Índex
1. [Fase 1: Instal·lació del sistema operatiu](#fase-1-installació-del-sistema-operatiu)
2. [Fase 2: Punts de restauració](#fase-2-punts-de-restauració)
3. [Fase 3: Llicències de Windows](#fase-3-llicències-de-windows)
4. [Fase 4: Gestor d'arrencada](#fase-4-gestor-darrencada)
5. [Fase 5: Xarxa bàsica](#fase-5-xarxa-bàsica)
6. [Fase 6: Comandes generals](#fase-6-comandes-generals)
7. [Fase 7: Instal·lació d'aplicacions](#fase-7-installació-daplicacions)

---

## Fase 1 - Instal·lació del sistema operatiu
* **Pas 1 al 3:** Crear màquina virtual amb VirtualBox assignant recursos (RAM mínim 4 GB, disc mínim 40 GB).
* **Pas 4:** Carregar la imatge ISO de Windows 10 o Windows 11.
* **Pas 5:** Instal·lar el sistema (idioma, usuari, contrasenya) i comprovar que arrenca correctament.

## Fase 2 - Punts de restauració
* **Pas 6 al 8:** Cercar "Crear un punt de restauració", activar la protecció al disc C: i crear un punt manual.
* **Pas 9 i 10:** Fer un canvi (instal·lar app o configuració), restaurar i comprovar resultats.

## Fase 3 - Llicències de Windows
* **Pas 11 i 12:** Obrir Configuració → Sistema → Activació per veure si Windows està activat.
* **Pas 13:** Executar al cmd la comanda `slmgr /xpr`.
* **Pas 14 i 15:** Esbrinar el llicenciament de Windows i consultar el preu aproximat d'una llicència en webs oficials.

## Fase 4 - Gestor d'arrencada
* **Pas 16 i 17:** Obrir Command Prompt com administrador i executar `bcdedit`.
* **Pas 18 i 19:** Identificar els blocs (Boot Manager i Boot Loader) i interpretar dades com `default`, `timeout`, `device` i `path`.
* **Pas 20 i 21:** Respondre preguntes sobre el sistema d'arrencada i explicar la funció del Boot Manager i Boot Loader.

## Fase 5 - Xarxa bàsica
* **Pas 22 i 23:** Obrir configuració de xarxa i consultar la IP amb la comanda `ipconfig`.
* **Pas 24 i 25:** Configurar la IP dinàmica (DHCP) i la IP fixa (manual: IP, màscara, gateway, DNS).
* **Pas 26:** Comprovar la connexió amb `ping google.com`.

## Fase 6 - Comandes generals
* **Pas 27 i 28:** Obrir PowerShell i diferenciar-lo del cmd (bàsic vs potent/automatització).
* **Pas 29:** Provar comandes bàsiques de fitxers: `dir`, `cd`, `mkdir`, `echo` i `del`.
* **Pas 30 al 33:** Utilitzar comandes de sistema i xarxa com `tasklist`, `taskkill`, `systeminfo`, `hostname`, `whoami`, `netstat`, `tree`, `help` i `shutdown`.

## Fase 7 - Instal·lació d'aplicacions
* **Pas 34 al 36:** Descarregar un programa des del navegador (Chrome o VS Code), instal·lar-lo i comprovar-ne el funcionament.
* **Pas 37 i 38:** Instal·lar una aplicació des de la Microsoft Store.
* **Pas 39 i 40:** Desinstal·lar una aplicació des de la configuració i verificar que ja no apareix al sistema.
