# Disseny de Solucions d'Emmagatzematge: Repte Garriga i Associats

## La Missió (El Repte del Client)

El prestigiós bufet d'advocats **Garriga i Associats** ha sol·licitat la renovació dels seus sistemes d'emmagatzematge. La gestió d'informació legal sensible requereix solucions que garanteixin:

- **Integritat i Redundància** (protecció contra fallades de disc)
- **Alta Disponibilitat**
- **Escalabilitat** (ampliació d'espai sense interrupcions)

Com a tècnics, la tasca és dissenyar i documentar una **Prova de Concepte (PoC)** per a entorns Linux i Windows que compleixi aquests requisits.

---

## Solucions a Dissenyar (Prova de Concepte)

El disseny se centra en dues tecnologies que proporcionen alta redundància i escalabilitat en els respectius sistemes operatius.

---

## 1. Part Linux: LVM (Logical Volume Manager)

S'utilitza la distribució **Zorin OS** per demostrar la flexibilitat d’LVM en la gestió de l’espai en disc.

### Requisit | Implementació Clau

#### **Configuració Base**
- Creació d’un **Grup de Volums (VG)** i un **Volum Lògic (LV)** inicial.
- Muntatge automàtic via `/etc/fstab`.

#### **Redundància**
- Implementació d’un **LV Mirror (`lvm_mirror`)** per a la protecció de dades.

#### **Instantànies**
- Creació i restauració de dades des d’una **Snapshot (`lv_snapshot`)** per garantir la integritat.

#### **Escalabilitat**
- Demostració de l’ampliació del volum lògic existent (`lvextend`).

---

## 2. Part Windows: Espais d’Emmagatzematge (Storage Spaces)

S'utilitza **Windows 11** per configurar un pool d’emmagatzematge altament resilient.

### Requisit | Configuracions a Demostrar

#### **Pool Inicial**
- Creació d’un **Storage Pool** amb tres discos.

#### **Resiliència**
- Creació d'Espais amb:
  - **Mirall (Mirroring)**
  - **Paritat (Parity)**
  - **Mirall Triple**

#### **Gestió**
- Visualització i gestió de l’estat del *Pool* i dels discos des de la consola de Windows.

<p>
  <a href="Guia.Zorin.md">
    <button style="padding:8px 16px; font-size:16px;">Guia Zorin</button>
  </a>
</p>

<p>
  <a href="GuiaWindows.md">
    <button style="padding:8px 16px; font-size:16px;">Guia Windows</button>
  </a>
</p>
