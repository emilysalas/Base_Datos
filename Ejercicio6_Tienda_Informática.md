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

#### 🗂️ Modelo Relacional 
<img width="601" height="223" alt="image" src="https://github.com/user-attachments/assets/0dee20ac-a6de-4f79-a2be-118ca4e1c87f" />

#### 🗂️ Tabla SQL
```sql
CREATE TABLE cliente (
   codigo VARCHAR(15) PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL,
   apellidos VARCHAR(100) NOT NULL,
   direccion VARCHAR(150) NOT NULL,
   num_telefono VARCHAR(15) NOT NULL
);
CREATE TABLE producto (
   codigo VARCHAR(15) PRIMARY KEY,
   descripcion VARCHAR(200) NOT NULL,
   precio DECIMAL(10,2) NOT NULL,
   num_existencias INT NOT NULL
);
CREATE TABLE proveedor (
   codigo VARCHAR(15) PRIMARY KEY,
   nombres VARCHAR(100) NOT NULL,
   apellidos VARCHAR(100) NOT NULL,
   direccion VARCHAR(150) NOT NULL,
   provincia VARCHAR(60) NOT NULL,
   num_telefono VARCHAR(15) NOT NULL
);
CREATE TABLE compra (
   codigo_cliente VARCHAR(15) NOT NULL,
   codigo_producto VARCHAR(15) NOT NULL,
   fecha DATE NOT NULL,
   PRIMARY KEY (codigo_cliente, codigo_producto, fecha),
   FOREIGN KEY (codigo_cliente) REFERENCES cliente(codigo),
   FOREIGN KEY (codigo_producto) REFERENCES producto(codigo)
);
CREATE TABLE suministra (
   codigo_proveedor VARCHAR(15) NOT NULL,
   codigo_producto VARCHAR(15) NOT NULL,
   PRIMARY KEY (codigo_proveedor, codigo_producto),
   FOREIGN KEY (codigo_proveedor) REFERENCES proveedor(codigo),
   FOREIGN KEY (codigo_producto) REFERENCES producto(codigo)
);

```
---

💡Desea regresar? [🔙](README.md)
