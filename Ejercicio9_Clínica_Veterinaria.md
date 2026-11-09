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

#### 🗂️ Modelo Relacional 
<img width="601" height="371" alt="image" src="https://github.com/user-attachments/assets/12c45973-332d-408e-9b4a-39afa5383f28" />


#### 🗂️ Tabla SQL
```sql
CREATE TABLE propietario (
   cedula VARCHAR(10) PRIMARY KEY,
   apellidos VARCHAR(100) NOT NULL,
   nombres VARCHAR(100) NOT NULL,
   direccion VARCHAR(150) NOT NULL
);
CREATE TABLE telefono_propietario (
   cedula VARCHAR(10) NOT NULL,
   telefono VARCHAR(15) NOT NULL,
   PRIMARY KEY (cedula, telefono),
   FOREIGN KEY (cedula) REFERENCES propietario(cedula) ON DELETE CASCADE
);
CREATE TABLE familiar (
   cedula_propietario VARCHAR(10) PRIMARY KEY,
   cedula_familiar VARCHAR(10) NOT NULL,
   nombre VARCHAR(100) NOT NULL,
   telefono VARCHAR(15) NOT NULL,
   FOREIGN KEY (cedula_propietario) REFERENCES propietario(cedula) ON DELETE CASCADE
);
CREATE TABLE mascota (
   id_mascota INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL,
   fecha_nacimiento DATE NOT NULL,
   tipo VARCHAR(50) NOT NULL,
   cedula_propietario VARCHAR(10) NOT NULL,
   FOREIGN KEY (cedula_propietario) REFERENCES propietario(cedula)
);
CREATE TABLE personal (
   codigo VARCHAR(15) PRIMARY KEY,
   cedula VARCHAR(10) NOT NULL UNIQUE,
   nombre VARCHAR(100) NOT NULL
);
CREATE TABLE veterinario (
   codigo VARCHAR(15) PRIMARY KEY,
   fecha_alta DATE NOT NULL,
   especialidad VARCHAR(100) NOT NULL,
   FOREIGN KEY (codigo) REFERENCES personal(codigo)
);
CREATE TABLE auxiliar (
   codigo VARCHAR(15) PRIMARY KEY,
   base_cotizacion DECIMAL(10,2) NOT NULL,
   FOREIGN KEY (codigo) REFERENCES personal(codigo)
);
CREATE TABLE consulta (
   id_mascota INT NOT NULL,
   codigo_veterinario VARCHAR(15) NOT NULL,
   fecha DATE NOT NULL,
   diagnostico VARCHAR(255) NOT NULL,
   PRIMARY KEY (id_mascota, codigo_veterinario, fecha),
   FOREIGN KEY (id_mascota) REFERENCES mascota(id_mascota),
   FOREIGN KEY (codigo_veterinario) REFERENCES veterinario(codigo)
);


```

---

💡Desea regresar? [🔙](README.md)
