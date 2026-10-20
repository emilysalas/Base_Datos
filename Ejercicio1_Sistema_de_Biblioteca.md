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

---

💡Desea regresar? [🔙](README.md)
