# **Funciones**

## **Funciones definidas**

Las funciones definidas son conjuntos de instrucciones SQL que permiten realizar ciertas operaciones con la base de datos, ayudan a agrupar, organizar y filtrar datos.

### *_Ejemplos_*

```sql
-- Función que devuelve el número de registros de una tabla
SELECT COUNT(*) FROM clientes;

-- Función que devuelve el promedio de salarios de un cargo
SELECT AVG(salario) FROM clientes WHERE cargo = 'Director';

-- Función que devuelve la suma de salarios de un cargo
SELECT SUM(salario) FROM clientes WHERE cargo = 'Director';

-- Función que devuelve el máximo de salarios de un cargo
SELECT MAX(salario) FROM clientes WHERE cargo = 'Director';

-- Función que devuelve el mínimo de salarios de un cargo
SELECT MIN(salario) FROM clientes WHERE cargo = 'Director';
```

## **Tipos de funciones definidas**

### 1. **Funciones matemáticas**

**ABS(x)** – Valor absoluto

```sql
-- Devuelve el valor absoluto, sin importar si es positivo o negativo
SELECT ABS(-10); -- 10

SELECT ABS(10); -- 10
```

**CEIL(x) / CEILING(x)** – Redondea hacia arriba

```sql
-- Redondea hacia arriba
SELECT CEIL(10.5); -- 11
```

**FLOOR(x)** – Redondea hacia abajo

```sql
-- Redondea hacia abajo
SELECT FLOOR(10.5); -- 10
```

**ROUND(x, d)** – Redondea a d decimales

```sql
-- Redondea a dos decimales
SELECT ROUND(10.5, 2); -- 10.50

```

**MOD(x, y) / x % y** – Módulo (residuo de división)

```sql
-- Devuelve el módulo de dos números
SELECT MOD(10, 2); -- 0
```

**POWER(x, y) / POW(x, y)** – Potencia

```sql
-- Estructura del POWER()
SELECT POWER(base, exponente); 

-- Devuelve el cuadrado de dos números
SELECT POWER(2, 2); -- 4 (2 * 2)

SELECT POWER(2, 3); -- 8 (2 * 2 * 2)
```

**SQRT(x)** – Raíz cuadrada

```sql
-- Devuelve la raíz cuadrada
SELECT SQRT(4); -- 2
```

**RAND()** – Número aleatorio entre 0 y 1

```sql
-- Devuelve un número aleatorio entre 0 y 1
SELECT RAND(); -- 0.123456789

-- Devuelve un número aleatorio entre 0 y 10
SELECT RAND(10); -- 7
```

**TRUNCATE(x, d)** – Trunca a d decimales

```sql
-- Trunca a dos decimales
SELECT TRUNCATE(10.5, 2); -- 10.50

-- Trunca a dos decimales
SELECT TRUNCATE(10.556, 2); -- 10.55 (No redondea de por sí)
```

**SIGN(x)** – Devuelve -1, 0 o 1

```sql
-- Devuelve -1 si es negativo, 0 si es cero y 1 si es positivo
SELECT SIGN(-10); -- -1

SELECT SIGN(0); -- 0

SELECT SIGN(10); -- 1
```

### 2. **Funciones de fecha y hora**

**NOW()** – Fecha y hora actual

```sql
SELECT NOW(); -- 2025-01-01 10:00:00
```

**CURDATE()** – Fecha actual (Ahora)

```sql
SELECT CURDATE(); -- 2025-01-01
```

**CURTIME()** – Hora actual (Ahora)

```sql
SELECT CURTIME(); -- 10:00:00
```

**DATE()** – Extrae la parte de fecha

```sql
SELECT DATE('2025-01-01'); -- 2025-01-01
```

**TIME()** – Extrae la parte de hora

```sql
SELECT TIME('10:00:00'); -- 10:00:00
```

**YEAR(date) / MONTH(date) / DAY(date)** – Año, mes, día

```sql
-- Muestra el año de una fecha
SELECT YEAR('2025-01-01'); -- 2025

-- Muestra el mes de una fecha
SELECT MONTH('2025-01-01'); -- 1

-- Muestra el día de una fecha
SELECT DAY('2025-01-01'); -- 1
```

