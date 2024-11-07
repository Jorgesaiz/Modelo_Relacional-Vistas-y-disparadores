# Modelo_Relacional-Vistas-y-disparadores

## Integrantes del grupo

### Jaime Alexander Sendín
### Jorge Saiz

# Actividad 1: Restauración de la base de datos `alquilerdvd`

## Objetivo

El objetivo de esta actividad es realizar la restauración de la base de datos contenida en el archivo `alquilerdvd.tar`. Este archivo contiene la estructura y los datos necesarios para simular el escenario de una tienda de alquiler de DVDs, como se describe en el proyecto. A través de este proceso, se familiariza uno con la restauración de bases de datos en PostgreSQL utilizando el comando `pg_restore`.

## Pasos Realizados

### 1. Preparación del entorno

Antes de comenzar con la restauración, es necesario asegurarse de que PostgreSQL esté instalado y funcionando correctamente en el sistema. También es necesario tener acceso al cliente de línea de comandos `psql`.

### 2. Creación de la base de datos vacía

Para restaurar los datos desde el archivo `.tar`, primero debemos crear una base de datos vacía donde se cargarán los datos. Esto se logra con el siguiente comando SQL:

```sql
CREATE DATABASE alquilerdvd;
```

### 3. Restauración desde el archivo `.tar`

El archivo `.tar` contiene la estructura y los datos. Una vez que la base de datos vacía ha sido creada, el siguiente paso es usar `pg_restore` para cargar la estructura y los datos contenidos en el archivo `.tar` en la base de datos que creamos.

Ejecutamos el siguiente comando, reemplazando `username` con el nombre de usuario correspondiente y `path/to/alquilerdvd.tar` con la ruta donde se encuentra el archivo `.tar`:

```bash
pg_restore -U username -d alquilerdvd -1 path/to/alquilerdvd.tar
```

### 4. Verificación de la restauración

Una vez completada la restauración de la base de datos, es importante verificar que la base de datos se haya restaurado correctamente. Para ello, seguimos estos pasos:

#### 1. Conección a la base de datos

Para empezar, nos conectamos a la base de datos restaurada utilizando `psql`, el cliente de línea de comandos de PostgreSQL. Ejecutamos el siguiente comando, reemplazando `username` con el nombre de usuario de PostgreSQL:

```bash
psql -U username -d alquilerdvd
```
#### 2. Listar las tablas

Una vez dentro de la sesión de psql, listamos todas las tablas disponibles en la base de datos restaurada con el siguiente comando:

```sql
\dt
```

Este comando mostrará una lista de todas las tablas que han sido restauradas desde el archivo .tar. Si todas las tablas esperadas están presentes, significa que la restauración se ha realizado correctamente.

#### 3. Verificar los datos restaurados

Para asegurarnos de que los datos han sido restaurados correctamente, ejecutamos una consulta simple sobre cualquier tabla de la base de datos. Por ejemplo, para ver algunas filas de una tabla específica, ejecutamos:

```sql
SELECT * FROM nombre_de_la_tabla LIMIT 10;
```

Reemplazamos nombre_de_la_tabla con el nombre real de una tabla en la base de datos. Este comando nos mostrará las primeras 10 filas de la tabla seleccionada, lo que permitirá verificar (de primeras) que los datos están presentes y correctamente restaurados.

