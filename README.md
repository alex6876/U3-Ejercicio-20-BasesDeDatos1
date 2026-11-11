# Modelo Relacional de Bases de Datos 20



## Descripción



Este documento detalla el esquema y la estructura del modelo relacional de bases de datos para un sistema de gestión de espacios de trabajo compartido o coworking, enfocado en el control de miembros, control de acceso por tarjetas RFID, consumos, espacios de trabajo y reservas.

---

## Estructura de Tablas y Atributos



### 1. Miembro



* **PK (Clave Primaria Compuesta):** `id_DNI`, `Id_tarjeta RFID`


* **Atributos:**
* `nombre`


* `Empresa`


* `correo electronico`





### 2. Consumo



* **PK (Clave Primaria):** `id_consumo`


* **Atributos:**
* `fecha`


* `descripción`


* `cantidad`


* `costo`




* **FK (Claves Foráneas):**
* `id_DNI` (asociado a la tabla Miembro)





### 3. Control-de-Acceso



* **PK (Clave Primaria):** `id_fichaje`


* **Atributos:**
* `fecha y hora`


* `sentido del movimiento`




* **FK (Claves Foráneas):**
* `id_tarjeta RFID` (asociado a la tabla Miembro)





### 4. Espacio-Trabajo



* **PK (Clave Primaria):** `id_Codigo espacio`


* **Atributos:**
* `nombre`


* `tipo_de_espacio`


* `capacidad_maxima`


* `tarifa_x_hora`


* `tarifa_por_joranada` (o `tarifa_por_jornada`)





### 5. Reserva



* **PK (Clave Primaria):** `id_reserva`


* **Atributos:**
* `fecha de uso`


* `hora_de_inicio`


* `dias`


* `hora_de_fin`




* **FK (Claves Foráneas):**
* `id_Codigo_espacio` (asociado a la tabla Espacio-Trabajo)


* `id_DNI` (asociado a la tabla Miembro)





---

## Relaciones Principales



* **Miembro y Consumo:** Un miembro del coworking puede registrar múltiples consumos de cafetería u otros servicios asociados a su identificador (`id_DNI`).


* **Miembro y Control-de-Acceso:** Los fichajes de entrada y salida mediante tarjetas RFID se vinculan al perfil del miembro a través de `id_tarjeta RFID`.


* **Miembro y Espacio-Trabajo (Reserva):** Los miembros realizan reservas de los diferentes espacios de trabajo disponibles, vinculando la tabla `Reserva` mediante `id_DNI` e `id_Codigo_espacio`.
