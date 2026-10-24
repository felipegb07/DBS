# Taller 4 (Introducción a vistas en las bases de datos)
Se hace un proceso de exploración de tal manera que se gener auna intrducción mediante las vistas en SQL, de tal manera que nos permite hacer que la base de datos pueda simplificarse los elemento en las bases de datos.

---

## Partes del taller
1. Práctica haciendo uso de W3Schools.
2. Vistas en SQL teniendo en cuenta el manejo de roles, tal que se tenga mayor seguridad.
3. Ejercicios.

### W3Schools
Los elementos presentes son los necesarios para poder hacer el taller de manera concluyente.

#### Create DB
```SQL
create database nombre_base_de_datos;
```

#### Drop DB
```SQL
drop database nombre_base_de_datos;
```

#### Create table
```SQL
create table nombre (
    atr type constainst
    ...
);
```

#### Drop table
```SQL
drop table if exist nombre_tabla;
```

#### Truncate table
Elimina todas las tuplas pero mantiene la tabla con las restricciones y atributos.
```SQL
truncate table nombre_tabla;
```

#### Alter table
Funciona de tal manera que nos permite modificar los atributos de una tabla.

##### Add
```SQL
alter table nombre_tabla
add atr type constraints;
```

##### Drop
```SQL
alter table nombre_tabla
drop column atr;
```

##### Rename
```SQL
alter table nombre_tabla
rename column atr_viejo to atr_nuevo;
```

##### Modify
Modifica el tipo de dato.
```SQL
alter table nombre_tabl
modify atr new_type constaints;
```

##### Adición de restricciones
```SQL
alter table nombre_tabla
add constraint nombre_restriccion constraints;
```

##### Restricciones mediante check
``` SQL
alter table nombre_tabla
add constaint nombre_Restriccion check (P);
```

#### Constraints o restricciones
Se hacen al momento de crear la tabla o al momento de hacer cualquier modificación.

##### Not null
**Creación de una tabla**
```SQL
create table nombre (
    atr type not null;
    ... not null
);
```

**Modificación de una tabla**
```SQL
alter table nombre
modify atr type not null;
```
##### Unique
Se hace uso de este al momento de hacer la creación de la tabla, haciendo que no se puedan tener valores repetidos en el atributo.

**Creación de tablas**
```SQL
create table nombre (
    atr1 type constaints,
    atr2 type constaints,
    constaint nombre unique (atr1, atr2) 
);
```
Con esto mostrará un código de error mostrando el nombre de la restricción y donde está.

**Modificación de tablas**
```SQL
alter table nombre
add unique (atr);
```

##### Primary key
**Creación de tablas**
```SQL
create table nombre (
    atr1 type primary key,
    atr2 type not null,
    constraint name constraint_type (atr)
);
```

**Incluir teniendo en cuenta los constraints**
```SQL
alter table nombe
add constraint nombre_restrcción primary key (atr1);
```
##### Foreing key
Se hace la creación de las tablas teniendo en cuenta las referencias hacia las otras tablas.

```SQL
create table nombre (
    atr1 type constraint,
    atr2 type constraint,
    constraint nombre foreign key (atr1) references (tabla1, tabla2)
);
```

##### Check
Funciona de tal manera que podamos hacer un predicado para hacer el filtro teniendo en cuenta una restricción.

```SQL
create table nombre (
    atr1 type const,
    atr2 type const,
    constraint nombre 
);
