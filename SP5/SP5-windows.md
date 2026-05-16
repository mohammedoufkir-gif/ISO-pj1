# Sprint 5: Monitoratge, Auditories i Programari Client/Servidor (10h)

## Guia de Configuració d'Autoritzacions i Auditories de Seguretat en Windows Server

### 1. Introducció i Fonaments del Sistema

Dins d'aquest bloc es detalla el procediment tècnic per al desplegament de controls d'accés i la gestió d'auditories de seguretat en entorns Windows Server. S'analitza comิ estructurar correctament el seguiment de les accions dels usuaris, la finalitat operativa d'aquests registres i la utilitat que ofereixen a l'hora de protegir la infraestructura de fitxers i detectar de manera preventiva comportaments anòmals o accessos no autoritzats.

Així mateix, es recullen un conjunt de validacions pràctiques mitjançant la generació programada d'esdeveniments d'accés (tant accions validades com requeriments denegats) i el seu posterior diagnòstic utilitzant les eines de monitorització integrades en el mateix sistema operatiu.

#### 1.1. Autorització en Sistemes Windows
L'autorització defineix el conjunt de regles mitjançant les quals el sistema operatiu gestiona i limita el ventall de privilegis que posseeix una entitat de seguretat (usuari o grup) sobre els recursos de l'equip. Aquesta infraestructura permet acoblar regles granulars per determinar qui disposa d'atribucions per a la lectura, escriptura, modificació o eliminació definitiva de directoris i fitxers. L'assignació d'aquests privilegis es realitza interactuant directament des de la pestanya de seguretat integrada a les propietats de l'element seleccionat.

D'altra banda, el sistema operatiu ofereix les anomenades "directives de seguretat". Aquestes regles corporatives automatitzen la implantació d'estàndards i polítiques de control d'accés, podent aplicar-se de manera local en un lúnic servidor o estendre's de manera massiva a tota una flota d'equips lligats a una topologia de domini corporatiu.

#### 1.2. El Rol de les Auditories de Seguretat
Les auditories de seguretat funcionen com una bitàcola automatitzada encarregada de registrar minuciosament qualsevol activitat rellevant dins d'un servidor Windows. El seu propòsit principal l'és la indexació exhaustiva de successos crítics, com ara intents d'autenticació de comptes, accessos directes a volums de dades o alteracions en les directives locals. Això esdevé indispensable per mantenir un històric de traçabilitat davant de qualsevol incidència de seguretat.

A través de la interpretació d'aquestes auditories és possible identificar anomalies operatives, intents repetits d'accés mitjançant credencials incorrectes o modificacions indegudes en arxius crítics, facilitant l'anàlisi de la salut global del sistema.

---

### 2. Metodologia de Configuració General

Per establir un entorn complet de monitorització en Windows Server s'ha de procedir de la següent manera:
1. **Configuració de les Polítiques del Sistema:** Execució de l'eina de gestió de polítiques de seguretat local (`secpol.msc`) per delimitar quins esdeveniments corporatius s'han d'indexar (inicis de sessió, accés a fitxers, creació de processos, etc.).
2. **Definició de l'Auditoria sobre Recursos:** Accés directe a les Propietats Avançades de la pestanya "Seguretat" de la carpeta o fitxer objectiu, on cal afegir de forma explícita quins usuaris i quines accions concretes (llegir, escriure, modificar) es volen auditar.
3. **Inspecció i Anàlisi de Registres:** Consulta i diagnòstic mitjançant el Visor d'Esdeveniments de Windows (`eventvwr.msc`), on cada tipus d'acció es classifica sota un identificador únic o *Event ID* (com l'ID 4624 per a accessos concedits o l'ID 4625 per a intents erronis).

*Nota tècnica: Es recomana aplicar un criteri selectiu a l'hora de definir què s'audita, ja que un registre massiu i innecessari d'esdeveniments podria penalitzar el rendiment del servidor.*

---

### 3. Desenvolupament de la Pràctica i Casos de Prova

