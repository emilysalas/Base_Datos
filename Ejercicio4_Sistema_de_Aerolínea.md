### ✈️ Ejercicio 4: Sistema de Aerolínea

#### 📋 Descripción
Una aerolínea opera vuelos (cada uno con número, fecha, origen y destino), cada vuelo lo realiza un avión. Los pasajeros realizan reservas para un vuelo específico, indicando asiento y tarifa pagada en el momento de la reserva.

#### 🗂️ Diagrama conceptual
```
+-------+       1       +---------+       1       +-------+
| Vuelo | ------------- | Realiza | ------------- | Avión |
+-------+               +---------+               +-------+
    | N
    |
    | Reserva (Asiento, Tarifa)
    |
    | 1
+-----------+
| Pasajero  |
+-----------+
```
#### 🗂️ Diagrama conceptual a mano
<img width="661" height="380" alt="image" src="https://github.com/user-attachments/assets/571231a9-750d-42d4-8179-41b6eb0fb9c9" />

#### 🗂️ Modelo Relacional 
<img width="601" height="181" alt="image" src="https://github.com/user-attachments/assets/c2a846ed-ae4a-40b3-b8a6-a9365b8ace4d" />

#### 🗂️ Tabla SQL
```sql
CREATE TABLE avion (
   matricula VARCHAR(15) PRIMARY KEY,
   modelo VARCHAR(50) NOT NULL
);
CREATE TABLE pasajero (
   id_pasajero INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL
);
CREATE TABLE vuelo (
   numero VARCHAR(15) PRIMARY KEY,
   fecha DATE NOT NULL,
   origen VARCHAR(60) NOT NULL,
   destino VARCHAR(60) NOT NULL,
   matricula VARCHAR(15) NOT NULL,
   FOREIGN KEY (matricula) REFERENCES avion(matricula)
);
CREATE TABLE reserva (
   id_reserva INT PRIMARY KEY,
   numero_vuelo VARCHAR(15) NOT NULL,
   id_pasajero INT NOT NULL,
   asiento VARCHAR(5) NOT NULL,
   tarifa_pagada DECIMAL(10,2) NOT NULL,
   FOREIGN KEY (numero_vuelo) REFERENCES vuelo(numero),
   FOREIGN KEY (id_pasajero) REFERENCES pasajero(id_pasajero)
);

```

---

💡Desea regresar? [🔙](README.md)
