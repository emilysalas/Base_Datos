### 💻 Ejercicio 6: Tienda Informática

---

#### 📋 Descripción
Se desea crear una aplicación para la gestión de una tienda informática:
* **Productos:** Código, descripción, precio y número de existencias.
* **Clientes:** Código, nombre, apellidos, dirección y número telefónico.
* **Ventas:** Un cliente puede comprar varios productos y un mismo producto puede ser comprado por varios clientes. Cada vez que se compre un artículo quedará registrada la fecha de compra.
* **Proveedores:** Código, nombres, apellidos, dirección, provincia y número de teléfono. Un producto puede ser suministrado por varios proveedores y un proveedor suministra varios productos.

#### 🔑 Entidades y Atributos

| 📦 Entidad | 🏷️ Atributos |
| :--- | :--- |
| **Producto** | Código, Descripción, Precio, Num_Existencias |
| **Cliente** | Código, Nombre, Apellido, Dirección, Num_Teléfono |
| **Proveedor** | Código, Nombres, Apellidos, Dirección, Provincia, Num_Teléfono |

#### 🗂️ Diagrama conceptual
```
                 +----------+
                 | Cliente  |
                 +----------+
                      | M
                      |
                   < Vende > (Atributo: Fecha)
                      |
                      | N
+-----------+    M    |    N    +-----------+
| Proveedor | ----- < Suministra > ----- | Producto  |
+-----------+                   +-----------+
```
#### 🗂️ Diagrama conceptual a mano
<img width="461" height="454" alt="image" src="https://github.com/user-attachments/assets/80adba4b-faa1-489c-bf7d-ca70fca01885" />

---

💡Desea regresar? [🔙](README.md)
