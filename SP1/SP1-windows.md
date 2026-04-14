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
  <img width="879" height="483" alt="Captura de pantalla de 2026-04-14 08-23-50" src="https://github.com/user-attachments/assets/30560936-3a7f-4e26-a72a-c68bfef6ba8f" />

* **Pas 4:** Carregar la imatge ISO de Windows 10 o Windows 11.
  
  <img width="328" height="225" alt="Captura de pantalla de 2026-04-14 08-35-09" src="https://github.com/user-attachments/assets/385caa77-e766-4f7e-92f4-1f0a641d5b22" />

* **Pas 5:** Instal·lar el sistema (idioma, usuari, contrasenya) i comprovar que arrenca correctament.
* 
<img width="381" height="303" alt="Captura de pantalla de 2026-04-14 08-33-13" src="https://github.com/user-attachments/assets/7162f54d-76eb-4f01-9a78-23a27c898d86" />

<img width="381" height="303" alt="Captura de pantalla de 2026-04-14 08-33-56" src="https://github.com/user-attachments/assets/60e62e4e-1d38-4830-a1c6-7028ec741e82" />

## Fase 2 - Punts de restauració
* **Pas 6 al 8:** Cercar "Crear un punt de restauració", activar la protecció al disc C: i crear un punt manual.
  <img width="802" height="683" alt="image" src="https://github.com/user-attachments/assets/b233cd64-53bc-4b9d-8946-2b2f6059ff36" />
  <img width="413" height="470" alt="image" src="https://github.com/user-attachments/assets/3d836df7-17b9-4ac4-bd32-196d8d942be3" />
<img width="413" height="470" alt="image" src="https://github.com/user-attachments/assets/5bd0b87a-3603-422a-9b0b-105909ebef48" />
<img width="416" height="226" alt="image" src="https://github.com/user-attachments/assets/88156170-cb05-45af-a90b-94d226356549" />
<img width="302" height="100" alt="image" src="https://github.com/user-attachments/assets/17a509ca-a2c0-467e-9fb9-bde068f921e6" />
<img width="361" height="131" alt="image" src="https://github.com/user-attachments/assets/5c8245b8-f98c-4863-9b64-00459639ac7b" />


* **Pas 9 i 10:** Fer un canvi (instal·lar app o configuració), restaurar i comprovar resultats.
  fem un canvi
<img width="963" height="778" alt="image" src="https://github.com/user-attachments/assets/d67956a0-331a-454d-bf77-4add24572a22" />

<img width="429" height="513" alt="image" src="https://github.com/user-attachments/assets/44177cf2-d691-4d57-83e4-641feafe3f54" />

<img width="569" height="467" alt="image" src="https://github.com/user-attachments/assets/3f7731ba-cfb9-4122-8cc1-fe597586585d" />

<img width="569" height="467" alt="image" src="https://github.com/user-attachments/assets/6f155f5f-8634-4fd8-8459-41b5a7613c58" />

<img width="295" height="100" alt="image" src="https://github.com/user-attachments/assets/d5ccb817-e725-4d4e-b49f-8b072590b2a6" />

<img width="531" height="468" alt="image" src="https://github.com/user-attachments/assets/ad550113-efe7-4a94-9215-a6c7496d9e7e" />


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
