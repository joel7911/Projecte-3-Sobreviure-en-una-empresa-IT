

# Guia d'Ús Tècnica: Bitwarden

**Objectiu:** Aquesta guia operativa descriu el procés d'instal·lació, configuració i ús de Bitwarden, l'eina seleccionada per la Direcció Tècnica per gestionar les credencials del personal.
**Audiència:** Personal Tècnic d'EverPia.

---

## 1. Instal·lació i Configuració Inicial

El nostre primer pas és crear el compte mestre, que serà la clau per a la vostra volta digital, i després instal·lar les eines necessàries.

### 1.1. Creació del Compte Mestre

La **Contrasenya Mestra** és la credencial més important que tindreu. És l'única contrasenya que heu de memoritzar.

**ADVERTIMENT:** Si perdeu o oblideu la vostra Contrasenya Mestra, Bitwarden no la pot recuperar (política de coneixement zero) i perdreu l'accés a totes les vostres credencials. Assegureu-vos que sigui **robusta i memorable**.

1.  Aneu al lloc web oficial de Bitwarden: [https://bitwarden.com](https://bitwarden.com)
2.  Feu clic a "Inicia" o "Get Started" per crear un nou compte.
3.  Empleneu el formulari. Introduïu el vostre correu electrònic corporatiu (`@everpia.com`).
    
4.  Creeu la vostra **Contrasenya Mestra**.
5.  Afegiu una **Pista** (Hint) si ho considereu necessari, però assegureu-vos que la pista no sigui la contrasenya en si.
    
6.  Accepteu els termes i envieu el formulari.

### 1.2. Instal·lació de l'Aplicació d'Escriptori

L'aplicació d'escriptori us dona accés complet a la volta, fins i tot sense connexió.

1.  Aneu a la pàgina de descàrregues: [https://bitwarden.com/download/](https://bitwarden.com/download/)
2.  Descarregueu l'instal·lador per al vostre sistema operatiu (Windows, macOS o Linux).
    
3.  Instal·leu l'aplicació i inicieu sessió amb el vostre Compte Mestre.

### 1.3. Instal·lació de l'Extensió del Navegador

Aquesta és l'eina més important per a l'ús diari, ja que gestiona l'emplenament automàtic.

1.  Obriu el vostre navegador principal (Chrome, Firefox, Edge, etc.).
2.  Aneu a la botiga d'extensions del navegador (Chrome Web Store, Firefox Add-ons).
3.  Cerqueu "Bitwarden" i afegiu l'extensió oficial.
    
4.  Un cop instal·lada, feu clic a la icona de Bitwarden a la barra d'eines i inicieu sessió.
5.  (Recomanat) Fixeu la icona de l'extensió a la barra d'eines per a un accés ràpid.

---

## 2. Generació de Contrasenyes Segures

Una de les funcions principals és deixar de crear contrasenyes febles.

1.  Feu clic a la icona de l'extensió de Bitwarden al navegador.
2.  Aneu a la pestanya **Generador**.
3.  Ajusteu els paràmetres de la contrasenya. Per a comptes tècnics, es recomana:
    * **Longitud:** Mínim 20 caràcters.
    * **Tipus:** Contrasenya.
    * **Caràcters:** Activeu les 4 opcions (Majúscules, Minúscules, Números i Caràcters especials).
    
4.  Feu clic a **Copiar** per utilitzar la contrasenya generada en un nou registre. L'eina també us permetrà autocompletar-la directament.

---

## 3. Exemples d'Ús i Emplenament Automàtic

### 3.1. Desar una Credencial d'un Servei Web (Automàtic)

La forma més senzilla de desar una contrasenya és durant el registre a un nou servei.

1.  Aneu a la pàgina de registre del nou servei web.
2.  Empleneu el vostre nom d'usuari.
3.  En el camp de la contrasenya, utilitzeu el **Generador** (vegeu secció 2) per crear i emplenar una contrasenya segura.
4.  En completar el registre i iniciar sessió, Bitwarden detectarà l'acció i mostrarà una barra a la part superior del navegador.
5.  Feu clic a **Desa**. La credencial (usuari, contrasenya i URL) s'emmagatzemarà a la vostra volta.

### 3.2. Desar una Credencial de Correu Electrònic (Manual)

També podeu afegir credencials manualment, com ara el vostre compte de correu principal o un accés SSH.

1.  Obriu l'extensió de Bitwarden o l'aplicació d'escriptori.
2.  Feu clic al botó **+** (Afegir un element).
    
3.  Empleneu la informació:
    * **Tipus:** Element d'inici de sessió.
    * **Nom:** Un nom descriptiu (p. ex., "Correu EverPia (Google)").
    * **Nom d'usuari:** El vostre correu (`nom.cognom@everpia.com`).
    * **Contrasenya:** La vostra contrasenya actual.
    * **URI 1:** La URL d'inici de sessió (p. ex., `https://accounts.google.com`). Això és clau perquè l'autocompletat funcioni.
4.  Feu clic a **Desa**.

### 3.3. Emplenament Automàtic (Autofill)

Un cop desada, Bitwarden farà la feina per vosaltres.

1.  Aneu a la pàgina d'inici de sessió d'un servei que ja teniu desat (p. ex., el correu de l'apartat 3.2).
2.  La icona de Bitwarden a la barra d'eines mostrarà un número, indicant que té credencials per a aquest lloc.
3.  Feu clic directament al camp d'usuari o contrasenya.
4.  Apareixerà un petit menú de Bitwarden. Feu clic al nom del compte que voleu utilitzar.
5.  Bitwarden emplenarà automàticament l'usuari i la contrasenya.
6.  (Alternativa ràpida) També podeu utilitzar la drecera de teclat: **Ctrl+Shift+L** (o Cmd+Shift+L a macOS).

---

## 4. Gestió de Còpies de Seguretat (Backup)

Tot i que Bitwarden és un servei al núvol, és una **política de seguretat obligatòria** mantenir una còpia de seguretat personal i xifrada de la vostra volta.

### 4.1. Com Exportar la Volta

La forma més segura d'exportar és des de l'**aplicació d'escriptori**.

1.  Obriu l'aplicació d'escriptori de Bitwarden.
2.  Assegureu-vos que la vostra volta està sincronitzada (normalment ho fa automàticament).
3.  Aneu al menú superior: `Fitxer` > `Exportar Volta`.
4.  Se us demanarà la vostra Contrasenya Mestra per confirmar l'operació.
5.  Seleccioneu el format d'arxiu. **ATENCIÓ:**
    * **`.json (xifrat)`:** AQUEST ÉS EL MÈTODE RECOMANAT. Genera un arxiu JSON que està protegit per la vostra Contrasenya Mestra.
    * `.csv` o `.json` (sense xifrar): Aquests formats exporten les vostres contrasenyes en **text pla**. Són extremadament insegurs i només s'han d'utilitzar si sabeu què esteu fent (p. ex., per migrar a una altra eina en un entorn controlat).
6.  Trieu `.json (xifrat)`, doneu-li un nom (p. ex., `bitwarden_export_AAAA-MM-DD.json`) i deseu-lo.

### 4.2. Emmagatzematge Segur de la Còpia de Seguretat

L'arxiu `json (xifrat)` que heu creat és la vostra línia de vida. Tracteu-lo amb la màxima cura.

**Pràctiques Recomanades:**

1.  **Clau USB Xifrada:**
    * Desar l'arxiu exportat en un dispositiu USB.
    * Aquest dispositiu USB ha d'estar **xifrat completament** (usant VeraCrypt, BitLocker To Go, o eines similars).
    * Desar aquest USB en una ubicació física segura (p. ex., un calaix amb clau, diferent d'on guardeu el vostre portàtil).
2.  **Emmagatzematge al Núvol Xifrat:**
    * Com que hem exportat en format `json (xifrat)`, és relativament segur pujar aquest arxiu a un servei d'emmagatzematge al núvol (p. ex., el vostre Google Drive o OneDrive corporatiu).
    * Per a una capa extra de seguretat, podeu comprimir l'arxiu `json (xifrat)` en un `.zip` protegit amb una contrasenya diferent abans de pujar-lo.

**Què NO s'ha de fer:**

* **NO** exportar en `.csv` (text pla) i desar-lo a l'escriptori.
* **NO** enviar l'exportació per correu electrònic, ni tan sols a vosaltres mateixos.
* **NO** desar la còpia de seguretat al mateix disc dur que el vostre sistema operatiu principal sense xifratge addicional.
