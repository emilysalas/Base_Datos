### 🎵 Ejercicio 7: Discos Musicales

---

#### 📋 Descripción
La tienda vende discos de diferentes géneros musicales y cantantes:
* **Género Musical:** Identificador, Nombre.
* **Disco:** Título, Género musical, Precio, Cantante.
* **Cantante:** Nombre, País. Todo disco pertenece a un cantante y un cantante puede tener muchos discos.
* **Canción:** Identificador, Título. Un disco tiene muchas canciones y una canción puede estar en varios discos. Interesa conocer la posición de una canción en un determinado disco.

#### 🔑 Entidades y Atributos

| 📦 Entidad | 🏷️ Atributos |
| :--- | :--- |
| **Disco** | Título, Precio, Genero_Musical, Cantante |
| **Género Musical** | ID_Genero_Musical, Nombre |
| **Cantante** | Nombre, País |
| **Canción** | ID_Cancion, Título |

#### 🗂️ Diagrama conceptual
```
                 +----------------+
                 | Género Musical |
                 +----------------+
                         | M
                     < Clasifica >
                         | N
+----------+     1    N  |  N        M    +---------+
| Cantante | ----- < Graba > ----- | Disco | ----- < Contiene > ----- | Canción |
+----------+                              +---------+ (Posición)       +---------+
```
#### 🗂️ Diagrama conceptual a mano
<img width="698" height="300" alt="image" src="https://github.com/user-attachments/assets/95929c98-7ea4-4eaf-84d3-6c2f895a7e59" />

---

💡Desea regresar? [🔙](README.md)
