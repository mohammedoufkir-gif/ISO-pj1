
# Sprint 1: Instal·lació, Configuració Inicial i Programari de Base (13h)

## Virtualització i instalacio del SO Ubuntu

### Creacio de la maquina virtual i requisits minims
Abans de crear la maquina virtual hem de entrar a la pagina  oficial de ubuntu i comprobar quins son els requisits minis del sistema operatiu.

Segons la pagina oficial els requisits minims recomendats son de 3 GB de ram.

<img width="872" height="304" alt="image" src="https://github.com/user-attachments/assets/0782f646-46cd-4cfd-a13a-617b57d53fa0" />

**RAM** en el nostre cas utilidzarem 4 GB de ram ja que de moment nomes arrancarem una maquina al mateix temps.

<img width="411" height="152" alt="image" src="https://github.com/user-attachments/assets/33a609b8-addd-4abd-a6fd-2d4e26a11455" />

**Emmagatzematge** utilidzarem 80GB ja que en un futur ficarem una instalacio dual amb window aixis quedara 40 GB per a ubuntu i 40 per a windows.

<img width="941" height="545" alt="Captura de pantalla de 2025-09-22 12-34-14" src="https://github.com/user-attachments/assets/87b9f6fe-a260-4fea-ada9-d0188caf66b2" />

**CPU(nuclis)** hem utilitzat només una CPU perquè realment per al ús que li donarem no fa falta res més.

<img width="660" height="259" alt="image" src="https://github.com/user-attachments/assets/a4debaea-4576-4d6d-9d79-e8d83220359e" />

### Particions

Per a les particions utilidzarem les seguents.

<img width="451" height="173" alt="image" src="https://github.com/user-attachments/assets/bf043212-5f76-4a67-b69c-e4609fce2f1c" />

**SWAP** > Jo no he utilidzat una particio swap j a que considero que per a el us que donaremm i sent una maquina virtual trobo que no es necesari.

**EXT4 15gb** / => Aquesta es la  particio  del arrel l'em ficat 15 GB per que es on se instala el sistema operatiu i algunes applicacions, amb 15 GB ja es mes que suficient.

**EXT4 2gb** /boot => La partició de boot l'hem creat per a poder tindre una instal·lació dual utilitzant grub customizer, 2 gb és suficient.

**EXT4 17gb** /home => Per a la partició del home he ficat 17 GB tot allò que sobra perquè és on es guarden la gran majoria de arxius dels usuaris com tindrem 1 usuari només i és una màquina virtual 17 GB ja va bé.

### Xarxa
#### Perque hem utilitzat la xarxa NAT
Hem utilitzat la xarxa NAT per a poder tindre conexio amb les altre maquines virtuals al mateix temps tenint NAT (internet).
#### Perque no hem utilidzat adaptador pont
Tot i que el adaptador pont ens permet tindre acces a la xarxa fisica i a internet te un problema es que al tindre un servidor  i canviarnos de clase com no es la matexa xarxa la ip assignada al servidor ja no serveis i ens toca canviara cosa que no pasa amb xarxa NAT.
<img width="666" height="135" alt="image" src="https://github.com/user-attachments/assets/64550fe6-6f2b-4c6a-a567-348485d1d808" />

### Inici

<img width="640" height="446" alt="image" src="https://github.com/user-attachments/assets/daaefe25-385f-407d-96df-35bf70efe7c8" />



## Llicènciament
### Llicència d’ús d’Ubuntu

Ubuntu és programari lliure i de codi obert.  
Aquest sistema operatiu es distribueix sota els termes de la GNU General Public License (GPL) i altres llicències lliures compatibles.

#### 1. Drets atorgats

Se’t concedeix el dret a:

- Utilitzar Ubuntu de manera gratuïta, tant en àmbits personals com professionals.  
- Copiar i redistribuir Ubuntu en qualsevol suport o mitjà.  
- Accedir al codi font i estudiar-ne el funcionament.  
- Modificar el programari i crear obres derivades.  
- Redistribuir versions modificades, sempre que es mantingui la mateixa llicència lliure aplicable.  

#### 2. Limitacions

Aquests drets es concedeixen amb les següents limitacions:

- El nom “Ubuntu” i els logotips associats són marques registrades de Canonical Ltd.  
- No es permet distribuir versions modificades utilitzant el nom ni els logotips oficials sense autorització expressa de Canonical.  

#### 3. Absència de garanties

Ubuntu es proporciona **sense cap garantia**.  
Ni els autors ni Canonical es fan responsables de possibles danys derivats de l’ús, la modificació o la redistribució del programari.

#### 4. Acceptació

En instal·lar, executar o redistribuir Ubuntu, acceptes els termes establerts en aquesta llicència i en les llicències individuals de cada component.

## Gestors d'arrencada per a instalacions DUALS
## Punts de restauracio 
## Configuracio de la xarxa
## Comandes generals i instal·lacions

