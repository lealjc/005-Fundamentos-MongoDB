# 005-Fundamentos-MongoDB
Básico/Introducción a Base de Datos/Fundamentos MongoDB/Postwork

<hr>
<b>Estos son las instrucciones que utilice para el Postwork de la sesión 5.</b>
<hr>

2. Copiar la carpeta Datos creada en el Sesion-02/Postwork/ y moverse a la carpeta Datos/

Postwork $ cp -a ../../Sesion-02/Postwork/Datos .
Postwork $ cd Datos
Datos $

Los datos se copiaron correctamente.

3. En MongoDB Compass crea una base de datos, preferentemente con el nombre de tu proyecto, como tienes que crear también una colección selecciona el nombre de algunos de los archivos CSV que desees importar.

Base de Datos => jcleal_Postwork
Archivos importados => estadis.csv y cat_ur.csv

4. En esta sesión se hará uso de los archivos en formato CSV que tengan una primera fila con el nombre de cada columna y por cada uno de ellos realizar el siguiente proceso:

-Analizar contenido del archivo

cat_ur.csv es un catálogo de delegaciones en las entidades federativas que incluye nombre largo, nombre corto y abreviatura.

estadis.csv es una tabla que contiene un id_ur para relacionarse con la tabla cat_ur, año, mes, ebdi, altas y bajas.


-Crear un Colección con el mismo nombre del archivo

Colección estadis

Colección cat_ur


-Importar datos a la Colección usando la opción de - - Import Data de MongoDB Compass

La colección cat_ur contiene: _id, id_ur, nombrel, nombrec, abrv

La colección estadis contiene: _id, ano, mes, id_ur, ebdi, altas, bajas


-Validar que los datos se hayan importado correctamente revisando que algunos de los documentos tengan la cantidad de campos correcta, nombre en cada uno de los 

campos y que el total de documentos sea el mismo que el total de filas en el archivos.

Archivos csv:

estadis = 240 registro

cat_ur = 35 registros


Colecciones:

estadis = 241 documentos

cat_ur = 36 documentos




-Revisar si hay documentos vacíos y en caso afirmativo eliminarlos

En la colección estadis, utlizando FILTER {ano: ""}, aparece el documento vacio. Lo eliminé.

En la colección cat_ur, utlizando FILTER {id_ur: ""}, aparece el documento vacio. Lo eliminé.

estadis = 240 documentos

cat_ur = 35 documentos




🏁 Meta 1:

Toma en cuenta que uno de tus objetivos es que logres contar con todo tu conjunto de datos importado en un Servidor MongoDB.

Comienza a realizar consultas a tus datos por medio de realizar filtrado de datos, respondiendo a preguntas como:

¿cuántos registros hay de cierto tipo o categoría?

{id_ur: "1"} / Resultado = 14; es correcto.

{altas: "3"} / Resultado = 1; es correcto.

{bajas: "0"} / Resultado = 224; es correcto.


¿cuántos registros hay de dos o más categorías?

{bajas: "0", altas: "0"} / Resultado = 206; es correcto.

{bajas: "0", altas: "0"} / Resultado = 206; es correcto.

{id_ur: "91", altas: "1"} / Resultado = 2; es correcto.


¿cuántos registros hay donde un campo sea mayor, menor o igual a cierto valor?

Igual =>

{id_ur: {$eq:"92"} } / Resultado = 9; es correcto.

Mayor =>

{id_ur: {$gt: 33} } / Resultado = 4; es correcto.

Menor =>

{id_ur: {$lt: 33} } / Resultado = 31; es correcto.