#### Pas 1: Configuració de les Directives d'Auditoria Local
Per iniciar el procediment pràctic, accedim a l'eina de gestió de seguretat local executant el comando `secpol.msc`. Dins de l'arbre de navegació situat a la columna esquerra, ens desplacem per la següent ruta: **Configuració de seguretat** > **Directives locals** > **Directiva d'auditoria**. Un cop oberta aquesta secció, configurem les polítiques anomenades "Auditar eventos de inicio de sesión" i "Auditar el acceso a objetos" per tal d'activar el seu seguiment.


<img width="1120" height="436" alt="image" src="https://github.com/user-attachments/assets/7e622d63-2307-42d3-a33d-d394d837de58" />


Un cop aplicats els canvis, ambdues directives queden registrades correctament amb l'estat de control activat per a esdeveniments d'èxit i fallada (Correcto, Erróneo).

<img width="512" height="40" alt="image" src="https://github.com/user-attachments/assets/0cb403f0-d575-4535-8425-69dfaf123cd9" />

#### Pas 2: Validació d'Inicis de Sessió i Traçabilitat (Event ID 4624)
Per verificar que el sistema respon de forma adequada a la política que acabem d'activar, procedim a tancar la sessió del compte d'administrador i realitzem una nova autenticació. Posteriorment, obrim el Visor d'Esdeveniments (`eventvwr.msc`) per examinar els registres interns. Si el procés s'ha completat de manera satisfactòria, localitzarem un assentament lligat a l'identificador numèric **Event ID 4624**, el qual certifica l'obertura d'una sessió correcta.

<img width="742" height="499" alt="image" src="https://github.com/user-attachments/assets/d6193ec4-9538-46aa-b4e6-93140854400e" />

<img width="1219" height="606" alt="image" src="https://github.com/user-attachments/assets/1d3e4c32-7671-452b-a323-fd05d65be8e8" />



#### Pas 3: Creació d'un Recurs i Configuració de l'Auditoria d'Objectes
Creem un directori nou a l'arrel del disc local `C:` anomenat `ProvaAuditoria`. A continuació, configurem les condicions de monitorització accedint a les propietats de la carpeta i desplaçant-nos cap a la pestanya de "Seguridad". Dins d'aquest menú, fem clic a les opcions avançades per obrir el panell de gestió de controls i auditories.

<img width="1048" height="510" alt="image" src="https://github.com/user-attachments/assets/ea2b6a1b-ef80-422f-bafc-3a976327b33f" />


