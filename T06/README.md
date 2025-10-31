
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
**Anàlisi:** Llista explícita dels servidors de noms autoritatius per al domini tecnocampus.cat obtinguts del camp ANSWER SECTION.

<img width="645" height="424" alt="image" src="https://github.com/user-attachments/assets/0290e6a3-39b6-46d1-b205-118c08fff229" />




---

### Comanda 3

**Comanda Executada:** `dig escolapia.cat SOA`
```bash
dig escolapia.cat SOA
```

**Anàlisi:** Quina informació s'ha obtingut sobre el registre PTR (resolució inversa) per a l'adreça IP especificada.



**Anàlisi:** Extracció del correu de l'administrador (recordant la conversió de l'arroba a punt) i el número de sèrie del domini (serial).

---

### Comanda 4: Resolució Inversa

**Comanda Executada:** `dig -x 147.83.2.135`



**Anàlisi:** Quina informació s'ha obtingut sobre el registre PTR (resolució inversa) per a l'adreça IP especificada.


---

## Comprovació de Resolució amb nslookup

### Comanda 1: Consulta No Autoritativa

**Anàlisi:** Explicació de per què la resposta obtinguda és "No Autoritativa" (i quin servidor ha respost a la consulta).

**Captura:**

---

### Comanda 2: Consulta Autoritativa

**Anàlisi:** Descripció de les diferències observades respecte a la Comanda 1 (especialment la presència o absència de l'etiqueta).

**Captura:**

---

## 4. Resolució Local (mDNS)

* **Comandes de Prova:** Les comandes que heu utilitzat per comprovar el funcionament de la resolució local (per exemple, `ping nom_altre_equip.local` o similar).
* **Captura:** Imatge de la prova de resolució local.
* **Anàlisi/Conclusions:** Explicació de si la prova ha funcionat, i una breu conclusió sobre la utilitat d'aquest mecanisme de resolució en entorns de xarxa sense servidor dedicat.
