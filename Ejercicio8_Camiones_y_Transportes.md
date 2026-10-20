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

---

💡Desea regresar? [🔙](README.md)
