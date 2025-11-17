Configuració del directori amb LDAP Account Manager (LAM)



Per instalar aquest programa em de utilitzar la comanda: “sudo apt install ldap-account-manager -y” 




<img width="640" height="306" alt="image" src="https://github.com/user-attachments/assets/8163182e-ccb6-4a98-b427-531d14fd7c66" />



<img width="1347" height="518" alt="image" src="https://github.com/user-attachments/assets/f727e859-d76c-4d10-8810-bbfc691bb3e9" />

<img width="1347" height="518" alt="image" src="https://github.com/user-attachments/assets/7c790778-176a-4123-a872-8f3493d70c76" />

<img width="1600" height="787" alt="image" src="https://github.com/user-attachments/assets/378c47b8-b407-4eac-bfad-d3a0a5f5f7f8" />


Per crear l’usuari utilitzem com exemple el manager01, només hem de posar el nom de l'usuari en “apellido”

<img width="1600" height="618" alt="image" src="https://github.com/user-attachments/assets/7f8c84d4-4531-4a1e-8ee8-2b8214a8e5de" />


i ens fiquem en unix per addherir-lo al grup que li correspon

<img width="1600" height="633" alt="image" src="https://github.com/user-attachments/assets/c098622e-59cd-4388-bc0a-0fde7da30c70" />


i li donem a “guardar”

i actualitzem 


4. Integració de Client (Client Ubuntu Desktop)

Configuració de /etc/hosts (al Client): Igual que al servidor, editeu el fitxer /etc/hosts al client per assegurar-vos que pot contactar amb el servidor pel seu nom.








ara al client primer configurem el ldap

primer l’instal·lem


Executeu sudo apt update.
Instal·leu les utilitats LDAP.


ara hem nomes hem se seguir a les captures

Feu un test bàsic per veure si el client arriba al servidor:


y li dones a “s”















ara fem una consulta desdel ldap del client per comprovar si es conecta

afegim “ldap” a “passwd” i a “group”, treiem “system” a “shadow” i afegim “ldap” i treiem “system” a “gshadow”


aquí hem de treure “use_authok”

Aqui hem de afegir aquesta linea:


Apliqueu els canvis reiniciant el servei de memòria cau de noms (Name Service Cache Daemon).





Y hara reiniciem

I fem un id


i veiem com s’han creat les carpetes

