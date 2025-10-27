---
layout: default
title: "Sprint 1: Instalacio i Configuracio inicial"
---
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

<img width="460" height="334" alt="image" src="https://github.com/user-attachments/assets/daaefe25-385f-407d-96df-35bf70efe7c8" />



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
# Instalacio de windows 10 

Arranquem amb la ISO de windows 10
<br/>
<img width="364" height="95" alt="image" src="https://github.com/user-attachments/assets/b28d5cbb-f11d-489e-938f-23e3f7579f27" />
<br/>

Fem una instalacio normal fins a la part de les particions
<br/>

<img width="709" height="537" alt="Captura de pantalla de 2025-09-30 13-28-19" src="https://github.com/user-attachments/assets/0366236b-5bd8-4b6d-9efa-2eba99e226a5" />
<br/>

# Arrancar amb super grub
Per a arrancar amb lo super grub hem de inseri la ISO
<br/>

<img width="336" height="200" alt="Captura de pantalla de 2025-10-06 11-58-25" src="https://github.com/user-attachments/assets/403e95e5-7528-455b-9767-2da0e935547f" />
<br/>

Hem d'arrancar amb la iso de super grub
<br/>
<img width="660" height="487" alt="Captura de pantalla de 2025-10-06 11-58-58" src="https://github.com/user-attachments/assets/42cfd84c-dd73-4c9b-9092-2af922b27750" />
<br/>

Arranquem amb ubuntu
<br/>
<img width="634" height="544" alt="Captura de pantalla de 2025-10-06 11-59-14" src="https://github.com/user-attachments/assets/08c2bbd6-e8f2-4795-9969-1cb6ee7ae713" />

# Arreglar la paricio  de arranc
Vale una vegada a dins de ubuntu per a arreglar la particio de arranc primner la hem de identificar
<br/>
<img width="733" height="204" alt="Captura desde 2025-10-06 12-37-39" src="https://github.com/user-attachments/assets/1a1c12c1-520e-40a8-8d12-3bf095301095" />
<br/>


I hem de muntarla 
<br/>
<img width="579" height="64" alt="Captura de pantalla de 2025-10-06 12-35-21" src="https://github.com/user-attachments/assets/cee2490e-7e77-4c0d-8aa9-8bc19666812e" />
<br/>

Ara editem el archiu /etc/defaul/grub
<br/>
<img width="622" height="80" alt="Captura desde 2025-10-06 12-50-31" src="https://github.com/user-attachments/assets/41be5ca3-c9f1-4d63-82cc-fb9989de9bed" />
<br/>

I ara comeentem les lines seleccionades
<br/>
<img width="674" height="178" alt="Captura desde 2025-10-06 12-50-40" src="https://github.com/user-attachments/assets/37c18bdb-75c8-461e-b29c-61cd298b46ca" />
<br/>

Afegim la seguent linea:
<br/>
<img width="674" height="178" alt="Captura desde 2025-10-06 12-50-42" src="https://github.com/user-attachments/assets/e15b3347-8122-490e-bfbd-6308a38a45f0" />
<br/>
Actualidsem el grub
<br/>

<img width="525" height="51" alt="Captura desde 2025-10-06 12-51-15" src="https://github.com/user-attachments/assets/7a703bbd-0b4a-41f9-8472-5cdf7f55eebb" />
<br/>

Instalem el efibootmgr
<br/>

<img width="525" height="98" alt="Captura desde 2025-10-06 12-51-32" src="https://github.com/user-attachments/assets/c7479cd3-ace8-4a99-9e02-2ef51155c2e9" />
<br/>

Executem el efibootmgr
<br/>

<img width="537" height="229" alt="Captura desde 2025-10-06 12-51-43" src="https://github.com/user-attachments/assets/2d4cd015-afe9-4aae-abc2-8978d857f3cf" />
<br/>

Una vegada fet ja funcionara el boot
<br/>

<img width="884" height="503" alt="image" src="https://github.com/user-attachments/assets/6d7db200-718d-4b2f-977e-a22ed52b3df2" />
<br/>

## Punts de restauracio 
Primner afegim un disc per a le copies de seguretat
<br/>

<img width="209" height="166" alt="image" src="https://github.com/user-attachments/assets/be1a8784-2817-4fd3-a605-682434ed6e18" />
<br/>

