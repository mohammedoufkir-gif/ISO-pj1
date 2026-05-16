
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




Un cop aplicats els canvis, ambdues directives queden registrades correctament amb l'estat de control activat per a esdeveniments d'èxit i fallada (Correcto, Erróneo).

#### Pas 2: Validació d'Inicis de Sessió i Traçabilitat (Event ID 4624)
Per verificar que el sistema respon de forma adequada a la política que acabem d'activar, procedim a tancar la sessió del compte d'administrador i realitzem una nova autenticació utilitzant les credencials d'un usuari de proves. Posteriorment, obrim el Visor d'Esdeveniments (`eventvwr.msc`) per examinar els registres interns. Si el procés s'ha completat de manera satisfactòria, localitzarem un assentament lligat a l'identificador numèric **Event ID 4624**, el qual certifica l'obertura d'una sessió correcta.

> 📷 **[MISSATGE DE CAPTURA - VISOR D'ESDEVENIMENTS - EVENT ID 4624 DE LOGON]**
> *La imatge mostra dues captures combinades del Visor d'Esdeveniments (`eventvwr.msc`). La primera part presenta el llistat general d'esdeveniments dins de la bitàcola de "Seguridad". S'hi pot observar una graella amb columnes que detallen les "Palabras clave", "Fecha y hora", "Origen" (Microsoft Windows security auditing), "Id. del evento" i "Categoría de la tarea". Es troba seleccionada una fila amb l'ID 4624 assignada a la categoria de tasca "Logon". La segona part de la captura mostra el panell de detalls inferiors en la seva pestanya "General", on es llegeix textualment el text descriptiu del sistema: "Se inició sesión correctamente en una cuenta.", seguit de les dades del subjecte amb l'ID de seguretat "NULL SID" i el nom de l'equip local del domini "MARIA\MARIA.local".*

#### Pas 3: Creació d'un Recurs i Configuració de l'Auditoria d'Objectes
Creem un directori nou a l'arrel del disc local `C:` anomenat `ProvaAuditoria`. A continuació, configurem les condicions de monitorització accedint a les propietats de la carpeta i desplaçant-nos cap a la pestanya de "Seguridad". Dins d'aquest menú, fem clic a les opcions avançades per obrir el panell de gestió de controls i auditories.

> 📷 **[MISSATGE DE CAPTURA - OPCIONS AVANÇADES DE LA CARPETA PROVAAUDITORIA]**
> *Es visualitzen dues pantalles superposades relacionades amb els paràmetres de la carpeta `ProvaAuditoria`. La finestra superior correspon a les propietats bàsiques de Seguretat de Windows, on es detallen els "Nombres de grupos o usuarios" (CREATOR OWNER, SYSTEM, Administradores, Usuarios) i els seus respectius permisos. El cursor es troba fent clic sobre el botó de la part inferior anomenat "Opciones avanzadas". La finestra inferior mostra la "Configuración de seguridad avanzada para ProvaAuditoria" posicionada sobre la pestanya "Auditoría". Aquest panell es troba completament buit de línies de control, mostrant a la part inferior esquerra el botó "Agregar" preparat per definir una nova directiva.*

Premem el botó "Agregar" i definim la configuració de l'entrada d'auditoria: seleccionem l'usuari local de l'entorn (en aquest cas, l'usuari "Maria"), establim el tipus com a "Correcto", comprovem que s'aplica a "Esta carpeta, subcarpetas y archivos" i marquem únicament els permisos bàsics de "Lectura y ejecución" i "Lectura".

#### Pas 4: Ampliació d'Entrades d'Auditoria (Perfil Administrador)
Per tal de disposar d'un ventall de proves més complet i comparar diferents perfils d'accés, tornem al panell de configuració avançada d'auditoria del directori i hi incorporem un segon registre de control enfocat, en aquest cas, a la compta de l'Administrador del sistema, assignant-li un perfil de "Control total" sobre la carpeta.

> 📷 **[MISSATGE DE CAPTURA - LLISTA D'ENTRADES D'AUDITORIA ACTIVES]**
> *La captura mostra la finestra de "Configuración de seguridad avanzada para ProvaAuditoria" amb la pestanya d'Auditoría activa. En la graella central d'entrades d'auditoria es detallen de manera clara dues regles en funcionament: la primera fila identifica un tipus d'auditoria "Correcto" per a l'entitat de seguretat "Maria MGA. Gutierrez Amposta" amb un accés de "Lectura y ejecución"; la segona fila recull un tipus "Correcto" enfocat a l'entitat de seguretat "Administrador" amb privilegis de "Control total". Per a ambdues regles s'especifica que l'origen d'herència és "Ninguno" i que la seva aplicació afecta a "Esta carpeta, subcarpetas y archivos".*

#### Pas 5: Validació d'Accés i Interacció amb Fitxers (Event ID 4663)
Per realitzar la prova de camp, accedim a l'interior del directori `C:\ProvaAuditoria` i generem activitat ordinària (com la creació de noves carpetes o arxius buits anomenats "hola" i "adeu", o l'obertura dels documents existents). Tot seguit, tornem a la consola del Visor d'Esdeveniments de seguretat; si verifiquem els nous registres generats pel sistema operatiu, veurem reflectit l'**Event ID 4663**, codi de referència que confirma l'accés a un objecte de fitxers.

> 📷 **[MISSATGE DE CAPTURA - GENERACIÓ D'ACTIVITAT I REGISTRE D'OBJECTES ID 4663]**
> *La imatge es compon de dues interfícies del sistema operatiu Windows Server. A la part superior, es veu la finestra de l'Explorador de Fitxers oberta a la ruta `Este equipo > Disco local (C:) > ProvaAuditoria`, llistant el contingut de la carpeta amb dos elements de tipus text anomenats "adeu" i "hola" amb les seves respectives dates de modificació. A la part inferior es mostra la consola del Visor d'Esdeveniments, on a la llista superior es troba marcat l'ID 4663 de la categoria "File System". El panell inferior "General" d'aquest esdeveniment detalla de forma explícita que el tipus d'objecte afectat és un "File" i que el paràmetre "Nombre del objeto" apunta directament a la ubicació física del recurs compromès: `C:\ProvaAuditoria`.*

#### Pas 6: Monitorització de l'Inici de Processos (Event ID 4688)
Continuant amb el desenvolupament pràctic, ens desplacem de nou a la secció de directives locals de seguretat per habilitar la política corporativa anomenada "Auditar el seguimiento de procesos". L'objectiu d'aquesta acció és auditar l'arrencada d'aplicacions del sistema. Per comprovar que respon correctament, procedim a obrir el navegador d'internet Microsoft Edge. Aquesta acció genera de forma instantània el registre de l'**Event ID 4688**, associat a la creació de processos actius.

> 📷 **[MISSATGE DE CAPTURA - DIRECTIVA DE PROCESSOS I EVENT ID 4688 INICIAL]**
> *S'aprecien diverses captures que documenten el procés complet. Primer, la finestra de Directives de Seguretat Local mostrant l'activació com a "Correcto, Erróneo" de la línia "Auditar el seguimiento de procesos". Després, es visualitza l'obertura de l'aplicació Microsoft Edge mostrant una finestra en blanc on es demana importar els favorits de l'usuari. Finalment, acoblat al conjunt, es mostra el Visor d'Esdeveniments seleccionant el registre d'auditoria correcta de tipus "Process Creation" amb l'ID d'esdeveniment 4688. El seu quadre de text descriptiu general identifica la compta d'origen de l'acció i el camp "Nombre del nuevo proceso", el qual apunta cap a l'executable del navegador a la ruta: `C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe`.*

#### Pas 7: Traçabilitat de la Finalització de Processos (Event ID 4689)
Com a contrapartida al pas anterior, realitzem ara el tancament complet del navegador que acabem d'obrir (ja sigui finalitzant l'aplicació de forma ordinària o forçant la seva detenció a través de l'Administrador de Tasques). Aquesta operació queda guardada automàticament al log de seguretat sota l'**Event ID 4689**, codi encarregat d'identificar que un procés en memòria s'ha donat per finalitzat.

> 📷 **[MISSATGE DE CAPTURA - VISOR D'ESDEVENIMENTS - EVENT ID 4689 DE FINALITZACIÓ]**
> *La captura mostra la finestra del Visor d'Esdeveniments posicionada sobre la llista de logs de seguretat del servidor. S'ha seleccionat una línia d'auditoria correcta corresponent a l'ID de succés 4689 lligat a la categoria "Process Termination". El panell inferior llegeix en el seu apartat de resum textual la descripció del sistema operatiu: "Se salió de un proceso.", lligat de forma directa al tancament de l'executable de l'aplicació del navegador d'internet fet servir en el test anterior.*

#### Pas 8: Auditoria i Administració de Comptes d'Usuari (Event ID 4720 i 4722)
Per finalitzar el catàleg d'auditories pràctiques, ens dirigim a les directives del servidor per activar la política de seguretat "Auditar la administración de cuentas". Per validar aquest control, procedim a realitzar accions d'administració de comptes: accedim a la consola de gestió d'Usuaris i Equips d'Active Directory i donem d'alta un nou usuari dins del domini anomenat `prova`. Com a resposta directa, el sistema registrarà l'**Event ID 4720** (creació del compte d'usuari) seguit del registre **Event ID 4722** (habilitació i activació del compte creat).

> 📷 **[MISSATGE DE CAPTURA - CONTROL DE COMPTES EN ACTIVE DIRECTORY I EVENTS ID 4720 / 4722]**
> *La pantalla es divideix en tres interfícies operatives de Windows Server. Al fons a l'esquerra, es mostra l'assistent de creació de perfils d'Active Directory "Nuevo objeto: Usuario" on s'ha definit el nom d'usuari "prova" i es troba activat el xec de "La contraseña nunca expira". A la dreta es veu l'arbre d'unitats organitzatives destacant l'usuari "prova" ja llistat a la carpeta "Informatica". A la part inferior es troba el Visor d'Esdeveniments llistant consecutivament els dos logs generats per aquesta acció d'administració: l'ID d'esdeveniment 4720, on el quadre de text de detall indica expressament "Se creó una cuenta de usuario.", i l'ID d'esdeveniment 4722 de la mateixa categoria "User Account Management" que recull la frase "Se habilitó una cuenta de usuario.".*

#### Pas 9: Monitorització de la Desactivació d'Usuaris (Event ID 4725)
Si fem ús de les eines d'Active Directory sobre el perfil del nou usuari i passem a modificar el seu estat operatiu triant l'opció de "Deshabilitar cuenta", el visor de seguretat del sistema registrarà immediatament aquesta acció mitjançant l'**Event ID 4725**.

> 📷 **[MISSATGE DE CAPTURA - NOTIFICACIÓ DE DESACTIVACIÓ DE COMPTE I EVENT ID 4725]**
> *Es visualitza en primer pla una petita finestra de diàleg de confirmació del sistema anomenada "Servicios de dominio de Active Directory" amb el text informatiu "El objeto prova ha sido deshabilitado." acompanyat d'un botó d'Aceptar. Al darrere d'aquesta finestra, es mostra el Visor d'Esdeveniments on apareix fixat un registre d'auditoria correcta de gestió de comptes marcat amb l'ID de succés 4725, el desglossament del qual a la pestanya General recull formalment la línia: "Se deshabilitó una cuenta de usuario.", lligant l'acció a la "Cuenta de destino: MARIA0\prova".*

#### Pas 10: Eliminació Definitiva del Compte (Event ID 4726)
Com a darrera acció per concloure el cicle pràctic de gestió i manteniment d'entitats de seguretat, si optem per esborrar de forma permanent el compte d'usuari `prova` del nostre llistat del directori actiu, la bitàcola de seguretat reflectirà aquesta operació final mitjançant el registre de l'**Event ID 4726**.

---

### 4. Referències i Recursos de Consulta

* **Materials del Curs:** Informació extreta de la plataforma Moodle de la assignatura *0369 - Implantació de Sistemes Operatius*.
* **Recursos Audiovisuals Externs:**
    * Vídeo didàctic de YouTube: *Cómo configurar auditorías en Windows Server*.
    * Vídeo de suport tècnic de YouTube: *Auditorías en Windows Server 2019*.
* **Documentació Tècnica de Microsoft:**
    * Guia oficial sobre desplegament de polítiques de seguretat i auditories centralitzades a Windows Server.
* **Blogs de Seguretat Informàtica:**
    * Micromouse: *Política de auditoría en Windows*.
    * Blog de la Universitat de Granada (UGR): *Activar la auditoría de inicio de sesión en Windows*.
