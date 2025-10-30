Aquí teniu el resum de la feina en català, sense emojis i en format Markdown:

---

`RESUM.md`

# Resum de la Tasca T01: Gestor de Contrasenyes

Aquesta tasca es va encarregar com a resposta directa a una **fuita d'informació (data breach)** a EverPia, causada per una contrasenya feble o reutilitzada en un compte tècnic.

L'objectiu principal era estandarditzar la seguretat de les credencials del personal tècnic mitjançant la selecció, justificació i documentació d'un gestor de contrasenyes corporatiu.

## Objectius del Treball

El treball es va dividir en dues fases clarament definides:

### Fase 1: Anàlisi i Justificació (Informe)

L'objectiu era crear un informe (`informe.md`) que sustentés la decisió de la Direcció Tècnica d'adoptar un gestor de contrasenyes:

1.  **Justificació del Risc:** Explicar tècnicament per què les contrasenyes febles i reutilitzades són un risc crític (esmentant atacs de diccionari, *credential stuffing*, etc.).
2.  **Comparativa Tècnica:** Realitzar una taula comparativa entre els dos models principals de gestors:
    * **Bitwarden (Núvol/Online):** Analitzar sincronització, seguretat (E2EE) i usabilitat.
    * **KeePassX/XC (Escriptori/Offline):** Analitzar arxiu KDBX, control local i independència del núvol.
3.  **Recomanació:** Escollir i justificar l'eina més adequada per al personal tècnic (es va escollir **Bitwarden**).

### Fase 2: Guia d'Ús Tècnica (Manual Operatiu)

L'objectiu era desenvolupar una guia pràctica (`guia.md`) basada en l'eina seleccionada (Bitwarden) per a la formació del personal. La guia havia de cobrir els punts següents:

1.  **Configuració Inicial:** Creació del compte mestre i instal·lació de l'aplicació d'escriptori i l'extensió del navegador.
2.  **Generació Segura:** Ús del generador de contrasenyes.
3.  **Flux de Treball:** Demostrar com desar i utilitzar la funció d'emplenament automàtic (*autofill*).
4.  **Còpies de Seguretat (Backup):** Explicar el procés d'exportació segura i les millors pràctiques per emmagatzemar la còpia de seguretat (p. ex., en clau USB xifrada).

## Lliurament

El lliurament final requeria una estructura de fitxers organitzada al repositori:

* `README.md`: Descripció general.
* `informe.md`: Contingut de la Fase 1.
* `guia.md`: Contingut de la Fase 2, amb referències a captures de pantalla a la carpeta `img/`.
---
[Guia](Guia.md)