**HOUR() / MINUTE() / SECOND()** – Hora, minuto, segundo

```sql
-- Muestra la hora de una fecha
SELECT HOUR('10:00:00'); -- 10

-- Muestra el minuto de una fecha
SELECT MINUTE('10:00:00'); -- 00

-- Muestra el segundo de una fecha
SELECT SECOND('10:00:00'); -- 00
```

**DATEDIFF(d1, d2)** – Diferencia de días entre fechas

```sql
-- Muestra la diferencia de días entre dos fechas
SELECT DATEDIFF('2025-01-01', '2025-01-02'); -- 1
```

**DATE_ADD(date, INTERVAL x unit)** – Suma fechas

```sql
-- Muestra la fecha sumando un año a una fecha
SELECT DATE_ADD('2025-01-01', INTERVAL 1 YEAR); -- 2026-01-01
```

**DATE_SUB(date, INTERVAL x unit)** – Resta fechas

```sql
-- Muestra la fecha restando un año a una fecha
SELECT DATE_SUB('2025-01-01', INTERVAL 1 YEAR); -- 2024-01-01
```

### 3. **Funciones de cadenas (strings)**

**CONCAT(s1, s2, ...)** – Une cadenas

```sql
-- Concatena dos cadenas
SELECT CONCAT('Hello', 'World'); -- HelloWorld
```

**LENGTH(str)** – Longitud en bytes

```sql
-- Muestra la longitud en bytes
SELECT LENGTH('Joe'); -- 3

SELECT LENGTH('niño'); -- 5

``` 

**CHAR_LENGTH(str)** – Longitud en caracteres

```sql
-- Muestra la longitud en caracteres
SELECT CHAR_LENGTH('Joe'); -- 3

SELECT CHAR_LENGTH('niño'); -- 4
```

**LOWER(str) / UPPER(str)** – Minúsculas / Mayúsculas

```sql
-- Convierte la cadena a minúsculas
SELECT LOWER('Hello'); -- hello

-- Convierte la cadena a mayúsculas
SELECT UPPER('Hello'); -- HELLO
```

**LEFT(str, n) / RIGHT(str, n)** – N caracteres desde izquierda o derecha

```sql
-- Muestra los primeros cinco caracteres de una cadena
SELECT LEFT('Hello', 3); -- Hel

-- Muestra los últimos cinco caracteres de una cadena
SELECT RIGHT('Hello', 3); -- llo
```

**SUBSTRING(str, start, length)** – Subcadena

```sql
-- Muestra la subcadena de la cadena
SELECT SUBSTRING('Hello', 2, 3); -- llo
```

**TRIM(str)** – Elimina espacios al inicio/fin

```sql
-- Elimina todos los espacios
SELECT TRIM('  Hello  '); -- Hello

-- Elimina los espacios a la izquierda
SELECT LTRIM('  Hello'); -- Hello

-- Elimina los espacios a la derecha
SELECT RTRIM('Hello  '); -- Hello
```

**REPLACE(str, from, to)** – Reemplaza texto

```sql
-- Estructura del REPLACE()
SELECT REPLACE(texto_base, que_reemplazar, a_que_reemplazar);

-- Reemplaza el texto 'Hello' por 'Hola'
SELECT REPLACE('Hello', 'Hello', 'Hola'); -- Hola
```

**INSTR(str, substr)** – Posición de subcadena

```sql
-- Muestra la posición de la subcadena 'llo' en la cadena 'Hello'
SELECT INSTR('Hello', 'llo'); -- 3
```

**LOCATE(substr, str)** – Igual a INSTR

```sql
-- Igual a INSTR, pero permite usar parametro de inicio
SELECT LOCATE('llo', 'Hello'); -- 3

SELECT LOCATE('llo', 'Hello', 6); -- 0 (No encuentrado)
```

**REVERSE(str)** – Invierte la cadena

```sql
-- Invierte la cadena
SELECT REVERSE('Hello'); -- olleH
```

### 4. **Funciones de conversión y tipo**

**CAST(expr AS type)** – Convierte tipo de dato

