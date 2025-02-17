---
title: Tablespaces en Oracle
published: true
---

### [](#header-3)Concepto sobre tablespaces

Los Espacios de Tablas o Tablespaces permiten agrupar lógicamente los datafiles o archivos de datos donde se almacenan físicamente los datos de las tablas de usuarios y del sistema. Oracle en todas sus ediciones cuenta por defecto con 5 tablespaces:

*   SYSAUX
*   SYSTEM
*   UNDO
*   TEMP
*   USERS

### [](#header-3)Funciones tablespaces default

| Tablespace        | Descripción           |
|:------------------|:----------------------|
| SYSTEM            | Este es el tablespace principal de la base de datos, que almacena el diccionario de datos y los objetos del sistema.|
| SYSAUX            | Este tablespace almacena objetos de la base de datos que no son críticos para el funcionamiento del sistema, pero que son necesarios para algunas funcionalidades de Oracle Database.|
| TEMP              | Este tablespace se utiliza para almacenar datos temporales generados durante la ejecución de consultas y otras operaciones en la base de datos.|
| UNDO              | Este tablespace se utiliza para almacenar información de deshacer para las transacciones que se están realizando actualmente.|
| USERS             | Este tablespace se utiliza para almacenar los objetos de usuario, es decir, aquellos objetos creados por los usuarios de la base de datos, como tablas, índices, vistas, etc.|

Crear tablespaces adicionales ayuda a organizar las  aplicaciones que se crean en base a esquemas, por ejemplo, podemos crear un tablespace que contengan esquemas para desarrollo, o también, podemos crear un tablespace por cada aplicativo a desarrollar.

### [](#header-3)Creacion de tablespaces

Para crear un tablespace se emplea el comando CREATE TABLESPACE, su sintaxis básica es:

```sql
CREATE TABLESPACE nombre_tablespace
DATAFILE 'ruta/datafile01.dbf' SIZE 100M
[AUTOEXTEND ON|OFF [NEXT 10M] [MAXSIZE 200M]]
[ONLINE | OFFLINE];
```

Para comprobar la creacion de nuestro tablespace usamos las vistas:

*   V$TABLESPACE
*   DBA_TABLESPACE

### [](#header-3)Ejemplos

*   Ejemplo 1:

Crear tablespace TBSPRUEBA1 con los siguientes parametros:

*   Tamaño inicial del datafile de 20M
*   Autoextendido Encendido
*   Saltos de 10MB  
*   Tamaño maximo de 50MB

```sql
CREATE TABLESPACE TBSPRUEBA1
DATAFILE 'ruta/datafile01.dbf' SIZE 20M
AUTOEXTEND ON
NEXT 10M
MAXSIZE 50M;
```

*   Ejemplo 2:

Crear tablespace TBSPRUEBA2 con los siguientes parametros:

*   Tamaño inicial de los datafiles 10MB (3 datafiles)
*   Autoextendido apagado

```sql
CREATE TABLESPACE TBSPRUEBA2
DATAFILE 'C:\datafiles\TBSDATAFILE02.DBF' SIZE 10M,
         'C:\datafiles\TBSDATAFILE03.DBF' SIZE 10M,
         'C:\datafiles\TBSDATAFILE04.DBF' SIZE 10M
AUTOEXTEND OFF;
```
### [](#header-3)Ejercicios

*   Ejercicio 1:

Crear tablespace TBSPRUEBA3 con los siguientes parametros:

*   Tamaño inicial del datafile de 50MB
*   Autoextendido Encendido
*   Saltos de 5MB
*   Tamaño maximo de 100MB

*   Ejercicio 2:

Crear tablespace TBSPRUEBA4 con los siguientes parametros:

*   Tamaño inicial de los datafiles de 15MB (3 datafiles)
*   Autoextendido apagado

