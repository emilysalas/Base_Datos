### 🏥 Ejemplo 3: Clínica Médica (Nivel Avanzado)

---

#### 📋 Descripción
Los pacientes solicitan citas; cada cita la atiende un médico a un paciente en fecha, hora y consultorio. De algunas citas se genera una receta que incluye medicamentos con dosis y duración. Cada médico pertenece a una especialidad.

#### 🗂️ Diagrama conceptual
```
+----------+       1       +---------+       N       +------+       1       +--------+
| Paciente | ------------- | Solicita| ------------- | Cita | ------------- | Médico |
+----------+               +---------+               +------+               +--------+
                                                        | 1                     | N
                                                        | Genera                |
                                                        v (0..1)                | 1
                                                   +---------+            +---------------+
                                                   | Receta  |            | Especialidad  |
                                                   +---------+            +---------------+
                                                        | 1
                                                        | Incluye
                                                        v N
                                                  +--------------+
                                                  | Medicamentos |
                                                  +--------------+
```
#### 🗂️ Diagrama conceptual a mano
<img width="959" height="394" alt="image" src="https://github.com/user-attachments/assets/db3cc48d-6768-4e36-8f1a-b55bfb36da5b" />

#### 🗂️ Modelo Relacional 
<img width="601" height="361" alt="image" src="https://github.com/user-attachments/assets/2625bd66-e4b5-46d7-920c-896a73e86092" />

#### 🗂️ Tabla SQL
```sql
CREATE TABLE paciente (
   id_paciente INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL
);
CREATE TABLE especialidad (
   id_especialidad INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL
);
CREATE TABLE medico (
   id_medico INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL,
   id_especialidad INT NOT NULL,
   FOREIGN KEY (id_especialidad) REFERENCES especialidad(id_especialidad)
);
CREATE TABLE medicamento (
   id_medicamento INT PRIMARY KEY,
   nombre VARCHAR(100) NOT NULL
);
CREATE TABLE cita (
   id_cita INT PRIMARY KEY,
   fecha DATE NOT NULL,
   hora TIME NOT NULL,
   consultorio VARCHAR(20) NOT NULL,
   id_paciente INT NOT NULL,
   id_medico INT NOT NULL,
   FOREIGN KEY (id_paciente) REFERENCES paciente(id_paciente),
   FOREIGN KEY (id_medico) REFERENCES medico(id_medico)
);
CREATE TABLE receta (
   id_receta INT PRIMARY KEY,
   id_cita INT NOT NULL UNIQUE,
   FOREIGN KEY (id_cita) REFERENCES cita(id_cita)
);
CREATE TABLE receta_medicamento (
   id_receta INT NOT NULL,
   id_medicamento INT NOT NULL,
   dosis VARCHAR(50) NOT NULL,
   duracion VARCHAR(50) NOT NULL,
   PRIMARY KEY (id_receta, id_medicamento),
   FOREIGN KEY (id_receta) REFERENCES receta(id_receta),
   FOREIGN KEY (id_medicamento) REFERENCES medicamento(id_medicamento)
);
```
---

💡Desea regresar? [🔙](README.md)
