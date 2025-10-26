# Informe: Avaluació i Recomanació de Gestors de Contrasenyes

**Per a:** Direcció Tècnica, Comitè de Crisi d'EverPia
**De:** Equip de Becaris (Departament Tècnic)
**Data:** 26 d'octubre de 2025
**Assumpte:** Anàlisi i recomanació per a la implementació d'un gestor de contrasenyes corporatiu.

---

## 1. Introducció i Justificació

El recent incident de seguretat (fuita d'informació) a EverPia, originat pel compromís d'un compte tècnic, subratlla una vulnerabilitat crítica en la nostra infraestructura: la gestió inadequada de credencials. La investigació apunta a l'ús d'una **contrasenya feble o reutilitzada** com a vector d'atac principal.

### El Risc Crític de les Contrasenyes Febles i Reutilitzades

Les pràctiques actuals suposen un risc inacceptable per a la integritat i confidencialitat de les nostres dades per dues raons principals:

1.  **Contrasenyes Febles:** Les contrasenyes curtes, predictibles o basades en paraules comunes (p. ex., `EverPia2025!`) són extremadament vulnerables a **atacs de diccionari** i **atacs de força bruta**. Els ciberdelinqüents utilitzen programari automatitzat que pot provar milions de combinacions per segon, fent que aquestes contrasenyes siguin trivials de desxifrar.
2.  **Contrasenyes Reutilitzades:** Aquest és el risc més greu en el context de les fuites de dades. Quan un empleat reutilitza la mateixa contrasenya per a múltiples serveis (interns i externs), una violació de seguretat en *qualsevol* d'aquests serveis externs (p. ex., una xarxa social, un fòrum) exposa les nostres credencials internes. Els atacants utilitzen aquesta informació en atacs de **credential stuffing**, provant sistemàticament les credencials filtrades contra els nostres sistemes (VPN, correu, servidors) fins a trobar una coincidència. L'incident recent és un exemple clar d'aquest escenari.

### La Funció Crucial d'un Gestor de Contrasenyes

Un gestor de contrasenyes mitiga directament aquests riscos. Actua com una **volta digital xifrada** on s'emmagatzemen totes les credencials de l'usuari. La seva funció és doble:

* **Genera contrasenyes úniques i robustes:** Per a cada servei, l'eina crea una contrasenya llarga (p. ex., `kGj9!z$qR&3vL*8p#w@T`) que és impossible d'endevinar o de trencar amb atacs de diccionari.
* **Emmagatzema i autocompleta:** L'usuari ja no necessita recordar centenars de contrasenyes complexes. Només ha de recordar una única **contrasenya mestra** per desbloquejar la volta.

L'adopció d'un gestor de contrasenyes elimina la reutilització i assegura que cada punt d'accés a la nostra infraestructura estigui protegit per una credencial única i forta, trencant la cadena d'atac del *credential stuffing*.

---

## 2. Comparativa Tècnica: Bitwarden vs. KeePassXC

S'han avaluat dues de les solucions més respectades del mercat, que representen els dos models principals: **núvol (Bitwarden)** i **local/offline (KeePassXC)**.

| Característica | Bitwarden (Model Núvol / Online) | KeePassXC (Model Local / Offline) |
| :--- | :--- | :--- |
| **Model de Seguretat** | **Xifratge End-to-End (E2EE)**. La volta es xifra localment (AES-256) amb la clau mestra abans de pujar al núvol. El proveïdor (Bitwarden) no té accés a les contrasenyes. | **Arxiu local xifrat (KDBX)**. L'usuari té control total sobre l'arxiu de la base de dades (AES-256). La seguretat depèn de la gestió d'aquest arxiu. |
| **Sincronització** | **Automàtica i nativa**. Les dades es sincronitzen de forma transparent entre tots els dispositius (mòbil, escriptori, navegador) a través dels servidors de Bitwarden. | **Manual**. L'usuari és responsable de sincronitzar l'arxiu KDBX. Requereix l'ús de serveis de tercers (p. ex., OneDrive, Google Drive, Syncthing) o dispositius físics (USB). |
| **Accés Multiplataforma**| Excel·lent. Clients natius per a Windows, macOS, Linux, iOS, Android, i extensions per a tots els navegadors principals. Accés web disponible. | Bo. Clients natius per a Windows, macOS i Linux. Aplicacions mòbils de tercers (compatibles amb KDBX) existeixen, però requereixen la sincronització manual de l'arxiu. |
| **Dependència / Continuïtat**| Depèn dels servidors de Bitwarden per a la sincronització. Si el servei cau, l'accés es limita a la còpia local emmagatzemada a la memòria cau del dispositiu. | Totalment independent. Funciona sense connexió a Internet. No depèn de cap servei extern. L'únic punt de fallada és la pèrdua o corrupció de l'arxiu KDBX. |
| **Model de Llicència i Cost**| **Freemium & Open Source**. La versió gratuïta és extremadament completa i suficient per a ús individual (sincronització il·limitada). Plans de pagament per a empreses amb funcions avançades. | Totalment Gratuït i Open Source (FOSS). Llicència GPL. Sense cap cost. |
| **Portabilitat de Dades** | Es pot exportar la volta completa en formats estàndard (JSON, CSV). | Excel·lent. L'arxiu KDBX és un estàndard obert i es pot moure, copiar i utilitzar amb dotzenes d'aplicacions compatibles (KeePass, KeeWeb, etc.). |

---

## 3. Avantatges i Inconvenients dels Models

### Model Online / Núvol (Bitwarden)

* **Avantatges (Pros):**
    * **Usabilitat Superior:** La sincronització automàtica és la característica clau. És transparent per a l'usuari i garanteix que totes les credencials estiguin disponibles a tots els dispositius (mòbil, portàtil, tauleta) en tot moment.
    * **Fàcil Adopció:** La baixa fricció en l'ús diari és crucial per garantir que el personal realment utilitzi l'eina i no torni a pràctiques insegures.
    * **Escalabilitat:** Permet una fàcil transició a un pla d'empresa, que ofereix gestió centralitzada, compartició segura de credencials d'equip (p. ex., claus API, servidors) i auditories.
* **Inconvenients (Contres):**
    * **Dependència de Tercers:** Encara que les dades estan xifrades E2EE ("zero-knowledge"), la volta resideix en servidors externs. Un atac als servidors de Bitwarden podria, tot i que improbable, exposar les voltes xifrades (no el contingut).
    * **Requereix Connexió:** Necessita Internet per a la sincronització inicial i les actualitzacions.

### Model Offline / Escriptori (KeePassXC)

* **Avantatges (Pros):**
    * **Control i Seguretat Màxims:** L'arxiu de la base de dades (KDBX) mai abandona el control de l'usuari tret que aquest ho decideixi. És la millor opció per a entorns "air-gapped" (desconnectats).
    * **Independència Total:** No depèn de cap servei, subscripció o connexió a Internet. La continuïtat del negoci està garantida mentre l'usuari tingui l'arxiu.
    * **Cost Zero:** És totalment gratuït.
* **Inconvenients (Contres):**
    * **Fricció en la Sincronització:** La gestió manual de la sincronització de l'arxiu KDBX és el seu principal inconvenient. És propens a errors humans: oblidar de sincronitzar, crear conflictes de versions o perdre l'arxiu.
    * **Risc de Pèrdua:** Si un usuari perd l'única còpia del seu arxiu KDBX (o oblida la contrasenya mestra), totes les credencials es perden de forma irrecuperable. La gestió de còpies de seguretat recau totalment en l'usuari.
    * **Usabilitat:** L'experiència en dispositius mòbils i l'autocompletat al navegador són generalment menys fluids que en les solucions al núvol.

---

## 4. Recomanació Final

Després d'analitzar els requisits de seguretat, usabilitat i continuïtat del negoci per al personal tècnic d'EverPia, **recomanem l'adopció de Bitwarden com a gestor de contrasenyes estàndard**.

### Justificació de la Recomanació

Encara que KeePassXC ofereix un control teòricament superior en ser offline, el seu principal inconvenient —la sincronització manual— esdevé un **risc operacional significatiu en un entorn d'equip**. El personal tècnic necessita accés fluid a les credencials des de múltiples dispositius (estacions de treball, portàtils, mòbils per a verificacions 2FA o accés d'emergència) sense haver de gestionar manualment un arxiu.

**Bitwarden** ofereix el millor equilibri:

1.  **Seguretat Robusta:** El seu model de xifratge End-to-End (E2EE) de coneixement zero està provat i és l'estàndard de la indústria. Garanteix que només nosaltres podem accedir a les nostres dades.
2.  **Adopció Garantida:** La facilitat d'ús i la sincronització transparent són crucials per assegurar que el 100% del personal tècnic adopti l'eina. Si una eina de seguretat és complicada, el personal buscarà maneres d'evitar-la.
3.  **Preparat per al Futur:** Començar amb els plans gratuïts de Bitwarden ens permet moure'ns fàcilment a un pla "Teams" o "Enterprise" en el futur. Això permetrà a la Direcció Tècnica gestionar de forma centralitzada les polítiques de contrasenyes, compartir credencials sensibles (com les d'un servidor de producció) de forma segura i revocar l'accés a ex-empleats instantàniament.


