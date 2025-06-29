# **Notas MySQL 2**

## **Introducción**

En este repositorio se puede encontrar diferentes comentarios, comandos y ejemplos de MySQL, usando el de referencia la documentación de las clases. Si desea ver el contenido propio de cada clase, puede ir directamente a los archivos o dar click en los enlaces de abajo.

## **Clases**

- [Clase 1: Normalización de datos](clases/Nomalizacion.md)

- [Clase 2: Consultas Básicas y avanzadas](clases/Consultas.md)

- [Clase 3: Funciones definidas y simples](clases/Funciones.md)

- [Clase 4: Usuarios y Seguridad](clases/Usuarios.md)

- [Clase 5: Eventos](clases/Eventos.md)

- [Clase 6: Triggers](clases/Triggers.md)

## **¿Qué es SQL?**

SQL (_Structured Query Language_) es un lenguaje de programación diseñado para gestionar y manipular bases de datos relacionales. Surgió en la década de 1970 y se ha convertido en el estándar en la administración de bases de datos.

### **Características**

1. **Lenguaje de consulta:** Permite realizar búsquedas y obtener datos precisos con sintaxis clara.
2. **Operaciones CRUD:** Facilita crear, leer, actualizar y eliminar datos en la base de datos.
3. **Gestión relacional:** Trabaja con tablas relacionadas y permite definir estructuras y restricciones.
4. **Consultas y filtrado:** Ofrece herramientas como `SELECT`, `WHERE`, `ORDER BY`, `GROUP BY` y funciones agregadas (`SUM`, `COUNT`, etc.).
5. **Funciones avanzadas:** Incluye operaciones matemáticas, de texto, fechas y transformaciones de datos.
6. **Seguridad:** Permite gestionar usuarios y permisos para proteger la base de datos.
7. **Transacciones:** Agrupa operaciones para asegurar su ejecución completa o su cancelación, con control de concurrencia para acceso simultáneo.

### **Componentes principales**

SQL (Structured Query Language) es un lenguaje de programación usado para gestionar bases de datos relacionales. Sus componentes principales se dividen en varias categorías:

**1. DDL (Data Definition Language)**

Define y administra la estructura de la base de datos:

- **CREATE:** Crea objetos como tablas o vistas.
- **ALTER:** Modifica objetos existentes.
- **DROP:** Elimina objetos.

**2. DML (Data Manipulation Language)**

Manipula los datos:

- **INSERT:** Agrega nuevos registros.
- **UPDATE:** Modifica datos existentes.
- **DELETE:** Elimina registros.

**3. DQL (Data Query Language)**

Consulta datos:

- **SELECT:** Recupera datos (es la principal instrucción DQL).

**4. DCL (Data Control Language)**

Administra permisos:

- **GRANT:** Otorga permisos.
- **REVOKE:** Revoca permisos.

**5. TCL (Transaction Control Language)**

Controla transacciones:

- **COMMIT:** Guarda cambios.
- **ROLLBACK:** Revierte cambios.
- **SAVEPOINT:** Marca puntos de recuperación dentro de una transacción.

---

**Cláusulas y Operadores Comunes**

- **WHERE:** Filtro de registros.
- **JOIN:** Combina datos de múltiples tablas.
- **GROUP BY / HAVING:** Agrupa y filtra grupos de datos.
- **ORDER BY:** Ordena resultados.

**Funciones en SQL**

- **Agregación:** COUNT, AVG, SUM, etc.
- **Fecha y hora:** CURRENT_DATE, CURRENT_TIME.
- **Cadenas:** CONCAT, SUBSTRING, LENGTH.

**Otros elementos**

- **Vistas:** Tablas virtuales basadas en consultas.
- **Índices:** Mejoran el rendimiento de búsqueda.
- **Triggers:** Ejecutan acciones automáticas ante ciertos eventos.

## **¿Qué es MySQL?**

MySQL es un sistema de gestión de bases de datos relacional (_RDBMS_) basado en el lenguaje SQL (_Structured Query Language_), que permite almacenar, organizar y recuperar datos de forma eficiente.

### **Indíces**

Los índices en MySQL son estructuras de datos que mejoran la velocidad de las operaciones de consulta (`SELECT`) al permitir un acceso más rápido a los datos.

**_¿Cuándo se usan?_**

- Para filtrar datos.
- Para agrupar datos.
- Para ordenar datos.
- Para optimizar la consulta.

**Estructura de un índice**

```sql
CREATE TABLE clientes (
    id INT NOT NULL PRIMARY KEY,
    nombre DATE,
    direccion VARCHAR(100),
    telefono VARCHAR(50),
    sexo ENUM('Masculino', 'Femenino'),
    INDEX (nombre, direccion) -- Elegimos los campos más buscados o importantes para consultar más rápido
);
```

