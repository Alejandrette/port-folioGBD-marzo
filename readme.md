# Resumen

En las consultas básicas hemos visto:
- **Select**: Es la que más hemos usado con diferencia, y sirve para sellecionar datos de una tabla
- **From**: es otro comando ligado a select, en el que le indicamos de que tabla debe consultar los datos
- **Where**: La usamos con fines de filtar los resultados de la consulta **SELECT** dependiendo de las condiciones que indiquemos
- **Distinct**: Nos elimina las filas que esten repetidas
- **Order by**: En el que podemos ordenar por las tablas, y si usamos **DESC** las ordenara de forma descendente
- **Atributos**: hemos decenas de atributos que pueden complementar a la consulta de **SELECT** y en que solo voy a destacar el: LIKE, UPPER, to_char,expresiones regulares (regexp_like, regexp_substr)...


En las consultas entre varias tablas:
- **Join**: La usamos para combinar 2 o más tablas en suna sola consulta
- **Left|Right|Full Join**: devuelve las filas dependiendo del atributo que eligamos, y si no hay relación entre las filas saldrá un valor null
- **Using|On**: Es un atributo que va ligado a **join** y donde le indicamos la **FK** de a relación entre las tablas que queremos hacer la consulta
- **Cross Join**: Combina las filas de la tabla con las filas e su propia tabla



# Reflexión Personal