### 🍽️ Ejercicio 2: Pedidos de Restaurante (Nivel Intermedio)

---

#### 📋 Descripción
Los clientes realizan pedidos que contienen varios platos con distinta cantidad. Los platos se agrupan en categorías. Cada pedido lo atiende un único mesero. El precio del plato debe registrarse tal como estaba al momento del pedido, aunque luego cambie.

#### 🗂️ Diagrama conceptual
```
+---------+       1       +--------+       1       +--------+       N       +-------+
| Cliente | ------------- | Realiza | ------------- | Pedido | ------------- | Plato |
+---------+               +--------+               +--------+               +-------+
                                                       | 1                      | 1
                                                       |                        |
                                                       | N                      | 1
                                                   +---------+            +-----------+
                                                   | Mesero  |            | Categoría |
                                                   +---------+            +-----------+
```
#### 🗂️ Diagrama conceptual a mano
<img width="977" height="314" alt="image" src="https://github.com/user-attachments/assets/1140f342-d2d3-49fe-af63-28dc01d8b4d0" />

#### 🗂️ Modelo Relacional 
<img width="601" height="319" alt="image" src="https://github.com/user-attachments/assets/ac82b047-f042-451a-83f8-4db1493502fa" />


#### 🗂️ Tabla SQL
```sql
CREATE TABLE cliente (
   id_cliente INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL
);
CREATE TABLE mesero (
   id_mesero INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL
);
CREATE TABLE categoria (
   id_categoria INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL
);
CREATE TABLE plato (
   id_plato INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL,
   precio DECIMAL(10,2) NOT NULL,
   id_categoria INT NOT NULL,
   FOREIGN KEY (id_categoria) REFERENCES categoria(id_categoria)
);
CREATE TABLE pedido (
   id_pedido INT PRIMARY KEY,
   fecha DATE NOT NULL,
   id_cliente INT NOT NULL,
   id_mesero INT NOT NULL,
   FOREIGN KEY (id_cliente) REFERENCES cliente(id_cliente),
   FOREIGN KEY (id_mesero) REFERENCES mesero(id_mesero)
);
CREATE TABLE detalle_pedido (
   id_pedido INT NOT NULL,
   id_plato INT NOT NULL,
   cantidad INT NOT NULL,
   precio_unitario DECIMAL(10,2) NOT NULL,
   PRIMARY KEY (id_pedido, id_plato),
   FOREIGN KEY (id_pedido) REFERENCES pedido(id_pedido),
   FOREIGN KEY (id_plato) REFERENCES plato(id_plato)
);

```

---

💡Desea regresar? [🔙](README.md)
