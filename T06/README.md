
# T06: Fonaments del servei DNS

## A. Diagnosi Avançada amb dig (Linux / macOS)

### Comanda 1: Consulta Bàsica de Registre A

**Comanda:**
`dig xtec.cat A`
```bash
dig xtec.cat A
```
<img width="649" height="478" alt="image" src="https://github.com/user-attachments/assets/db72330f-510b-4d7f-936c-2cdea09f7bb2" />


---

### Comanda 2: Servidors de Noms NS

**Comanda Executada:** `dig tecnocampus.cat NS`
```bash
dig tecnocampus.cat NS
```

<img width="645" height="424" alt="image" src="https://github.com/user-attachments/assets/0290e6a3-39b6-46d1-b205-118c08fff229" />

Anàlisi: Demana el registre SOA (Start of Authority). L'anàlisi se centra a extreure de la resposta el correu de l'administrador (el camp RNAME, recordant que el primer punt substitueix l'arrova, p. ex., hostmaster.escolapia.cat. equival a hostmaster@escolapia.cat) i el número de sèrie (Serial), que indica la versió de la configuració de la zona.

---

### Comanda 3

**Comanda Executada:** `dig escolapia.cat SOA`
```bash
dig escolapia.cat SOA
```

<img width="637" height="426" alt="image" src="https://github.com/user-attachments/assets/694603e8-a0c0-4f11-aa83-da4adb9038f1" />


**Anàlisi:** Extracció del correu de l'administrador (recordant la conversió de l'arroba a punt) i el número de sèrie del domini (serial).

---

### Comanda 4: Resolució Inversa

**Comanda Executada:** `dig -x 147.83.2.135`

<img width="643" height="410" alt="image" src="https://github.com/user-attachments/assets/5d78d4f8-556a-46d5-8632-048923702ed4" />


Anàlisi: Realitza una resolució inversa (opció -x). L'anàlisi busca el registre PTR (Pointer) a la ANSWER SECTION per obtenir el nom de domini (hostname) que està assignat a l'adreça IP 147.83.2.135.

---

## Comprovació de Resolució amb nslookup

### Comanda 1: Consulta No Autoritativa

<img width="363" height="390" alt="image" src="https://github.com/user-attachments/assets/41fff857-8f33-430a-8b75-148a08f85752" />


Anàlisi: L'anàlisi explica per què la resposta obtinguda és "No Autoritativa" (Non-authoritative answer). Això passa perquè qui respon és el nostre servidor DNS local (el resolver), que ens dóna la informació des de la seva memòria cau (cache), i no el servidor oficial del domini. La sortida indicarà quin servidor (el nostre) ha respost.

---

### Comanda 2: Consulta Autoritativa

<img width="545" height="706" alt="image" src="https://github.com/user-attachments/assets/660d0ce2-28ca-453f-8b43-a2b6d1130bba" />


Anàlisi: La diferència principal respecte a la Comanda 1 és l'absència de l'etiqueta "No Autoritativa". En preguntar directament a un dels servidors NS del domini, la resposta és oficial (autoritativa). L'anàlisi confirma que la informació prové directament de la font original.

---

## 4. Resolució Local (mDNS)

* **Comandes de Prova:** Les comandes que heu utilitzat per comprovar el funcionament de la resolució local (per exemple, `ping nom_altre_equip.local` o similar).
* **Anàlisi/Conclusions:** Explicació de si la prova ha funcionat, i una breu conclusió sobre la utilitat d'aquest mecanisme de resolució en entorns de xarxa sense servidor dedicat.
