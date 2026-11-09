### 🚚 Ejercicio 8: Camiones y Transportes

---

#### 📋 Descripción
Se desea informatizar la gestión de una empresa de transporte que reparte paquetes por toda España:
* **Camionero:** Cédula, nombre, teléfono, dirección, salario, población.
* **Paquete:** Código del paquete, descripción, destinatario, dirección del destinatario.
* **Provincia:** Código de provincia, nombre. Un paquete sólo llega a una provincia, pero a una provincia llegan muchos paquetes.
* **Camión:** Matrícula, modelo, tipo, potencia. Un camionero conduce distintos camiones en fechas distintas.

#### 🔑 Entidades y Atributos

| 📦 Entidad | 🏷️ Atributos |
| :--- | :--- |
| **Camionero** | Cédula, Nombre, Teléfono, Dirección, Salario, Población |
| **Paquete** | Código, Descripción, Destinatario |
| **Provincia** | Código_Provincia, Nombre |
| **Camión** | Matrícula, Modelo, Tipo, Potencia |

#### 🗂️ Diagrama conceptual
```
                  +--------------+
                  | Destinatario |
                  +--------------+
                         | 1
                    < Pertenece >
                         | N
+-----------+     1   N  |  N        1    +-----------+
| Camionero | ----- < Distribuye > ----- |  Paquete  |
+-----------+                            +-----------+
      | N                                      | N
  < Conduce >                             < Distribuido >
      | N                                      | 1
+-----------+                            +-----------+
|  Camión   |                            | Provincia |
+-----------+                            +-----------+
```
#### 🗂️ Diagrama conceptual a mano
<img width="634" height="406" alt="image" src="https://github.com/user-attachments/assets/da250ae8-2381-4271-a9b4-06b9e151b419" />

#### 🗂️ Modelo Relacional 
<img width="601" height="255" alt="image" src="https://github.com/user-attachments/assets/8be45315-1936-446f-bb88-d971d7af44d9" />


#### 🗂️ Tabla SQL
```sql
CREATE TABLE camionero (
   cedula VARCHAR(10) PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL,
   telefono VARCHAR(15) NOT NULL,
   direccion VARCHAR(150) NOT NULL,
   salario DECIMAL(10,2) NOT NULL,
   poblacion VARCHAR(80) NOT NULL
);
CREATE TABLE provincia (
   codigo_provincia VARCHAR(10) PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL
);
CREATE TABLE camion (
   matricula VARCHAR(15) PRIMARY KEY,
   modelo VARCHAR(50) NOT NULL,
   tipo VARCHAR(50) NOT NULL,
   potencia INT NOT NULL
);
CREATE TABLE destinatario (
   id_destinatario INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL,
   direccion VARCHAR(150) NOT NULL
);
CREATE TABLE paquete (
   codigo_paquete VARCHAR(15) PRIMARY KEY,
   descripcion VARCHAR(200) NOT NULL,
   id_destinatario INT NOT NULL,
   cedula VARCHAR(10) NOT NULL,
   codigo_provincia VARCHAR(10) NOT NULL,
   FOREIGN KEY (id_destinatario) REFERENCES destinatario(id_destinatario),
   FOREIGN KEY (cedula) REFERENCES camionero(cedula),
   FOREIGN KEY (codigo_provincia) REFERENCES provincia(codigo_provincia)
);
CREATE TABLE conduce (
   cedula VARCHAR(10) NOT NULL,
   matricula VARCHAR(15) NOT NULL,
   fecha DATE NOT NULL,
   PRIMARY KEY (cedula, matricula, fecha),
   FOREIGN KEY (cedula) REFERENCES camionero(cedula),
   FOREIGN KEY (matricula) REFERENCES camion(matricula)
);

```
---

💡Desea regresar? [🔙](README.md)
