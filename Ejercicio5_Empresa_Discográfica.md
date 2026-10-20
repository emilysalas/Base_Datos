### 🎼 Ejercicio 5: Empresa Discográfica

---

#### 📋 Descripción
Una empresa discográfica necesita modelar los datos sobre sus diferentes recursos según las siguientes características:
* **Manager:** De cada mánager se almacena un identificador de manager y su nombre. Un manager representa a una serie de artistas.
* **Artista:** Un artista es representado por un manager. De los artistas se almacena su nombre completo (usando un único atributo) y su NIF.
* **Evento de promoción:** Los artistas participan en eventos de promoción para dar a conocer sus trabajos. En un evento de promoción pueden participar varios artistas. De un evento se almacena un identificador único, la fecha de celebración y el número de asistentes.

#### 🔑 Entidades y Atributos

| 📦 Entidad | 🏷️ Atributos | 🔑 Clave Primaria |
| :--- | :--- | :--- |
| **Manager** | Identificador, Nombre | Identificador |
| **Artista** | Nombre_Completo, NIF | NIF |
| **Evento** | Identificador_Unico, Fecha_Celebracion, Num_Asistentes | Identificador_Unico |

#### 🗂️ Diagrama conceptual
```
+---------+       1              N       +---------+       N              M       +--------+
| Manager | ----- < Representa > ----- | Artista | ----- < Participa > ----- | Evento |
+---------+                              +---------+                              +--------+
```

#### 🗂️ Diagrama conceptual a mano
<img width="885" height="265" alt="image" src="https://github.com/user-attachments/assets/7b3f8a0a-4978-4229-8b51-d1370679d906" />

---

💡Desea regresar? [🔙](README.md)
