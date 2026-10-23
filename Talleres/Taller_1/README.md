# Antes de empezar el taller
Al momento de hacer la implementación y descarga de los paquetes en el servidor de ubuntu v24.04, se debe hacer la creación de un entorno el cual nos permite hacer diferentes modificaciones sin modificar el sistema de archivos de python que tienen las distribuciones de linux nativas.

~~~bash
source nombre_entorno/bin/activate
~~~

Esto se hace con la finalidad de generar un espacio aislado y evitar conflictos de librerías. Haciendo que en caso tal de que necesitemos diferentes elementos de distintas librerías, podamos evitar conflictos de versiones entre las mismas.

Algo a tener en cuenta, es que al momento de hacer la instalación de miniconda, también debemos hacer la ejecución de un comando vía curl 

~~~bash
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
~~~

Estos comandos fueron guardados mediante un archivo .txt que fue ejecutado mediante bash, lo cual nos permite hacer lo siguiente.

~~~bash
bash nombre_archivo.txt
~~~

Lo que nos permite miniconda, es instalar de forma ligera python y su gestor de paquetes **Conda** para espacios de trabajo y entornos visuales aislados para instalar solo ls librerías necesarias sin saturar la memoria del computador.

## Elementos del taller
1. Se hace la descar de `applications.db` y su posterior ejecución mediante radb.
2. Se usa `\list;` para observar las relaciones de las bases de datos.

### Relaciones del taller
| Nombre tabla | Nombre relacion | Tipo de dato |
| --- | --- | --- |
| Apply | sID | number |
| - | cName | String |
| - | major | String |
| - | decision | String |
| College | cName | String |
| - | state | String |
| - | enrollment | number |
| Stundet | sID | number |
| - | sName | String | 
| - | GPA | number |
| sizeHS | number |
 


Podemos ver que en las diferentes tablas que tenemos, contamos con distintas cantidades de tuplas.

- Apply => 11 tuplas.
- College => 4 tuplas.
- Student => 5 tuplas.

Para las busquedas, debemos hacer uso de `\select_{condition} input_relation;`; para eso, se usa el operador de selección `σ`. Se hace el uso de diferentes relaciones, las cuales se ven regidas por la condición y el `imput_relation` que nos permite generar relaciones con los nombres de las tablas.

Al momento de realizar los test, lo que hacemos es generar condiciones al momento de realizar filtros, podemos ver que tendremos tuplas como solución que cumple la condición. Lo que podremos ver, es que se hace el retorno de todos los atributos con sus respectivos elementos

## Operadores
---
### Selección
Los ejemplos parten desde el principio simple del operador de selección, el cual nos permite ver qué relaciones se harán entre los diferentes elementos.

#### Estructura básica
`\select_{condiciones} nom_tabla;`

#### Ejemplos.
- σGAP >4.0∧sizeHS>2000 student.
`\select_{GAP > 4.0 and sizeHS > 2000} student;`

- σmajor=′ Sistemas′ ∧cN ame=′ P U J ′ apply.
`\select_{major = 'Sistemas' and cName = 'PUJ'} apply;`

### Proyección
El operador de proyección lo que hace es crear una nueva relación seleccionando atributos especificos de una relación existente. Esto lo que nos permitirá es mostrar solo los atributos que seleccionemos.

- Algo importante a tener en cuenta, es que los atributos se verán separados por `,`, de tal manera que si queremos listar varios atributos, tendremos que hacerlo de manera diferente al `and`.
#### Estructura básica
`project_{lista, atributos} nom_tabla;`

#### Ejemplo
-  Student ID and decision for all applications.
- ΠsID,decision apply.
`\project_{sID, decision} apply;`

- Muestra el sName, sID y GPA de los estudiantes que tengan un GPA mayor a 4.0.
`\proyect_{sName, sID, GPA}(\select_{GPA > 4.0} student);`

Podemos ver que la consulta anterior es compuesta, de tal manera que tenemos un paréntesis que define lo que haremos dentro de la busqueda con los elementos que hemos filtrado, haciendo que pueda ser más sencilla mientras que podamos entender la lógica de cada una de las partes.

### Producto cartesiano
El producto cartesiano lo que hace, es generar una suma de cada atributo en nuestra tabla_1 y sumarlo a cada atributo de nuestra tabla_2, de tal manera que cuando miremos los elementos, tendremos que se habrá hecho una suma de los atributos de cada tabla generando una completamente nueva.

#### Estructura básica
`tabla_1 \cross tabla_2;`

#### Ejemplo
- Find the Cartesian product between the students and the applications.
- student × apply.

`student \cross apply;`

Cuando hacemos la implementación de consultas compuestas, podemos ver que tendremos que emplear diferentes nombres para nuestras variables, tal que si tenemos dos tablas con un mismo nombre en su relación, tendremos que hacer uso de elementos que nos permitan reconocer esa llave foranea como lo son:
   
     - `tabla_1.var and tabla_2.var`

Podemos ver que aunque ambas cuentan con la misma variable, debemos hacer una distinción con el tipo de tabla del que estamos seleccionando los elementos, lo cual nos permitirá hacer que se haga un mejor filtro cuando hagamos busquedas de elementos entre tablas.

- Retorne el Nombre y GPA de los estudiantes que applicaron a Sistemas

`\project_{cName, GPA}(\select_{students.sID = apply.sID and apply.major = 'Sistemas'}(student \cross apply));`

### Union natural o simple
Lo que hará es que tomará todos atributos que tengan el mismo nombre de las relaciones entre tablas. También podemos ver que al momento de hacer las uniones mediante el `\join`, tendremos que se evitarán los repetidos, de tal forma que tengamos los elementos unidos mediante una misma variable con lsa tuplas relacionadas.

#### Ejemplo
- Nombre, Id y GPA de los los estudiantes que aplicaron a sistemas sin repetidos.

`proyect_{sName, sID, GPA}(\select_{apply.major = 'Sistemas'}(apply \join student));`

- Nombre, GPA y universidad de los estudiantes que aplicaron a 'MEdicina' en instituciones con un enrollment mayor a 2000

`\proyect_{sName, GPA, cName}(\select_{apply.cName = 'Medicina' and college.enrollment > 20000}(apply \join(college \join student)));`

### Union theta
Lo que hace este tipo de union, es generar una union de manera normal mediante `\join` pero se hace uso de una condición, de tal manera que tendremos una union condicionada por ciertos atributos los cuales pueden tener diferentes nombres.

#### Estructura básica
`tabla_1 \join{condición} tabla_2;`
 

## Sumario general
Al momento de hacer la implementación de consultas en más de una tabla, debemos hacer la especificación de las tablas mediante una asociación que puede ser `\join ó \cross` dependiendo de lo que necesitemos.

Para cada tipo de consulta independiente, debemos hacer uso de paréntesis, de tal manera que será resuelto de atrás hacia adelante, permitiendo que tengamos diferentes consultas en "linea", haciendo que en caso tal que solo tengamos una consulta la cual está en linea, pero no hacemos ninguna relación con otras tablas, será más simple de realizar y no tendremos que colocarla fuera del paréntesis primario.

`\proyect_{atr1, atr2}(\select_{condicion} tabla1);`

Se puede hacer la implementación de un formato multilinea, ya que al momento de hacer una consulta, no se figura como un resultado si no se tiene el `;`.
