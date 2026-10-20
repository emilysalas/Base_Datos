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

---

💡Desea regresar? [🔙](README.md)
