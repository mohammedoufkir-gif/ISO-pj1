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
* Creem la maquina mab 2GB de RAM, 1 nucli i 50GB de disk
  <img width="879" height="483" alt="Captura de pantalla de 2026-04-14 08-23-50" src="https://github.com/user-attachments/assets/30560936-3a7f-4e26-a72a-c68bfef6ba8f" />

* Carregem la imatge ISO de Windows 10.
  
  <img width="328" height="225" alt="Captura de pantalla de 2026-04-14 08-35-09" src="https://github.com/user-attachments/assets/385caa77-e766-4f7e-92f4-1f0a641d5b22" />

* Instal·lem el sistema operatiu
<img width="381" height="303" alt="Captura de pantalla de 2026-04-14 08-33-13" src="https://github.com/user-attachments/assets/7162f54d-76eb-4f01-9a78-23a27c898d86" />
<img width="381" height="303" alt="Captura de pantalla de 2026-04-14 08-33-56" src="https://github.com/user-attachments/assets/60e62e4e-1d38-4830-a1c6-7028ec741e82" />

## Fase 2 - Punts de restauració
* per a crear el punt de restauracio anem a "crear un punto de restauracion"
  <img width="802" height="683" alt="image" src="https://github.com/user-attachments/assets/b233cd64-53bc-4b9d-8946-2b2f6059ff36" />
* Una vegada dins activem la proteccio de sistem i dessignem quin persentatge del disk pot utilitzar per emmagatzema els punt de restauracio
  <img width="413" height="470" alt="image" src="https://github.com/user-attachments/assets/3d836df7-17b9-4ac4-bd32-196d8d942be3" />
* Ara anem a proteccio de sistema i fem clic a crar
<img width="413" height="470" alt="image" src="https://github.com/user-attachments/assets/5bd0b87a-3603-422a-9b0b-105909ebef48" />

Ara fiquem un nom al punt de restauracio
<img width="416" height="226" alt="image" src="https://github.com/user-attachments/assets/88156170-cb05-45af-a90b-94d226356549" />
<img width="361" height="131" alt="image" src="https://github.com/user-attachments/assets/5c8245b8-f98c-4863-9b64-00459639ac7b" />


* Ara fem un canvi en el SO en el meu cas e ficat un fons de pantalla

<img width="963" height="778" alt="image" src="https://github.com/user-attachments/assets/d67956a0-331a-454d-bf77-4add24572a22" />

Restaurem el SO 

<img width="429" height="513" alt="image" src="https://github.com/user-attachments/assets/44177cf2-d691-4d57-83e4-641feafe3f54" />

Elegim la nostre punt de restauracio

<img width="569" height="467" alt="image" src="https://github.com/user-attachments/assets/3f7731ba-cfb9-4122-8cc1-fe597586585d" />

Confirmem

<img width="569" height="467" alt="image" src="https://github.com/user-attachments/assets/6f155f5f-8634-4fd8-8459-41b5a7613c58" />

I el el sistem es reiniciara
<img width="531" height="468" alt="image" src="https://github.com/user-attachments/assets/ad550113-efe7-4a94-9215-a6c7496d9e7e" />

Uan vegada reinciat com podem veure que se ha restaurat el sistema operatiu, ja que no tenim el fons de panatalla de la pala.
<img width="955" height="874" alt="Captura de pantalla de 2026-04-17 09-11-18" src="https://github.com/user-attachments/assets/dc5dc755-40f6-4393-9add-5ef9536a642a" />



## Fase 3 - Llicències de Windows
* Anem a onfiguració → Sistema → Activació per veure si Windows està activat en el nostr eca no .
  <img width="804" height="650" alt="Captura de pantalla de 2026-04-17 09-13-13" src="https://github.com/user-attachments/assets/01c18255-f816-41e4-92d7-1a6cac497ead" />

* Executar al cmd la comanda `slmgr /xpr` per veure quin edicion de windows tenim.
  <img width="927" height="513" alt="Captura de pantalla de 2026-04-17 09-15-17" src="https://github.com/user-attachments/assets/4224870f-562b-438f-b2fd-a40184a514d0" />

* **Pas 14 i 15:** Esbrinar el llicenciament de Windows i consultar el preu aproximat d'una llicència en webs oficials.

## Fase 4 - Gestor d'arrencada
* **Pas 16 i 17:** Obrir Command Prompt com administrador i executar `bcdedit`.
<img width="788" height="502" alt="Captura de pantalla de 2026-04-17 09-17-29" src="https://github.com/user-attachments/assets/b5afb003-5888-47d8-a0ef-67b458695682" />

* **Pas 18 i 19:** Identificar els blocs (Boot Manager i Boot Loader) i interpretar dades com `default`, `timeout`, `device` i `path`.
* **Pas 20 i 21:** Respondre preguntes sobre el sistema d'arrencada i explicar la funció del Boot Manager i Boot Loader.

## Fase 5 - Xarxa bàsica
* Configuracio de xarxa
  <img width="732" height="381" alt="image" src="https://github.com/user-attachments/assets/cba316b6-b474-41c0-ac98-e18553728182" />
* comanda ifconfig per a vuere informarcio de xarxa

