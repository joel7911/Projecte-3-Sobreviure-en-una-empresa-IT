# Linux: LVM amb Zorin OS


## 1. Preparar l’entorn

Primer cal instal·lar els paquets necessaris per gestionar discos i LVM. També crearem dos discos virtuals de 10 GB que seran els que utilitzarem inicialment.
sudo apt update
sudo apt install fdisk lvm2

<img width="894" height="287" alt="image" src="https://github.com/user-attachments/assets/c1272319-a0a1-4cc8-93b5-97458f6d4c9b" />



## 2. Configuració inicial de LVM

Particionem els discos inicials (sdb i sdc) per poder-los utilitzar amb LVM:
sudo fdisk /dev/sdb
# n → nova partició
# t → 8e (Linux LVM)
# w → guardar

sudo fdisk /dev/sdc
# mateix procés
sudo partprobe

<img width="841" height="566" alt="image" src="https://github.com/user-attachments/assets/922926bf-ffcd-4a66-83b4-c3ddf4932e4f" />


Creem els Physical Volumes (PV):
sudo pvcreate /dev/sdb1 /dev/sdc1

<img width="482" height="81" alt="image" src="https://github.com/user-attachments/assets/859b8cda-38c0-4b4d-be5c-71fa37c7336e" />


Creem el Volume Group (VG):
sudo vgcreate vg_empresa /dev/sdb1 /dev/sdc1

<img width="576" height="73" alt="image" src="https://github.com/user-attachments/assets/f123d3b8-8662-4895-a81b-c756da36a6aa" />


Creem un Logical Volume (LV) inicial de 8 GB:
sudo lvcreate -L 8G -n lv_inicial vg_empresa

<img width="562" height="81" alt="image" src="https://github.com/user-attachments/assets/b82e55e7-fb58-4f3c-9fb7-5134460bb3a1" />


Formategem i muntem el volum:
sudo mkfs.ext4 /dev/vg_empresa/lv_inicial
sudo mkdir /mnt/inicial
sudo mount /dev/vg_empresa/lv_inicial /mnt/inicial

<img width="702" height="238" alt="image" src="https://github.com/user-attachments/assets/79ef14da-d78f-48fd-b2b6-30bfc7a9bce7" />

<img width="593" height="80" alt="image" src="https://github.com/user-attachments/assets/e3a4d113-7806-4b35-88e6-64d6e526c022" />

Perquè es munti automàticament en iniciar, afegim-lo a /etc/fstab i recarreguem la configuració:
sudo blkid /dev/vg_empresa/lv_inicial
sudo nano /etc/fstab
# Afegim la línia: UUID=TU_UUID /mnt/inicial ext4 defaults 0 2
sudo systemctl daemon-reload
sudo mount -a

<img width="765" height="283" alt="image" src="https://github.com/user-attachments/assets/51cf8b5a-3c09-4591-bfa9-2d5e0b06e223" />


## 3. Alta disponibilitat (mirroring)

Creem un LV mirror per protegir la informació en cas de fallada d’un disc:
sudo lvcreate -m1 -L 1G -n lvm_mirror vg_empresa
sudo lvdisplay

<img width="596" height="72" alt="image" src="https://github.com/user-attachments/assets/23c54c7c-5b9b-42cb-98c9-2297e245420b" />


## 4. Instantànies i discos addicionals

Afegim dos discos extra de 10 GB a la VM. Linux els detectarà com sdd i sde. Comprovem amb:
lsblk

Particionem els discos addicionals:
sudo fdisk /dev/sdd
# n → nova partició
# t → 8e
# w → guardar

sudo fdisk /dev/sde
# mateix procés
sudo partprobe

Afegim els discos al VG:
sudo pvcreate /dev/sdd1 /dev/sde1
sudo vgextend vg_empresa /dev/sdd1 /dev/sde1

<img width="499" height="75" alt="image" src="https://github.com/user-attachments/assets/7c3735ed-7736-4556-9dbb-5da69a2c1576" />


Creem el LV de dades amb un dels discos addicionals:
sudo lvcreate -L 8G -n lvm_dades vg_empresa /dev/sdd1
sudo mkfs.ext4 /dev/vg_empresa/lvm_dades
sudo mkdir /mnt/dades
sudo mount /dev/vg_empresa/lvm_dades /mnt/dades

<img width="701" height="253" alt="image" src="https://github.com/user-attachments/assets/f3439d3b-35bc-4236-9b23-e367cad7b592" />


## 5. Arxius de prova

Afegim alguns arxius dins del volum de dades per provar les snapshots:
cd /mnt/dades
echo "Archivo de prueba de Carlos" | sudo tee /mnt/dades/carlos.prueba
echo "Archivo de prueba de Martí" | sudo tee /mnt/dades/marti.prueba
ls


## 6. Crear snapshot

Creem una instantània del volum de dades:
sudo lvcreate -L 2G -s -n lv_snapshot /dev/vg_empresa/lvm_dades
sudo lvs

<img width="792" height="193" alt="image" src="https://github.com/user-attachments/assets/6abf10b8-16fe-498f-be72-2a02b47d7a58" />


lv_snapshot guarda l’estat actual dels arxius i es pot utilitzar per restaurar-los.

## 7. Simular fallada i restaurar snapshot

Simulem la pèrdua de fitxers:
sudo rm /mnt/dades/*.prueba
ls /mnt/dades

<img width="494" height="101" alt="image" src="https://github.com/user-attachments/assets/5dfeb90b-1a63-41f5-8c55-53202b6ebe83" />


Desmuntem el volum:
sudo umount /mnt/dades

Restaurar la snapshot:
sudo lvconvert --merge /dev/vg_empresa/lv_snapshot

<img width="634" height="57" alt="image" src="https://github.com/user-attachments/assets/37109b3c-d59c-41c7-af88-8dcce4e6699e" />



Muntem de nou el volum:
sudo mount /dev/vg_empresa/lvm_dades /mnt/dades
ls /mnt/dades

Ara els arxius carlos.prueba i marti.prueba tornen a estar disponibles.

<img width="634" height="83" alt="image" src="https://github.com/user-attachments/assets/dadd1246-6a37-442f-8e54-9c4101f28eed" />


## 8. Escalabilitat

Per comprovar que el volum es pot ampliar:
vgdisplay vg_empresa
sudo lvextend -L +2G /dev/vg_empresa/lvm_dades
sudo resize2fs /dev/vg_empresa/lvm_dades
df -h

<img width="800" height="607" alt="image" src="https://github.com/user-attachments/assets/2ffa63f1-ba7d-4992-8fb4-d28652832b28" />


Ara lvm_dades té més espai sense interrupcions.