### **Comandos básicos útiles**

Estos comandos van junto al uso de Docker

**1. Para crear un contenedor donde trabajar:**

```docker
docker run --name mysql_container -e MYSQL_ROOT_PASSWORD=admin -p 3307:3306 -d mysql:8.4
```

**Si el contenedor ya existe, se puede usar:**

```docker
docker start nombre_contenedor
```

**2. Para entrar a la consola del contenedor:**

```docker
docker exec -it mysql_container sh
```

**3. Para acceder a la consola de MySQL:**

```docker
mysql -uroot -padmin
```

**Explicación:**

- `-uroot`: Nombre de usuario.
- `-padmin`: Contraseña.

### **Comandos básicos dentro de MySQL**

**1. Ver bases de datos existentes:**

```sql
SHOW DATABASES;
```

**2. Crear una base de datos:**

```sql
CREATE DATABASE base_datos DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

**3. Usar la base de datos:**

```sql
USE base_datos;
```

**4. Ver tablas existentes:**

```sql
SHOW TABLES;
```

**5. Crear una tabla:**

```sql
CREATE TABLE tabla (
    campo1 INT,
    campo2 VARCHAR(100),
    campo3 DATE
);
```

**Estructura de un Check**

```sql
CREATE TABLE Empleados (
  Id INT PRIMARY KEY,
  Nombre VARCHAR(50),
  Apellido VARCHAR(50),
  Edad INT CHECK (Edad >= 18)
);
```

**6. Insertar datos:**

```sql
INSERT INTO tabla (campo1, campo2, campo3)
VALUES (1, 'Hola', '2022-01-01');
```

**7. Consultar datos:**

```sql
SELECT campo1, campo2, campo3
FROM tabla;
```

**8. Eliminar una tabla:**

```sql
DROP TABLE IF EXISTS tabla;
```

**9. Ver estructura de una tabla:**

- **1.** Opción 1:

    ```sql
    DESC tabla;
    ```

- **2.** Opción 2:

    ```sql
    SHOW CREATE TABLE tabla;
    ```

**10. Ver contenido de una tabla:**

```sql
SELECT * FROM tabla;
```

**11. Actualizar datos:**

```sql
UPDATE tabla
SET campo1 = 2
WHERE campo1 = 1;
```

**12. Eliminar datos:**

```sql
DELETE FROM tabla
WHERE campo1 = 1;
```

**13. Truncar tablas:**

```sql
TRUNCATE tabla;
```

**14. Ver llaves de una tabla:**

```sql
SHOW INDEX FROM tabla;
```

**15. Ver índices de una tabla:**

```sql
SHOW INDEX FROM tabla;
```

**16. Definir llaves foráneas:**

- **1.** Opción 1:

    ```sql
    ALTER TABLE tabla
    ADD FOREIGN KEY (campo1)
    REFERENCES tabla2 (campo2);
    ```

- **2.** Opción 2:

    ```sql
    CREATE TABLE tabla (
        campo1 INT,
        campo2 VARCHAR(100),
        campo3 DATE,
        FOREIGN KEY (campo1)
        REFERENCES tabla2 (campo2)
    );
    ```

**17. Eliminar llaves foráneas:**

```sql
ALTER TABLE tabla
DROP FOREIGN KEY campo1;
```

**18. Modificar tablas:**

```sql
ALTER TABLE tabla
MODIFY COLUMN nombre VARCHAR(200);
```

**19. Modificar nombre de una tabla:**

- **1.** Opción 1:

    ```sql
    ALTER TABLE tabla1  RENAME TO nueva_tabla1;
    ```

- **2.** Opción 2:

    ```sql
    RENAME TABLE nombre_actual TO nombre_nuevo;
    ```

**20. Modificar nommbre de una columna:**

- **1.** Opción 1:

    ```sql
    ALTER TABLE tabla RENAME COLUMN columna TO columna_nueva;
    ```

- **2.** Opción 2:

    ```sql
    ALTER TABLE tabla CHANGE columna columna_nueva tipo_de_dato;
    ```

**21. Agregar columnas:**

```sql
ALTER TABLE tabla
ADD COLUMN email VARCHAR(100) NOT NULL AFTER nombre;

FIRT | AFTER // sirve para seleccionar donde colocar esa columna
```

**22. Eliminar columnas:**

```sql
ALTER TABLE tabla DROP COLUMN columna;
```

## **Autor**

**Camper:** `Juan David Jaimes Miranda`