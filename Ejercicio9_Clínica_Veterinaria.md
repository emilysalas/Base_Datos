### 🏥 Ejercicio 9: Clínica Veterinaria

---

#### 📋 Descripción
Sistema para la gestión de atención médica de mascotas:
* **Propietario:** Cédula, apellidos, nombres, dirección, teléfono.
* **Familiar de Contacto:** Cédula, nombre, teléfono (solo interesa si el propietario aún no se ha dado de alta definitiva).
* **Mascota:** Identificador, nombre, fecha de nacimiento, tipo.
* **Personal:** Código, cédula, nombre. Se dividen en:
  * **Veterinarios:** Fecha de alta, especialidad.
  * **Auxiliares:** Base de cotización.
* **Consulta:** Fecha, diagnóstico. Registra la atención dada por un veterinario a una mascota.

#### 🔑 Entidades y Atributos

| 📦 Entidad | 🏷️ Atributos Especiales / Subclases |
| :--- | :--- |
| **Propietario** | Cédula, Apellidos, Nombres, Dirección, Teléfono |
| **Familiar** | Cédula, Nombre, Teléfono |
| **Mascota** | Identificador, Nombre, Fecha_Nacimiento, Tipo |
| **Personal (Clínica)** | Código, Cédula, Nombre |
| ↳ *Veterinario* | Fecha_Alta, Especialidad |
| ↳ *Auxiliar* | Cotización |
| **Consulta** | Diagnóstico, Fecha |

#### 🗂️ Diagrama conceptual
```
+----------+    1        1    +----------+
| Familiar | ----- < Tiene > ----- | Propietario|
+----------+                  +----------+
                                   | 1
                                < Tiene >
                                   | N
+-------------+               +----------+    1        N    +----------+
| Veterinario | ----- < Atiende > -| Consulta |- < Recibe > --| Mascota  |
+-------------+               +----------+                  +----------+
      | (Subclase)
+-------------+
|   Clínica   | (Personal)
+-------------+
```
#### 🗂️ Diagrama conceptual a mano
<img width="976" height="502" alt="image" src="https://github.com/user-attachments/assets/f718dd36-3cf2-48e3-8ee5-ffa113e0d5b9" />

---

💡Desea regresar? [🔙](README.md)
