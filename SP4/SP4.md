
## RAIDs
### Teoria RAID

El terme **RAID** (*Redundant Array of Independent Disks*) es refereix a una tecnologia d'emmagatzematge que combina diversos discs durs físics en una sola unitat lògica per millorar el rendiment o la seguretat.

---

####  Nivells de RAID més utilitzats

##### RAID 0 (Striping)
Distribueix les dades equitativament entre dos o més discs.
* **Objectiu:** Rendiment màxim.
* **Risc:** Si un sol disc falla, **es perden totes les dades**.
* **Capacitat:** $100\%$.

##### RAID 1 (Mirroring)
Crea una còpia exacta (mirall) de les dades en dos discs.
* **Objectiu:** Seguretat i continuïtat.
* **Avantatge:** Si un disc falla, l'altre té tota la informació.
* **Capacitat:** $50\%$.

##### RAID 5 (Paritat distribuïda)
Reparteix dades i informació de recuperació (paritat) entre almenys 3 discs.
* **Objectiu:** Equilibri entre capacitat i seguretat.
* **Resiliència:** Pot fallar **un disc** sense pèrdua de dades.
* **Capacitat:** $n - 1$ discs.

##### RAID 10 (1+0)
Combina el mirall (RAID 1) i el fraccionament (RAID 0). Requereix 4 discs.
* **Objectiu:** El millor rendiment i alta seguretat.
* **Capacitat:** $50\%$.

---

#### Taula Comparativa

| Nivell RAID | Discs Mínims | Tolerància a Fallades | Rendiment |
| :--- | :--- | :--- | :--- |
| **RAID 0** | 2 | Cap | Molt Alt |
| **RAID 1** | 2 | 1 disc | Mitjà |
| **RAID 5** | 3 | 1 disc | Alt (Lectura) |
| **RAID 10** | 4 | Almenys 1 disc | Excel·lent |

---

> [!IMPORTANT]
> **El RAID no és un Backup.** Un RAID protegeix contra la fallada física d'un disc, però no contra errors humans o virus. Cal seguir fent còpies de seguretat externes.


### RAID a Linux
**Aquesta es una maquina ubuntu amb dos disc (1GB + 1GB)per el RAID**

#### Instalacio del paquet

Primer instalem el paket mdam

<img width="528" height="24" alt="image" src="https://github.com/user-attachments/assets/1f7ed0ce-837f-415a-998b-672b5977f769" />

#### Formatacio dels discos

Fem un **lsblk** per identeficar els discos

<img width="715" height="447" alt="image" src="https://github.com/user-attachments/assets/d8e1cf59-4398-441f-bb89-222dfe01c932" />

Formatem els discos amb fdisk tant el "sdb" com el "sdc"

<img width="806" height="35" alt="image" src="https://github.com/user-attachments/assets/5ce24be4-f90b-4dae-bf15-1538786eda70" />

#### Creacio del RAID

Primer creem una carpeta dins de /mnt per muntar el RAID amb els permisos necesaris

<img width="695" height="195" alt="image" src="https://github.com/user-attachments/assets/f20e53f2-1505-4575-b032-53d6caef52a9" />

Creem un RAID que indiquem amb /dev/md0 com el veurem al nostre SO  , el level=1 que es equivalent a RAID 1, per ultim se indica els discos que se utilitzaran

<img width="875" height="202" alt="image" src="https://github.com/user-attachments/assets/5b33c7f9-9d04-46db-a252-761717e295e6" />

Formatem el raid amb el sistema de fixer ext4
<img width="873" height="271" alt="image" src="https://github.com/user-attachments/assets/fe6b315c-9413-4770-bcef-d31d57087d94" />

<img width="648" height="598" alt="image" src="https://github.com/user-attachments/assets/34a08b6d-53d3-4875-b31f-97e9a0314109" />

<img width="847" height="90" alt="image" src="https://github.com/user-attachments/assets/86fa3b0b-f3ae-401e-a055-536487e9745c" />

<img width="739" height="32" alt="image" src="https://github.com/user-attachments/assets/ab1718bd-0280-4069-a16c-18dea0cb17b8" />


<img width="885" height="63" alt="image" src="https://github.com/user-attachments/assets/96b1c941-ac36-40a8-84b2-dfcc9a318371" />
<img width="875" height="372" alt="image" src="https://github.com/user-attachments/assets/0eb939b7-64d9-4156-acf3-1926b2c7d739" />
re<img width="675" height="21" alt="image" src="https://github.com/user-attachments/assets/81019100-1341-4518-acd6-b4e243a076e4" />
<img width="372" height="78" alt="image" src="https://github.com/user-attachments/assets/0f3b0c73-2542-46a9-b800-8c2c1276b94c" />
<img width="549" height="51" alt="image" src="https://github.com/user-attachments/assets/17e06826-b4a3-44f0-bdd4-7b3054ae89f5" />

<img width="714" height="133" alt="image" src="https://github.com/user-attachments/assets/7f82c35f-216c-4ba0-8bb5-a41957ba9e43" />
<img width="714" height="133" alt="image" src="https://github.com/user-attachments/assets/d7f18e7d-a420-4ccd-801b-061a624f4c7d" />
<img width="645" height="48" alt="image" src="https://github.com/user-attachments/assets/d3d511bc-899f-4085-b0d0-7b92ec5c9beb" />
<img width="688" height="285" alt="image" src="https://github.com/user-attachments/assets/e9b014e1-bb6b-4ff1-9717-70e0c5e9013a" />
<img width="753" height="62" alt="image" src="https://github.com/user-attachments/assets/51698b6e-34bd-410a-8d3c-cc9ea2f52df7" />
borra raid
<img width="620" height="50" alt="image" src="https://github.com/user-attachments/assets/a670522d-74dd-435f-bc8f-06fc959fddaf" />
<img width="730" height="297" alt="image" src="https://github.com/user-attachments/assets/1f89b778-6689-42ed-834e-7cb6e4b16e0f" />
<img width="757" height="491" alt="image" src="https://github.com/user-attachments/assets/9ad7c528-bfbc-40a9-9b90-00966b0aacd1" />
<img width="653" height="97" alt="image" src="https://github.com/user-attachments/assets/86f05be2-2bc2-418c-97a4-30e98b023f2c" />