Premem el botó "Agregar" i definim la configuració de l'entrada d'auditoria: seleccionem l'usuari local de l'entorn (en aquest cas, l'usuari "moha"), establim el tipus com a "Correcto", comprovem que s'aplica a "Esta carpeta, subcarpetas y archivos" i marquem únicament els permisos bàsics de "Lectura y ejecución" i "Lectura".


<img width="774" height="529" alt="image" src="https://github.com/user-attachments/assets/7816906c-cb1e-43b7-a733-243c3272aeeb" />


<img width="915" height="591" alt="image" src="https://github.com/user-attachments/assets/eedb5049-d256-4314-8875-bf300277bba4" />


<img width="425" height="495" alt="image" src="https://github.com/user-attachments/assets/24bf93c3-74a9-4611-9b95-1bc9c680b2aa" />


#### Pas 4: Ampliació d'Entrades d'Auditoria (Perfil Administrador)
Per tal de disposar d'un ventall de proves més complet i comparar diferents perfils d'accés, tornem al panell de configuració avançada d'auditoria del directori i hi incorporem un segon registre de control enfocat, en aquest cas, a la compta de l'Administrador del sistema, assignant-li un perfil de "Control total" sobre la carpeta.

<img width="917" height="604" alt="image" src="https://github.com/user-attachments/assets/c2726161-696d-4016-835e-42da2f10b6d6" />


#### Pas 5: Validació d'Accés i Interacció amb Fitxers (Event ID 4662)
Per realitzar la prova de camp, accedim a l'interior del directori `C:\ProvaAuditoria` i generem activitat ordinària com un acarpeta prova. Tot seguit, tornem a la consola del Visor d'Esdeveniments de seguretat; si verifiquem els nous registres generats pel sistema operatiu, veurem reflectit l'**Event ID 4662**, codi de referència que confirma l'accés a un objecte de fitxers.


<img width="908" height="341" alt="image" src="https://github.com/user-attachments/assets/e9045070-33f8-40f6-aa1c-f93cfe65ff33" />


<img width="617" height="444" alt="image" src="https://github.com/user-attachments/assets/fee70613-ff66-4895-9ca0-a85fc09fcdbe" />

#### Pas 6: Monitorització de l'Inici de Processos (Event ID 4688)
Continuant amb el desenvolupament pràctic, ens desplacem de nou a la secció de directives locals de seguretat per habilitar la política corporativa anomenada "Auditar el seguimiento de procesos". L'objectiu d'aquesta acció és auditar l'arrencada d'aplicacions del sistema. Per comprovar que respon correctament, procedim a obrir el navegador d'internet Microsoft Edge. Aquesta acció genera de forma instantània el registre de l'**Event ID 4688**, associat a la creació de processos actius.


<img width="1183" height="549" alt="image" src="https://github.com/user-attachments/assets/03886e67-9bdc-4fcb-8d6b-0852e9fd9e7a" />

<img width="1329" height="636" alt="image" src="https://github.com/user-attachments/assets/ddae0af1-8875-473e-8311-2c41d93f57bc" />



<img width="814" height="491" alt="image" src="https://github.com/user-attachments/assets/6696391a-aa38-4b9e-8635-82c41077b221" />


#### Pas 7: Traçabilitat de la Finalització de Processos (Event ID 4689)
Com a contrapartida al pas anterior, realitzem ara el tancament complet del navegador que acabem d'obrir (ja sigui finalitzant l'aplicació de forma ordinària o forçant la seva detenció a través de l'Administrador de Tasques). Aquesta operació queda guardada automàticament al log de seguretat sota l'**Event ID 4689**, codi encarregat d'identificar que un procés en memòria s'ha donat per finalitzat.

<img width="762" height="451" alt="image" src="https://github.com/user-attachments/assets/9f7d436d-7b5d-42bc-954f-4d955aba13e2" />



#### Pas 8: Auditoria i Administració de Comptes d'Usuari (Event ID 4720 i 4722)
Per finalitzar el catàleg d'auditories pràctiques, ens dirigim a les directives del servidor per activar la política de seguretat "Auditar la administración de cuentas". Per validar aquest control, procedim a realitzar accions d'administració de comptes: accedim a la consola de gestió d'Usuaris i Equips d'Active Directory i donem d'alta un nou usuari dins del domini anomenat `prova`. Com a resposta directa, el sistema registrarà l'**Event ID 4720** (creació del compte d'usuari) seguit del registre **Event ID 4722** (habilitació i activació del compte creat).


<img width="1078" height="573" alt="image" src="https://github.com/user-attachments/assets/485d7931-c6a8-4d95-b8cf-d964075b925a" />

<img width="783" height="503" alt="image" src="https://github.com/user-attachments/assets/665aa19d-edf8-496f-982d-52e4e8a98802" />


<img width="783" height="503" alt="image" src="https://github.com/user-attachments/assets/e11ea201-14bb-4c50-8b45-3b8dad6e8401" />


<img width="1071" height="397" alt="image" src="https://github.com/user-attachments/assets/1d4aaf6f-c895-4328-b924-409b003b896b" />


<img width="730" height="421" alt="image" src="https://github.com/user-attachments/assets/b675f0a3-33d2-47ee-89b0-48263aec3cb0" />


#### Pas 9: Monitorització de la Desactivació d'Usuaris (Event ID 4725)
Si fem ús de les eines d'Active Directory sobre el perfil del nou usuari i passem a modificar el seu estat operatiu triant l'opció de "Deshabilitar cuenta", el visor de seguretat del sistema registrarà immediatament aquesta acció mitjançant l'**Event ID 4725**.

<img width="568" height="328" alt="image" src="https://github.com/user-attachments/assets/ae04c8b3-5437-4e4a-b292-907b57bcda22" />

<img width="634" height="470" alt="image" src="https://github.com/user-attachments/assets/a62ac114-3e20-40e8-a64b-f04eae53c155" />

#### Pas 10: Eliminació Definitiva del Compte (Event ID 4726)
Com a darrera acció per concloure el cicle pràctic de gestió i manteniment d'entitats de seguretat, si optem per esborrar de forma permanent el compte d'usuari `prova` del nostre llistat del directori actiu, la bitàcola de seguretat reflectirà aquesta operació final mitjançant el registre de l'**Event ID 4726**.

<img width="634" height="470" alt="image" src="https://github.com/user-attachments/assets/4d1e5d4a-4e54-46fa-b29f-06e0fc58c728" />

<img width="634" height="470" alt="image" src="https://github.com/user-attachments/assets/2c03a847-11b8-4d63-8ed1-8feb655fdf25" />

## Guia de Monitorització del Rendiment en Sistemes Windows Server

### 1. Introducció a la Supervisió de Recursos
La monitorització activa dels components de programari i de maquinari és un pilar fonamental per garantir la disponibilitat, estabilitat i eficiència operativa d'un servidor Windows. Mitjançant l'anàlisi de mètriques clau, els administradors de sistemes poden diagnosticar colls d'ampolla, anticipar anomalies i avaluar l'impacte en el rendiment provocat per l'execució d'aplicacions i serveis en segon pla.

A continuació, s'exposen els principals indicadors de rendiment dividits per branques de maquinari i es detalla el procediment per analitzar-los de manera pràctica a través de les eines natives del sistema operatiu.

---

### 2. Mètriques Fonamentals de Rendiment

#### 2.1. Unitat Central de Processament (CPU)
* **Elements Registrats:** Mostra el conjunt complet de processos en estat actiu juntament amb el percentatge específic de capacitat de procés que estan consumint a cada instant. Així mateix, llista els subprocesos, serveis vinculats i estadístiques de traçabilitat tals com el recompte de fils o l'identificador únic de procés o PID.
* **Interpretació de Dades:** El percentatge de CPU indica la fracció del processador assignada a una tasca. Si un servei manté de forma sostinguda valors superiors al 80-90%, s'ha de considerar com un indici de sobrecàrrega o d'una fallada en l'aplicació. El PID facilita la correlació del procés amb altres diagnòstics al Visor d'Esdeveniments o consoles PowerShell, mentre que el nom ajuda a diferenciar executables legítims d'anomalies del sistema.

#### 2.2. Memòria Volàtil (RAM)
* **Elements Registrats:** Indexa la quantitat de memòria física retinguda per cada procés executat. Detalla l'estat global de la RAM física (lliure, retinguda, en ús, en espera), a més del dimensionament de l'arxiu de paginació (*swap*) i les incidències d'accés a les adreces de memòria.
* **Interpretació de Dades:** La memòria en ús l'és la porció física ocupada de forma instantània per l'aplicació. La memòria en espera conté dades llistes per ser reaprofitades ràpidament per Windows si és necessari, i la disponible és la suma de la memòria lliure i la d'espera. Un ús intensiu de la memòria virtual (RAM combinada amb l'arxiu en disc) indica una mancança greu de memòria física instal·lada.

#### 2.3. Subsistema de Disc
* **Elements Registrats:** Identifica quins processos estan efectuant operacions d'entrada/sortida (lectura i escriptura) sobre les unitats d'emmagatzematge, el volum de dades transferit per segon, els temps de resposta, la latència de les operacions i les rutes específiques de fitxers en ús.
* **Interpretació de Dades:** La velocitat de lectura/escriptura (expressada en Bytes per segon) alerta sobre processos com una alta dependència de disc. Un temps de resposta que superi de manera contínua el llindar dels 20-30 ms denota problemes de rendiment de la unitat. Si la cua de disc és alta, el maquinari és incapaç d'atendre les peticions al mateix ritme que es generen, provocant la ralentització general del servidor.

#### 2.4. Interfície de Xarxa
* **Elements Registrats:** Traça les aplicacions que es troben transmetent o rebent trames de dades a través de les targetes de xarxa. Detalla els ports locals o remots de comunicació empleats, les adreces IP de destinació i el volum total de bytes transferits per segon tant en enviament com en recepció ($Tx$ i $Rx$).
* **Interpretació de Dades:** El percentatge d'utilització de la xarxa avalua l'estat d'ocupació de la línia respecte al seu ample de banda total. La llista de ports ajuda a diagnosticar quins serveis estan actius (p. ex., port 80 per a HTTP o 443 per a HTTPS), mentre que la identificació de les IP remotes i connexions actives resulta crucial per auditar possibles fluxos de dades sospitosos o cap a destinacions no desitjades.

---

### 3. Procediments Pràctics de Monitorització

#### Pas 1: Accés a l'Administrador de Tasques
Per fer una primera aproximació al consum de recursos en temps real, iniciem la utilitat nativa del sistema operatiu prement la combinació de tecles `Ctrl + Shift + Esc`. Dins d'aquest entorn, a la pestanya principal podrem consultar el desgast de recursos distribuït granularment per aplicacions, serveis o usuaris.

<img width="956" height="636" alt="image" src="https://github.com/user-attachments/assets/1c0008c0-d685-487f-bd75-818c6c63cf74" />

#### Pas 2: Monitorització de la Gràfica de Rendiment de CPU i Memòria
Per disposar d'una perspectiva històrica de l'ús de la infraestructura, ens desplacem cap a la pestanya "Rendimiento" de la mateixa eina. Des d'aquest panell podem analitzar el comportament tant de la CPU com de la memòria d'una manera gràfica.

<img width="956" height="636" alt="image" src="https://github.com/user-attachments/assets/bc87c7be-d63b-4da7-a023-f5b88411fc5f" />

<img width="956" height="636" alt="image" src="https://github.com/user-attachments/assets/45cd2924-c524-4bcc-a14f-32ff170d75a3" />

<img width="956" height="636" alt="image" src="https://github.com/user-attachments/assets/93513f2b-d77b-4445-8320-d22ebc773ba5" />

<img width="956" height="636" alt="image" src="https://github.com/user-attachments/assets/7fd15606-e776-468e-a20e-feba493eda92" />

<img width="956" height="636" alt="image" src="https://github.com/user-attachments/assets/8c17e37a-467c-454a-8cf3-ddff23549304" />




#### Pas 3: Diagnòstic Detallat com el Monitor de Recursos
Quan es requereix una anàlisi molt més exhaustiva i minuciosa que superi el nivell de detall aportat per l'Administrador de Tasques, passem a utilitzar l'eina "Monitor de recursos". Aquesta utilitat s'organitza mitjançant pestanyes dedicades exclusivament a cadascun dels elements de maquinari analitzats anteriorment.

<img width="792" height="604" alt="image" src="https://github.com/user-attachments/assets/beff16cc-7152-43c1-b275-3fa8a8c4eb8d" />

<img width="792" height="604" alt="image" src="https://github.com/user-attachments/assets/98649c2e-069d-4e76-ba83-6fae3fc70798" />

<img width="792" height="604" alt="image" src="https://github.com/user-attachments/assets/95ffc0b7-3c2d-4174-b655-76c32c35a31d" />

<img width="792" height="604" alt="image" src="https://github.com/user-attachments/assets/54bad642-c4ad-4d3e-a63e-e9c2340ca34f" />

<img width="792" height="604" alt="image" src="https://github.com/user-attachments/assets/67b7aaca-872f-4773-8d2c-9310ae3e6dba" />







