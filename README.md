# Views - Vistas

**Las Vistas (Views) en MySQL son tablas virtuales.** Es decir, tablas que no guardan ningún dato propiamente dentro de ellas. Solo muestran los datos que están almacenados en otras tablas (que sí son reales).

**Las Vistas (Views) en MySQL son tablas virtuales.** Es decir, tablas que no guardan ningún dato propiamente dentro de ellas. Solo muestran los datos que están almacenados en otras tablas (que sí son reales).

**Ventajas al crear Views**

* **Control de accesos:** de una tabla real, se puede escoger qué información específicamente se desea compartir con otros usuarios. De este modo, ellos no tendrán acceso al resto de los datos de la tabla, solo a las VIEWS.
* **Mejora del rendimiento:** se pueden crear _queries_ (consultas) a partir de vistas que han sido extraídas de SELECT complejas. Esto evita tener que ejecutar _queries_
* **Pruebas seguras:** las vistas ofrecen un entorno de tablas de prueba para que los desarrolladores no afecten la información real.
* **Reusabilidad de consultas:** gracias a las vistas, no se deben crear consultas complejas que requieran uniones de manera repetida.
* **Mantenimiento de la integridad:** al crear aplicaciones y usar las VIEWS en vez de las tablas reales se garantiza que dichas aplicaciones no se rompan cuando se realicen cambios en la estructura de la base de datos.

```
/* CREAR VISTA */
create view vw_view_name as 
select * from table_name;

/* REEMPLAZAR VISTA */
create or replace view vw_view_name as 
select * from table_name;

/* EJECUTAR VISTA */
select * from vw_view_name;
select column01, column02 from vw_view_name as ViewInto;

/* MODIFICAR VISTA */
alter view vw_view_name as
select * from table_name;

/* VER CREACION DE VISTA */
show create view vw_view_name;

/* ELIMINAR VISTA */
drop view vw_view_name;

/* CONSULTA WHERE EN VISTA */
select * from vw_view_name 
where columnx = 'valorx';
```