Primer instalem el timeshift
<br/>

<img width="753" height="527" alt="Captura de pantalla de 2025-10-07 13-09-21" src="https://github.com/user-attachments/assets/89b9a3d9-17ef-437f-841a-e7882d068ecc" />
<br/>

Formatem el disc com a ext 4
<br/>

<img width="753" height="527" alt="Captura de pantalla de 2025-10-07 13-12-26" src="https://github.com/user-attachments/assets/ac62847c-18b9-457a-a272-bfbe96d170b2" />
<br/>
Arranquem el timeshift
<br/>
<img width="723" height="737" alt="Captura de pantalla de 2025-10-07 13-15-18" src="https://github.com/user-attachments/assets/1b5ad397-0863-40d2-b09e-0b0bb6689543" />

<br/>
Confegurem una copia de seguretat cada que arranca el SO
<br/>

<img width="723" height="737" alt="Captura de pantalla de 2025-10-07 13-15-55" src="https://github.com/user-attachments/assets/999d1bf6-1f3c-4769-aee2-12480a925d26" />
<br/>

Seleccionem el directori /home/mohamed
<br/>

<img width="926" height="707" alt="Captura de pantalla de 2025-10-07 13-16-12" src="https://github.com/user-attachments/assets/98727b39-08b7-45e1-882f-7dbb4e27e1f3" />
<br/>

Cremn archius de prova 
<br/>

<img width="926" height="707" alt="Captura de pantalla de 2025-10-07 13-16-43" src="https://github.com/user-attachments/assets/bdc2b002-27f8-40a5-809f-9417dab52ee1" />

<br/>
Reiniciem el dispositiu per a poder veure que se ha creat la copia correctament
<br/>

<img width="608" height="63" alt="image" src="https://github.com/user-attachments/assets/3782c683-23c0-42ff-84e0-cb1f893f58e8" />

<br/>
Eleminem els archius hola i adeu 
<br/>

<img width="692" height="255" alt="image" src="https://github.com/user-attachments/assets/dd2f363e-592f-4dc3-b0f4-7ac368abc471" />

<br/>
Ara restaurem
<br/>

<img width="504" height="594" alt="image" src="https://github.com/user-attachments/assets/16d63cf2-dc06-4eba-90c1-904489954890" />
<br/>

I seleccionem els archius que volem restaura
<br/>

<img width="504" height="594" alt="image" src="https://github.com/user-attachments/assets/40d4554f-dc10-4f1a-9df6-d00f2bbc4cf5" />
<br/>

Ye comensara fer  la restauracio 
<br/>

<img width="1286" height="802" alt="image" src="https://github.com/user-attachments/assets/72fa4509-1b96-4e17-8f64-9b5eb35b29d5" />


<br/>
Ara podem comproba que tanrt hola com adeu se han restaurat correctament

<br/>
<img width="771" height="280" alt="image" src="https://github.com/user-attachments/assets/cbe1d895-ec31-42fd-bddf-11bc7939266f" />

## Configuracio de la xarxa
Modifiquem els parametes de xarxa amb la iterficie grafica
<img width="774" height="528" alt="image" src="https://github.com/user-attachments/assets/59147f2f-4dd0-4ea8-9168-c152c9c372ea" />
<img width="774" height="528" alt="image" src="https://github.com/user-attachments/assets/14530130-3c5f-4997-90ac-22670769eec7" />
<img width="818" height="216" alt="image" src="https://github.com/user-attachments/assets/2cedbf4d-6d93-4388-91df-c6f312220629" />
<img width="762" height="385" alt="image" src="https://github.com/user-attachments/assets/f944efcc-18ee-4eac-ab88-3d82bf8a5bf5" />


<img width="523" height="27" alt="image" src="https://github.com/user-attachments/assets/44a53349-1487-4f68-9e38-f96fee579c58" />
<img width="797" height="312" alt="image" src="https://github.com/user-attachments/assets/f512cff2-09b6-4daf-9741-338c44878697" />
<img width="797" height="312" alt="image" src="https://github.com/user-attachments/assets/1a86948f-b737-40f3-a828-96482cd51591" />




## Comandes generals i instal·lacions

