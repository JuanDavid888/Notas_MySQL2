# **Consultas**

Las consultas son una forma de traer cierta información que se encuentra en una base de datos, de hace principalmente para averiguar información específica de una tabla, información que depende de varios campos o de otras tablas, etc.

## **Consultas Básicas**

Una consulta básica, sirve para traer datos primarios o comúnes que tienen ciertas tablas, pero que con ciertas condiciones o restricciones ayuda a tener un resultado más específico.

### *_Estructura de una Consulta Básica_*

```sql
SELECT columnas
FROM tabla
WHERE condiciones;
```

#### _Ejemplo_

```sql
SELECT nombre, apellido
FROM clientes
WHERE sexo = 'Masculino';
```

### **Consultas con JOIN**

La consulta con JOIN son consultas que se realizan a partir de dos o más tablas, por eso su nombres (Unir), son útiles para taer datos que estén en esas tablas elegidas, pero que hay que tener en cuenta que quieres traer.

#### *_Estructura de una Consulta con JOIN_*

```sql
SELECT columnas
FROM tabla1
JOIN tabla2
ON condiciones;
```

#### _Ejemplo_

```sql
SELECT nombre, apellido, salario
FROM clientes
JOIN trabajos
ON clientes.cargo = trabajos.nombre; -- cargo es el equivalente a nombre en trabajos
```

### **Procedimientos Almacenados**

Un procedimiento almacenado es un conjunto de instrucciones SQL que se guardan en la base de datos y se pueden ejecutar cuando sea necesario. Estos procedimientos pueden contener múltiples consultas SQL y lógica condicional.

#### **_Características:_**

- **Reutilización:** Pueden ser reutilizados en cualquier parte de la aplicación o por otros procedimientos.
- **Lógica compleja:** Pueden incluir lógica de control (condicionales, bucles, etc.), lo que permite realizar operaciones más complejas dentro de la base de datos.
- **Rendimiento:** Al estar precompilados, pueden ejecutarse más rápido que una consulta normal, especialmente si la consulta es compleja.
- **Seguridad:** Permiten establecer permisos de acceso más granulares; los usuarios pueden ejecutar un procedimiento sin darles acceso directo a las tablas subyacentes.
- **Parámetros:** Los procedimientos almacenados pueden aceptar parámetros, lo que los hace más dinámicos y reutilizables.

#### *_Estructura de un Procedimiento Almacenado_*

```sql
DELIMITER $$

DROP PROCEDURE IF EXISTS nombre_del_procedimiento;

CREATE PROCEDURE nombre_del_procedimiento(param1 tipo, param2 tipo)
BEGIN
    -- Instrucciones SQL aquí
END $$

DELIMITER ;
```

#### **_Ejemplo:_**

```sql
DELIMITER $$

DROP PROCEDURE IF EXISTS insertar_cliente;

CREATE PROCEDURE insertar_cliente(
    IN p_nombre VARCHAR(100),
    IN p_telefono VARCHAR(11),
    IN p_direccion VARCHAR(150)
)
BEGIN
    INSERT INTO cliente (nombre, telefono, direccion)
    VALUES (p_nombre, p_telefono, p_direccion);
END $$

DELIMITER ;
```

### *_Estrucura para llamar un Procedimiento Almacenado_*

```sql
CALL insertar_cliente(parámetros);
```