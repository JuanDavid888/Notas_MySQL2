# **Triggers**

## **¿Qué son?**

Un trigger (o _disparador_) es un objeto de la base de datos que se ejecuta automáticamente en respuesta a ciertos eventos que ocurren sobre una tabla específica. Es un conjunto de instrucciones SQL que se ejecutan antes o después de una operación de modificación en la base de datos (como `INSERT`, `UPDATE`, `DELETE`).

## **Importancia**

- Validar que los datos que se insertan o actualizan cumplan ciertas reglas (_ejemplo:_ cantidades no negativas).
- Mantener integridad referencial o de negocio más compleja que las restricciones normales.
- Registrar cambios para auditoría y seguimiento.
- Actualizar otras tablas relacionadas automáticamente.
- Impedir operaciones no deseadas lanzando errores.

## **Diferencia entre BEFORE y AFTER**

- **BEFORE:** Se ejecuta antes de que la operación (`INSERT`, `UPDATE`, `DELETE`) se realice.
    - Permite validar o modificar datos.
    - Puede detener la operación si lanza un error.
- **AFTER:** Se ejecuta después de que la operación se complete.
    - No puede modificar los datos afectados.
    - Se usa para acciones como auditoría o notificaciones.

### ***Ejemplo práctico***

- **BEFORE INSERT:** Validar que el campo `cantidad` sea mayor o igual a 1 antes de insertar.
- **AFTER INSERT:** Insertar un registro en la tabla de auditoría indicando que se insertó un nuevo registro.


### **_Estructura base_**

```sql
CREATE TRIGGER nombre_del_trigger
{BEFORE | AFTER} {INSERT | UPDATE | DELETE}
ON nombre_de_la_tabla
FOR EACH ROW
BEGIN
-- cuerpo del trigger
END;
```

### **Comandos de triggers**

#### **_Crear triggers_**

Para crear un trigger, se usa el siguiente comando:

```sql
DELIMITER $$

DROP TRIGGER IF EXISTS nombre_trigger $$

CREATE TRIGGER nombre_trigger
{BEFORE | AFTER} {INSERT | UPDATE | DELETE}
ON nombre_tabla
FOR EACH ROW
BEGIN
-- cuerpo del trigger

END$$

DELIMITER ;
```

#### **_Eliminar triggers_**

Para eliminar un trigger, se usa el siguiente comando:

```sql
DROP TRIGGER IF EXISTS nombre_trigger;
```

#### **_Revisar triggers_**

Para revisar los triggers existentes, se usan los siguientes comandos:

**1.** Muestra los triggers existentes asociados a una tabla.

```sql
SELECT TRIGGER_NAME
FROM information_schema.TRIGGERS
WHERE EVENT_OBJECT_TABLE = 'nombre_tabla';
```
**2.** Muestra los triggers existentes asociados a una tabla y su momento de ejecución.

```sql
SELECT
	TRIGGER_NAME,
	ACTION_TIMING AS Momento,
	EVENT_MANIPULATION AS Evento
FROM information_schema.TRIGGERS
WHERE EVENT_OBJECT_TABLE = 'nombre_tabla';
```