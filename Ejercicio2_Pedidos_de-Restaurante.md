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

---

💡Desea regresar? [🔙](README.md)
