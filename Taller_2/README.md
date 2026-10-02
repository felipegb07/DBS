# Taller 2 bases de datos - Introducción a SQL
Este taller tiene la finalidad de proporcionar los conocimientos básicos de SQL, de tal manera que estos puedan ser implementados en las diferentes bases de datos que serán posteriormente utilizadas.

Este taller consiste en hacer uso de la base de datos *university* en donde se pueden generar diferentes asociaciones teniendo en cuenta los elementos que se usen.

Se recomienda realizar la instalción teniendo en cuenta los pasos de la página web, de tal manera que **NO** se haga la instalación de paquetes mediante *snap* ya que este presenta erores en las rutas de las librerías.

## Instalación de la base de datos
Se hace la creación de un usuario mediante los comandos de.
```sql
create user nombreUsuario with password 'contraseña';
```

Esto se hace de tal manera que se evita hacer uso del usuario por defecto que se encuentra en psql que es postgre, de tal forma que al momento de hacer la creación de una base de datos, el owner de la misma pueda ser el usuario que modifica las tablas.

```sql
create database nombreBaseDeDatos owner nombreUsuario;
```

Al momento que hacemos la creación de la base de datos, debemos tener en cuenta que como ya estamos dentro de la base de datos, no debemos generar un accesos como si estuviesemos por fuera sino que se hace mediante `\c nombreBaseDeDatos`.

| **Fuera** | **Dentro** |
| --- | --- |
| `psql -u usuario -d nombreBaseDeDatos` | `\c nombreBaseDeDatos` |

Con esto en mente, podemos generar el acceso a nuestra base de datos mediante comandos.  
