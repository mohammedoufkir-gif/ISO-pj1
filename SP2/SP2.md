#Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers (20h)
-
## Sistemes de fitxers i particions

### Mida de sector
La mida del sector és la unitat mínima **física** on es guarden les dades en un disc. Per defecte és de **512 bytes** (en discs moderns pot ser de 4096 bytes). Aquesta mida **no es pot modificar**.

### Mida de bloc
La mida del bloc (o *cluster*) és la unitat mínima **lògica** on es guarden les dades a nivell de sistema operatiu.  
Per defecte és de **4096 bytes (4 KB)**, equivalent a 8 sectors.  
<img width="853" height="105" alt="image" src="https://github.com/user-attachments/assets/5a5782bf-aee4-4626-8b1e-454b49258725" />

Creem un fixer amb echo.

Despres fem du -b per veure la mida del fixer.

Despres podem comprobar la mida real amb du -sh podem veure que ocupa 4,0k per que es la mida minima dins del sistema opratiu.

<img width="1021" height="234" alt="Captura de pantalla de 2025-10-27 12-29-53" src="https://github.com/user-attachments/assets/e9bb5383-30bd-4600-9848-99d1e5a6e75c" />

Aquesta mida **es pot modificar** quan es formata la partició.  
Cada partició pot tenir el seu **propi sistema de fitxers** i la seva **pròpia mida de bloc**.

### Fragmentació interna
La fragmentació interna es produeix quan la mida dels blocs és més gran que la mida dels arxius que s’hi guarden. Això provoca **desaprofitament d’espai**.

### Fragmentació externa
La fragmentació externa es produeix quan un fitxer **no està guardat en blocs consecutius**. Això fa que els accessos siguin **més lents**, ja que el disc ha de llegir-lo en diferents zones.

### Sistema de fitxers
Hi ha molts tipus de sistemes de fitxers. Cada un està **optimitzat per funcions concretes** i té **limitacions pròpies** (mida màxima d’arxiu, inodes, etc.).

---

### Tipus de formateig

#### Baix nivell
- Elimina tot.  
- Reconstrueix estructures físiques i pot **reparar sectors defectuosos**.  
- Necessita programes específics.  
- No s’usa habitualment en discs moderns.

#### Mig nivell
- Similar a l’alt nivell però **marca sectors defectuosos** per no utilitzar-los.

#### Alt nivell
- No elimina tots els arxius físicament; només **esborra el sistema de fitxers**.  
- Si troba sectors defectuosos, normalment **els ignora**.

---

### Partició
Una partició és un **tros físic del disc dur**.  
Amb eines com **GParted** podem crear, eliminar i redimensionar particions, però **no podem canviar la mida de bloc** sense tornar a formatar.

### Volum
Un volum és una **capa d’abstracció** per damunt de les particions i/o discs, utilitzada per sistemes com LVM o RAID.

---

### Gestió de particions

#### GParted
Eina gràfica per:
- Crear particions  
- Redimensionar  
- Eliminar  
- Formatar  
- Veure sistemes de fitxers
#### Creacio de particions amb GParted
<img width="816" height="561" alt="image" src="https://github.com/user-attachments/assets/6a000586-4d9f-4094-83a3-2f386e563388" />
<img width="602" height="487" alt="image" src="https://github.com/user-attachments/assets/2c6f3529-d029-4396-bc52-5dc414cdf473" />
<img width="902" height="313" alt="image" src="https://github.com/user-attachments/assets/95878d7d-b2ba-42ae-bf43-55fc07c08cc2" />

<img width="602" height="487" alt="image" src="https://github.com/user-attachments/assets/59939785-43e6-4ff9-85a4-2179e4c8848e" />
<img width="799" height="366" alt="image" src="https://github.com/user-attachments/assets/c5c5ece0-27bc-4766-b479-d8c357d53a17" />
<img width="799" height="366" alt="image" src="https://github.com/user-attachments/assets/96e604dc-5ab9-4bc7-8b4d-188c37b5c6ea" />

---

### Comandes (Linux)
## Gestió de procesos
## Gestió d'usuaris i grups i permisos
## Còpies de seguretat i automatització de tasques
## Quotes d'usuari

