## 1. Crear un Volum amb Dos Discos i Crear un Espai Simple

L'objectiu és crear un grup d'emmagatzematge amb dos discos i, posteriorment, un espai d'emmagatzematge de tipus Simple.

### Pas a Pas

1. Inicialitzar els discos (si cal):
    - Si els discos són nous o no estan inicialitzats, apareixerà la finestra "Inicializar disco".
    - Selecciona els discos a inicialitzar, per exemple, Disco 1, Disco 2, Disco 3.
    - Tria un estil de partició: MBR (Registro de arranque maestro) o GPT (Tabla de particiones GUID).
    - Fes clic a “Aceptar”.

<img width="717" height="458" alt="image" src="https://github.com/user-attachments/assets/b9a9d2e3-2cf6-4d04-bb2c-4a87436e0df4" />


2. Accedir a espais d'emmagatzematge:
    - Ves al **Panel de control** i obre **Administrar espacios de almacenamiento**.

<img width="494" height="326" alt="image" src="https://github.com/user-attachments/assets/c3669189-3a77-49c9-a7b1-be872459c57e" />


    - Fes clic a **Crear grupo de almacenamiento** dues vegades (si ho demana).

<img width="775" height="589" alt="image" src="https://github.com/user-attachments/assets/c8a907c7-f165-4a6d-b5ad-fd2d5593ac30" />


3. Seleccionar unitats:
    - A la finestra "Seleccione unidades para crear un grupo de almacenamiento", selecciona els dos discos que utilitzaràs.
    - Les unitats es mostraran com VBOX HARDDISK de 10,0 GB cadascuna, connectades per SATA.
4. Crear l'espai Simple:
    - Quan es creï el grup, configura l'espai:
        - **Tipo de resistencia**: selecciona Simple (sin resistencia).
        - Aquest tipus només crea una còpia de dades, però no et protegeix d'errors de disc.
        - **Sistema de archivos**: NTFS.
        - **Capacidad total del grupo**: 28,1 GB.
        - **Tamaño máximo**: 22,0 GB.

<img width="693" height="361" alt="image" src="https://github.com/user-attachments/assets/a97a67c3-2009-4279-8913-036a42a885cd" />


## 2. Eliminar l’Espai Anterior i Crear un Espai amb Reflex Doble

1. Eliminar l'espai simple:
    - A la interfície d'Espais d'emmagatzematge, selecciona l'espai simple creat anteriorment i utilitza l'opció **Eliminar**.
2. Crear un nou espai de Reflex Doble:
    - Fes clic a l’opció per crear un nou espai d’emmagatzematge.
    - Configura el nou espai:
        - **Capacidad total del grupo**: 28,1 GB.
        - **Tamaño máximo**: 30 GB.

<img width="689" height="467" alt="image" src="https://github.com/user-attachments/assets/0d60cd40-0f05-4e0d-bc2c-b539ba606e4c" />


        - **Nombre**: Espacio de almacenamiento.
        - **Letra de unidad**: G:.

<img width="663" height="524" alt="image" src="https://github.com/user-attachments/assets/4610137e-b326-4674-990f-36b2a78d0311" />


3. Guardar arxius:
    - Obre la nova unitat Espacio de almacenamiento (G:) i desa-hi alguns arxius, per exemple, el document de text 32234fd o una carpeta.

<img width="775" height="247" alt="image" src="https://github.com/user-attachments/assets/586b049c-c591-4b05-8047-8100caed8f50" />


## 3. Comprovar Tolerància de Fallades

1. Apagar la màquina virtual (VM).
2. Desconnectar el disc 2.
3. Tornar a arrencar la VM.
4. Comprovar l’alerta:
    - Accedeix a Espacios de almacenamiento.
    - Hauries de veure una advertència per l’Espacio de almacenamiento (G:), indicant que la resistència ha estat reduïda.
5. Comprovar la lectura de dades:
    - Obre l’Explorador de fitxers i navega fins a la unitat Espació de almacenamiento (G:).
    - Comprova si pots llegir la informació desada prèviament.

<img width="388" height="413" alt="image" src="https://github.com/user-attachments/assets/2c763eb2-84a7-45cc-be29-f0b365c6e6c4" />


## 4. Restaurar el Mirall

1. Afegir el tercer disc a la VM:
    - Apaga la VM i afegeix el tercer disc (per exemple, emmagatzematge_3.vdi o emmagatzematge_4.vdi) a la configuració del controlador SATA.

<img width="363" height="393" alt="image" src="https://github.com/user-attachments/assets/23a5d8d2-9958-4cf8-b068-4fa00ec79343" />


2. Torna a arrencar la VM.
3. Restaura el mirall:
    - A Espacios de almacenamiento, utilitza l’opció per **Agregar unidades o reparar el espacio**.

## 5. Afegir el Disc Eliminat

1. Apagar la màquina virtual.
2. Afegir el disc que s’havia eliminat:
    - Torna a connectar (afegir) el disc físic que havies eliminat al pas 3 (emmagatzematge_2.vdi) a la configuració del controlador SATA.

<img width="661" height="219" alt="image" src="https://github.com/user-attachments/assets/af5f3243-7cff-455e-9a02-a1654084ac19" />


3. Arrencar la VM:
    - El disc estarà disponible per ser gestionat novament al sistema.

<img width="375" height="361" alt="image" src="https://github.com/user-attachments/assets/ecfe0e42-bdb5-4de3-93e8-41bf63fe0a29" />
