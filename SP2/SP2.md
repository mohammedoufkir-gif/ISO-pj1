#Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers (20h)
-
## Sistemes de fitxers i particions

### Mida de sector
La mida del sector és la unitat mínima **física** on es guarden les dades en un disc. Per defecte és de **512 bytes** (en discs moderns pot ser de 4096 bytes). Aquesta mida **no es pot modificar**.

### Mida de bloc
La mida del bloc (o *cluster*) és la unitat mínima **lògica** on es guarden les dades a nivell de sistema operatiu.  
Per defecte és de **4096 bytes (4 KB)**, equivalent a 8 sectors.  
Aquesta mida **es pot modificar** quan es formata la partició.  
Cada partició pot tenir el seu **propi sistema de fitxers** i la seva **pròpia mida de bloc**.

### Fragmentació interna
La fragmentació interna es produeix quan la mida dels blocs és més gran que la mida dels arxius que s’hi guarden. Això provoca **desaprofitament d’espai**.

### Fragmentació externa
La fragmentació externa es produeix quan un fitxer **no està guardat en blocs consecutius**. Això fa que els accessos siguin **més lents**, ja que el disc ha de llegir-lo en diferents zones.

### Sistema de fitxers
Hi ha molts tipus de sistemes de fitxers. Cada un està **optimitzat per funcions concretes** i té **limitacions pròpies** (mida màxima d’arxiu, inodes, etc.).

---

## Tipus de formateig

### Baix nivell
- Elimina tot.  
- Reconstrueix estructures físiques i pot **reparar sectors defectuosos**.  
- Necessita programes específics.  
- No s’usa habitualment en discs moderns.

### Mig nivell
- Similar a l’alt nivell però **marca sectors defectuosos** per no utilitzar-los.

### Alt nivell
- No elimina tots els arxius físicament; només **esborra el sistema de fitxers**.  
- Si troba sectors defectuosos, normalment **els ignora**.

---

## Partició
Una partició és un **tros físic del disc dur**.  
Amb eines com **GParted** podem crear, eliminar i redimensionar particions, però **no podem canviar la mida de bloc** sense tornar a formatar.

## Volum
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

---

### Comandes (Linux)
##Gestió de procesos
##Gestió d'usuaris i grups i permisos
##Còpies de seguretat i automatització de tasques
##Quotes d'usuari