<img width="705" height="199" alt="image" src="https://github.com/user-attachments/assets/0b1819a1-33e1-42c6-8be3-54b0e8261d75" />


*  Configuracio DHCP    
  <img width="428" height="218" alt="image" src="https://github.com/user-attachments/assets/6fa6c3da-9c5f-41b2-971b-66d1f20e14b3" />
  
* Configuracio d'ip fixa

<img width="397" height="642" alt="image" src="https://github.com/user-attachments/assets/c58c45aa-216d-4bd2-b12f-44b27b553eb8" />


* **Pas 26:** Comprovar la connexió amb `ping google.com`.
<img width="668" height="246" alt="image" src="https://github.com/user-attachments/assets/eb794a24-3cde-4eca-a806-e279a419ed83" />

## Fase 6 - Comandes generals
* **Pas 27 i 28:** Obrir PowerShell i diferenciar-lo del cmd (bàsic vs potent/automatització).
  <img width="768" height="531" alt="image" src="https://github.com/user-attachments/assets/4d8ea62c-b499-4858-abb7-0c0fb40ef7df" />

* **Pas 29:** Provar comandes bàsiques de fitxers: `dir`, `cd`, `mkdir`, `echo` i `del`.
  <img width="709" height="320" alt="image" src="https://github.com/user-attachments/assets/574b8318-6546-4705-8ee2-bf783b9cc772" />
<img width="324" height="19" alt="image" src="https://github.com/user-attachments/assets/a6aa77d3-2c59-4fa7-8077-9ea56c66a9ce" />
<img width="427" height="150" alt="image" src="https://github.com/user-attachments/assets/3b78f554-95ff-441a-9df5-60a4016aeb4d" />
<img width="442" height="74" alt="image" src="https://github.com/user-attachments/assets/b56f31c6-f107-490c-9b8e-acae6ec3c26a" />
<img width="420" height="24" alt="image" src="https://github.com/user-attachments/assets/8c507c0d-74f1-4219-a399-936e31342a85" />

* **Pas 30 al 33:** Utilitzar comandes de sistema i xarxa com `tasklist`, `taskkill`, `systeminfo`, `hostname`, `whoami`, `netstat`, `tree`, `help` i `shutdown`.
* 
<img width="661" height="610" alt="image" src="https://github.com/user-attachments/assets/7d254556-2db9-48b1-a05d-df129f63fc27" />

<img width="862" height="680" alt="image" src="https://github.com/user-attachments/assets/b58d7173-35ba-4d31-b4de-2bcdbf49f7be" />

<img width="453" height="74" alt="image" src="https://github.com/user-attachments/assets/465c188b-3764-4fb9-9566-8757873c3298" />
<img width="826" height="576" alt="Captura de pantalla de 2026-04-17 22-18-56" src="https://github.com/user-attachments/assets/012fba7e-13de-4351-bb33-83b70a94648e" />
<img width="247" height="40" alt="Captura de pantalla de 2026-04-17 22-19-24" src="https://github.com/user-attachments/assets/5727b593-4496-494c-9959-be2831045a01" />

<img width="264" height="37" alt="Captura de pantalla de 2026-04-17 22-19-55" src="https://github.com/user-attachments/assets/b93771c2-8e19-482b-8444-119c41cf4609" />
<img width="727" height="473" alt="Captura de pantalla de 2026-04-17 22-20-17" src="https://github.com/user-attachments/assets/871e8e35-00e9-4fcb-a2fd-88f0c07f9f0e" />
<img width="727" height="473" alt="Captura de pantalla de 2026-04-17 22-20-31" src="https://github.com/user-attachments/assets/edc271c7-74bb-49ef-9694-e49f48ca5a28" />
<img width="727" height="473" alt="Captura de pantalla de 2026-04-17 22-24-32" src="https://github.com/user-attachments/assets/814da669-56cc-4004-a978-8a52999af2a5" />
<img width="311" height="42" alt="image" src="https://github.com/user-attachments/assets/3e3db94b-1cca-4395-b064-77685273396c" />

## Fase 7 - Instal·lació d'aplicacions
* **Pas 34 al 36:** Descarregar un programa des del navegador, instal·lar-lo i comprovar-ne el funcionament.
  <img width="396" height="140" alt="image" src="https://github.com/user-attachments/assets/10152caf-0d15-4969-b5c7-2c7de4805238" />
<img width="470" height="342" alt="image" src="https://github.com/user-attachments/assets/32428314-21f5-4ce9-980b-de2f96791694" />
<img width="918" height="697" alt="image" src="https://github.com/user-attachments/assets/ea6c614f-43e1-4266-9ba3-d07e35a24d93" />
<img width="1024" height="766" alt="image" src="https://github.com/user-attachments/assets/7da82c3c-f615-4d6d-9c83-83734d06d160" />


* **Pas 37 i 38:** Instal·lar una aplicació des de la Microsoft Store.
<img width="802" height="642" alt="image" src="https://github.com/user-attachments/assets/42b4d460-86bf-4924-a24a-17435ebcfeb0" />


* **Pas 39 i 40:** Desinstal·lar una aplicació des de la configuració i verificar que ja no apareix al sistema.
<img width="494" height="156" alt="image" src="https://github.com/user-attachments/assets/98fd7072-8c8f-4cc0-b142-456ce6c1aead" />
