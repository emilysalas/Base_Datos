### 📖 Ejercicio 1: Sistema de Biblioteca (Nivel Básico)

---

#### 📋 Descripción
Una biblioteca registra libros y autores. Un libro puede tener varios autores y un autor varios libros. Los socios toman libros prestados; de cada préstamo interesan la fecha de retiro y la de devolución.

#### 🗂️ Diagrama conceptual
```
  +---------+         1..N         +----------+         1..N         +-------+
  |  Libro  | -------------------- | esEscrito | -------------------- | Autor |
  +---------+                      +----------+                      +-------+
       | 1
       |
       | N
  +----------+
  | Préstamo | ---- (Fecha_Retiro, Fecha_Devolución)
  +----------+
       | N
       |
       | 1
  +----------+
  |  Socio   |
  +----------+
```
#### 🗂️ Diagrama conceptual a mano
<img width="970" height="264" alt="image" src="https://github.com/user-attachments/assets/a837d8ef-96b3-41da-a3dd-c656da90b6d1" />

#### 🗂️ Modelo Relacional 
<img width="601" height="237" alt="image" src="https://github.com/user-attachments/assets/6c7dc7de-1c99-4f50-b76d-feac441c96ce" />

#### 🗂️ Tabla SQL
```sql
CREATE TABLE socio (
    id_socio INT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE libro (
    isbn VARCHAR(20) PRIMARY KEY,
    titulo VARCHAR(150) NOT NULL
);

CREATE TABLE autor (
    id_autor INT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE libro_autor (
    isbn VARCHAR(20) NOT NULL,
    id_autor INT NOT NULL,
    PRIMARY KEY (isbn, id_autor),
    FOREIGN KEY (isbn) REFERENCES libro(isbn),
    FOREIGN KEY (id_autor) REFERENCES autor(id_autor)
);

CREATE TABLE prestamo (
    id_prestamo INT PRIMARY KEY,
    id_socio INT NOT NULL,
    isbn VARCHAR(20) NOT NULL,
    fecha_retiro DATE NOT NULL,
    fecha_devolucion DATE,
    FOREIGN KEY (id_socio) REFERENCES socio(id_socio),
    FOREIGN KEY (isbn) REFERENCES libro(isbn)
);
```
---

💡Desea regresar? [🔙](README.md)
