# **Usuarios y Seguridad**

## **Importancia**

En la administración de bases de datos MySQL, la seguridad y la gestión de permisos son esenciales para proteger la información sensible, permitiendo solo a usuarios autorizados realizar operaciones específicas. Esto salvaguarda los datos contra accesos no autorizados, mantiene la integridad y optimiza el rendimiento de la base de datos.

## **Usuarios**

**MySQL, durante su instalación, crea varios usuarios por defecto, cada uno con un conjunto específico de permisos y roles los más destacados son:**

- **Usuario 'root':** Es el superusuario que tiene acceso total a todas las bases de datos y tablas. Es esencial para tareas administrativas.
- **Usuario Anónimo:** Por defecto, MySQL incluye un usuario anónimo, accesible sin nombre de usuario ni contraseña. Generalmente, tiene permisos limitados y se recomienda eliminarlo por razones de seguridad.

## **Cómo crear usuarios**

Se usa el siguiente comando:

```sql
CREATE USER 'usuarioEjemplo'@'localhost' IDENTIFIED BY 'contraseñaSegura';
```

## **Permisos**

Los permisos deben asignarse con cuidado, ya que representan un control o acceso a la información en la base de datos o parte de ella. Dependiendo el usuario con un rol, se asignan ciertos permisos a cada tabla, columna y demás elementos.

### *_Tipos de permisos_*

- **SELECT:** Permite acceder a los datos de una tabla.
- **INSERT:** Permite insertar datos en una tabla.
- **UPDATE:** Permite actualizar datos en una tabla.
- **DELETE:** Permite eliminar datos de una tabla.
- **CREATE:** Permite crear tablas, vistas, procedimientos almacenados y funciones.
- **DROP:** Permite eliminar tablas, vistas, procedimientos almacenados y funciones.
- **ALTER:** Permite modificar tablas, vistas, procedimientos almacenados y funciones.
- **INDEX:** Permite crear índices en una tabla.
- **CREATE TEMPORARY TABLES:** Permite crear tablas temporales.
- **REFERENCES:** Permite crear referencias entre tablas.

### *_Ejemplo de permisos_*

```sql
GRANT SELECT, INSERT, UPDATE, DELETE ON base_datos TO 'usuario'@'localhost';
```

### **Explicación de los permisos**

Para poder acceder a una tabla, es necesario primero seleccionar que acciones puede ejecutar el usuario, despues en que base de datos, posteriormente si lo desea, con un '.' después de la base de datos (base.tabla) puede dar permisos exclusivos a esa tabla.

```sql
GRANT SELECT, INSERT, UPDATE, DELETE ON base_datos.tabla TO 'usuario'@'localhost';
```

### **Comandos con los usuarios**

### **_Creación de usuarios_**

Para crear un usuario, se usa el siguiente comando:

```sql
CREATE USER 'nombre'@'localhost' IDENTIFIED BY 'contraseña';
-- Plugin => sistema para cifrar en el servidor las contrasenas
-- Se esta creando un Plugin - Default => caching_sha2_password
```

```sql
CREATE USER 'nombre'@'localhost'  IDENTIFIED WITH sha256_password BY 'contraseña';
-- Este plugin es usado para certificado sl, mas vulnerable, sin cache
```

### **_Revisar usuarios_**

Para revisar los usuarios existentes junto al tipo de host y plugin, se usa el siguiente comando:

```sql
SELECT user, host, plugin FROM mysql.user;
```

### **_Eliminar usuarios_**

Para eliminar un usuario, se usa el siguiente comando:

```sql
DROP USER 'nombre'@'localhost';
```

### **_Revisar permisos de usuarios_**

Para revisar los permisos de un usuario, se usa el siguiente comando:

```sql
SHOW GRANTS FOR 'nombre'@'localhost';
```

### **_Agregar permisos a usuarios_**

Para agregar permisos a un usuario, se usa el siguiente comando:

**1.** Para dar acceso completo a una base de datos:

```sql
GRANT ALL PRIVILEGES ON . FROM 'nombre'@'localhost';
```

**2.** Para dar acceso a una tabla:

```sql
GRANT SELECT, UPDATE ON base_datos.tabla TO 'nombre'@'localhost';
```

### **_Eliminar permisos de usuarios_**

Para eliminar permisos de un usuario, se usa el siguiente comando:

**1.** Para eliminar todos los permisos de una base de datos:

```sql
REVOKE ALL PRIVILEGES ON base_datos.* FROM 'nombre'@'localhost';
```

**2.** Para eliminar ciertos permisos de una tabla:

```sql
REVOKE INSERT ON base_datos.* FROM 'usuario'@'localhost';
```

### **_Refrescar permisos_**

Para refrescar los permisos de un usuario, se usa el siguiente comando:

```sql
FLUSH PRIVILEGES;
```