```sql
-- Convierte una cadena a un número
SELECT CAST('10' AS INT); -- 10
```

**CONVERT(expr, type)** – Igual que CAST

```sql
-- Convierte una cadena a un número
SELECT CONVERT('10', INT); -- 10
```

**FORMAT(x, d)** – Número con comas, redondeado a d decimales

```sql
-- Devuelve el número con comas
SELECT FORMAT(10.5, 2); -- 10,50
```

### 5. **Funciones de control de flujo**

**IF(expr, true_val, false_val)** – Condicional tipo if

```sql
-- Devuelve el valor de true_val si expr es verdadera
SELECT IF(10 > 5, 'Mayor', 'Menor'); -- Mayor
```

**IFNULL(expr1, expr2)** – Devuelve expr2 si expr1 es NULL

```sql
-- Devuelve el valor de expr2 si expr1 es NULL
SELECT IFNULL(NULL, 'Valor'); -- Valor
```

**NULLIF(expr1, expr2)** – Devuelve NULL si ambos son iguales

```sql
-- Devuelve NULL si expr1 es igual a expr2
SELECT NULLIF(10, 10); -- NULL
```

**CASE WHEN ... THEN ... ELSE ... END** – Condicional múltiple

```sql
-- Devuelve el valor de true_val si expr es verdadera
SELECT CASE WHEN 10 > 5 THEN 'Mayor' ELSE 'Menor' END; -- Mayor
```
### 6. **Funciones de agregación (uso común con GROUP BY)**

**COUNT(*) / COUNT(col)** – Cuenta filas

```sql
-- Cuenta filas
SELECT COUNT(*) FROM clientes; -- 3
```
**SUM(col)** – Suma total

```sql
-- Suma total de salarios
SELECT SUM(salario) FROM clientes; -- 1000
```

**AVG(col)** – Promedio

```sql
-- Promedio de salarios
SELECT AVG(salario) FROM clientes; -- 500
```

**MIN(col) / MAX(col)** – Mínimo / Máximo

```sql
-- Mínimo de salarios
SELECT MIN(salario) FROM clientes; -- 100

-- Máximo de salarios
SELECT MAX(salario) FROM clientes; -- 1000
```
**GROUP_CONCAT(col)** – Une valores de grupo separados por comas

```sql
-- Concatena valores de grupo
SELECT GROUP_CONCAT(cargo) FROM clientes; -- Director,Director,Director
```
### 7. **Funciones lógicas y de comparación**

**ISNULL(expr)** – Devuelve 1 si es NULL

```sql
-- Devuelve 1 si es NULL
SELECT ISNULL(NULL); -- 1
```

**COALESCE(a, b, c, ...)** – Devuelve el primer valor no NULL

```sql
-- Devuelve el primer valor no NULL
SELECT COALESCE(NULL, 10, NULL); -- 10
```

**GREATEST(x1, x2, ...)** – El mayor de los valores

```sql
-- El mayor de los valores
SELECT GREATEST(10, 5, 2); -- 10
```

**LEAST(x1, x2, ...)** – El menor de los valores

```sql
-- El menor de los valores
SELECT LEAST(10, 5, 2); -- 2
```

## **Funciones Simples** 

Las funciones simples son operaciones rápidas y eficientes, las cuales pueden ser llamadas cuando sea, hechas para realizar una tarea específica, no están hechas para insertar, actualizar o eliminar datos, sino para realizar operaciones con los datos de la base de datos.

## *_Estructura de una Función_*

```sql
DELIMITER $$

DROP FUNCTION IF EXISTS nombre_funcion;

FUNCTION nombre_funcion(parámetros)
RETURNS tipo
BEGIN
    -- Instrucciones SQL aquí
END $$

DELIMITER ;
```

#### **_Ejemplo:_**

```sql
DELIMITER $$

DROP FUNCTION IF EXISTS sumar;

CREATE FUNCTION sumar(a INT, b INT)
RETURNS INT
BEGIN
    RETURN a + b;
END $$

DELIMITER ;
```

#### *_Estructura para llamar una Función_*

```sql
SELECT nombre_funcion(parámetros);
```