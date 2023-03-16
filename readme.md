# Resumen

En las consultas básicas hemos visto:
- **Select**: Es la que más hemos usado con diferencia, y sirve para selecionar datos de una tabla.
- **From**: es otro comando ligado a select, en el que le indicamos de que tabla debe consultar los datos.
- **Where**: La usamos con fines de filtrar los resultados de la consulta **SELECT** dependiendo de las condiciones que indiquemos.
- **Distinct**: Nos elimina las filas que estén repetidas.
- **Order by**: En el que podemos ordenar por las tablas, y si usamos **DESC** las ordenara de forma descendente.
- **Atributos**: hemos decenas de atributos que pueden complementar a la consulta de **SELECT** y en que solo voy a destacar el: LIKE, UPPER, to_char, expresiones regulares (regexp_like, regexp_substr)...


En las consultas entre varias tablas:
- **Join**: La usamos para combinar 2 o más tablas en una sola consulta.
- **Left|Right|Full Join**: devuelve las filas dependiendo del atributo que elijamos, y si no hay relación entre las filas saldrá un valor null.
- **Using|On**: Es un atributo que va ligado a **join** y donde le indicamos la **FK** de a relación entre las tablas que queremos hacer la consulta.
- **Cross Join**: Combina las filas de la tabla con las filas e su propia tabla.



# Reflexión Personal

Tenía un total desconocimiento sobre como funcionaban las Bases de Datos y el tipo de datos que pueden almacenar.
Como las consultas para mostrar los datos específicos que queremos obtener.

Este tema me ha aportado abrirme al mundo de los lenguajes aparte de HTML y CSS que ya conocía, y me ha fascinado lo poco que he visto.

Un punto que destacar ha sido la asignatura que más horas le he echado, no por falta de comprensión o que necesitaba estudiar más porque lo llevase peor, sino porque es la que más me ha entretenido y me ha gustado practicarla día a día.

Un punto en contra ha sido que me costaba entender consultas y su sintaxis.



# Ejercicios Significativos

## De la práctica 18, el ejercicio 4 de las tablas de Geografía

Esta ha sido una de las primeras consultas "complejas" que más me ha costado con diferencia, ya que me liaba entre la relación que había que elegir.

```sh
select distinct
    l.NOMBRE localidad,c.NOMBRE comunidad,p.NOMBRE provincia,
    cp.nombre
from LOCALIDADES l
join PROVINCIAS p using (n_provincia)
join COMUNIDADES c using (id_comunidad)
join LOCALIDADES cp on (l.id_localidad=p.ID_CAPITAL);
```

## De la práctica 18, el ejercicio 11 de las tablas de Geografía

En esta consulta no me ha resultado muy difícil pera ha sido una de las que me han salido sin ningún esfuerzo.

```sh
select c.nombre,c1.NOMBRE
from COMUNIDADES c
cross join COMUNIDADES c1
where length(c.NOMBRE)=length(c1.NOMBRE)
and c.NOMBRE!=c1.NOMBRE;
```

## De la práctica 18, el ejercicio 16 de las tablas de Geografía

Una consulta con **max** que me salió sin tener el conocimiento de su sintaxis.

```sh
select max(count(l.NOMBRE))
from PROVINCIAS p
join LOCALIDADES l using (n_provincia)
group by p.NOMBRE
order by p.NOMBRE;
```

## De la práctica 23, el ejercicio 3 de las tablas de Estudios

Una consulta que me costó, no era muy completa.

```sh
select NOMBRE,APELLIDO1,APELLIDO2,to_char(avg(nvl(nota,0)),'99D00') nota
from ALUMNOS a
join ASISTIR asi using (cod_alumno)
group by NOMBRE,APELLIDO1,APELLIDO2
having avg(nvl(nota,0))>5;
```



# Ejercicios de Invención Propia

Un informe de la cantidad de pedidos de un tipo de producto, de este mes.

```sh
SELECT tipo, SUM(cantidad) AS ventas_totales
FROM LINEAS_PEDIDO
join PEDIDOS p using (n_pedido)
where extract(month from FECHA)=extract(month from sysdate)
GROUP BY extract(month from fecha), tipo;
```



# Conclusiones

Las principales dificultades han sido entender lo que hacía cada atributo (lo que va dentro del where) y sobre todo los cross join mezclando con left outer join...

Lo que más me ha gustado han sido esforzarme y obligarme a pensar 20 minutos para una simple consulta, y conseguir la satisfacción de resolverla.