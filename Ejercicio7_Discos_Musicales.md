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

#### 🗂️ Modelo Relacional 
<img width="601" height="254" alt="image" src="https://github.com/user-attachments/assets/4e9236f0-e74d-409d-b5d1-ae55d8064238" />


#### 🗂️ Tabla SQL
```sql
CREATE TABLE genero_musical (
   id_genero_musical INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL
);
CREATE TABLE cantante (
   id_cantante INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL,
   pais VARCHAR(60) NOT NULL
);
CREATE TABLE cancion (
   id_cancion INT PRIMARY KEY,
   titulo VARCHAR(150) NOT NULL
);
CREATE TABLE disco (
   id_disco INT PRIMARY KEY,
   titulo VARCHAR(150) NOT NULL,
   precio DECIMAL(10,2) NOT NULL,
   id_genero_musical INT NOT NULL,
   id_cantante INT NOT NULL,
   FOREIGN KEY (id_genero_musical) REFERENCES genero_musical(id_genero_musical),
   FOREIGN KEY (id_cantante) REFERENCES cantante(id_cantante)
);
CREATE TABLE disco_cancion (
   id_disco INT NOT NULL,
   id_cancion INT NOT NULL,
   posicion INT NOT NULL,
   PRIMARY KEY (id_disco, id_cancion),
   FOREIGN KEY (id_disco) REFERENCES disco(id_disco),
   FOREIGN KEY (id_cancion) REFERENCES cancion(id_cancion)
);


```
---

💡Desea regresar? [🔙](README.md)
