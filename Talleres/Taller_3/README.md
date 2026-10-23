# Una introducción a las bases de datos
Este laboratorio tiene la finalidad de hacer la implementación de la base de datos *superHero database* de tal manera que podemos hacer uso de las diferentes variantes que se presentan en el *join*.

- Se hace la implementación de las diferentes bases de datos mediante SQL.
- Se analizan los diferentes elementos los cuales permiten hacer una busqueda mediante las caracteristicas de los superHeroes.

Se busca hacer la implementación de diferentes elementos en la página de w3Schools, de tal manera que se realizarán los 15 ejercicios que se tienen, de tal manera que se pueda tener un aprendizaje de los diferentes **JOIN** y las funciones nulas.

## Instalación de postgresql
Se hace la instalación de postgreSQL, de tal manera que como estoy haciendo uso de Linux, se hace la instalación mediante terminal teniendo en cuenta el siguiente comando.
```bash
apt install postgresql
```

Luego se procede a hacer la configuración de los elementos como lo indica la página de instalación de SQL, al momento de hacer la implementación de los comandos estoy haciendo uso de la distribución proporcionada por Ubuntu, de tal manera que se busca hacer la configuración automática mediante los siguientes comandos.
```bash
sudo apt install -y postgresql-common
sudo /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh
```

Al momento que hacemos la instalación de los diferentes elementos, algo que debemos tener en cuenta es que se para poder tener acceso a las bases de datos, debemos saber que se asigna un usuario de manera automática, de tal manera que debemos hacer uso del siguiente comando para poder tener acceso a las bases de datos presentes en postgre.

```bash
sudo -u postgres psql
```

Al momento que se hace la asignación del usuario, debemos tener en cuenta que al momento que hacemos la implementación de la base de datos con nuestro usuario llamado **postgres** este no tendrá contraseña, haciendo que podamos tener el acceso a este sin hacer uso de la misma.

### Cambio de la contraseña en caso de ser necesario
```bash
sudo -u postgres psql
alter user postgres with password 'contraseña que se quiera colocar al usuario';
```

### Administración mediante interfáz gráfica
Cuando hacemos el acceso de los diferentes elementos, algo que debemos tenern en cuenta es que podemos hacer la instalación de diferentes interfaces gráficas, de tal manera que haremos uso de *pgadmin* mediante el comando de instalación.

Como estoy haciendo uso de ubuntu, simplemente hice la instalación mediante snap, de tal manera que se puede tener acceso a los diferentes paquetes que ofrece canonical en su tienda sin necesidad de hacer toda la instalación y configuración mediante curl y diferentes instaladores. Se hace la instalación mediante la versión 18 de pgAdmin, de tal manera que se cuenta con versiones que soportan diferentes tipos de datos los cuales pueden servir de tal manera que tengamos la recepción de diferentes elementos al momento de hacer operaciones en la base de datos.

Lo que nos permitirá esto, es generar diferentes administraciones de las bases de datos teniendo en cuenta que estamos haciendo uso de las mismas en el GNU de linux.

## Implementación de la base de datos
Esta base de datos se importa desde el sitio web https://www.databasestar.com/.

### Estructura de la base de datos teniendo en cuenta el diagrama
!(Estructura base de datos)[Imagenes/EstructuraBase.png]

### Descarga base de datos
Se hace la implementación de la base de datos teniendo en cuenta que se hará mediante el link de **databasestar.com** https://www.databasestar.com/sample-database-superheroes/ . En esta se podrán encontrar elementos como.
- Diagrama entidad relación.
- Explicación de de las tablas y las columnas.
- Una descarga para los elementos de la base de datos.
- Un ejemplo de una consulta en la base de datos.

### Explicación de la base de datos
- superhero(name, full name/real name, IDs, height{cm}, weight{kg}).
- gender(male, female)
