# Stored Procedures - Procedimientos Almacenados

Los **procedimientos almacenados MySQL**, también conocidos como _Stored Procedure_, se presentan como conjuntos de instrucciones escritas en el lenguaje SQL. Su objetivo es realizar una tarea determinada, desde operaciones sencillas hasta tareas muy complejas. Los procedimientos almacenados MySQL contienen una o más instrucciones SQL además de un procesamiento manipulador o lógico.

La característica fundamental de los procedimientos almacenados MySQL es que estos comandos **se quedan almacenados y se ejecutan en el servidor o en el motor de bases de datos**. Este aspecto permite que las aplicaciones clientes las ejecuten directamente mediante llamada a una API.

**Los procedimientos almacenados MySQL se han diseñado para aligerar a las aplicaciones clientes, pudiendo ejecutar directamente en el servidos aquellas tareas pesadas y que necesitan muchos recursos.**

Estas son las **características principales** de los procedimientos almacenados MySQL:

* Pueden recibir y devolver parámetros.
* Pueden manejar tablas, ejecutando operaciones e iteraciones de lectura/escritura.
* Pueden devolver una tabla como resultado.
* Se almacenan en la base de datos en la cual se crean.
* No dependen de ninguna tabla en particular.
* Pueden aceptar recursividad.

**Ventajas de Procedimientos Almacenados**

* **Compatibilidad**: los procedimientos almacenados MySQL permiten ejecutar la misma operación sobre la base de datos también en el caso de que las aplicaciones cliente estén implementadas en distintas plataformas y programadas en distintos lenguajes.
* **Integridad**: gracias a los procedimientos almacenados MySQL es posible centralizar el acceso a la información.
* **Seguridad**: cuando necesitamos evitar el acceso directo a la base de datos, los procedimientos almacenados MySQL permiten establecer un entorno seguro, otorgando permisos y privilegios para la ejecución.
* **Rendimiento**: con los procedimientos almacenados MySQL todo el trabajo se ejecuta en el servidor, por lo cual se minimiza de forma importante la cantidad de información intercambiada con las aplicaciones cliente y se reduce el tráfico de acceso a la base de datos además del numero de accesos.
* **Centralización:** los procedimientos almacenados MySQL permiten centralizar la lógica comercial ofreciendo a todas las aplicaciones clientes la misma versión actualizada, lo que hace el mantenimiento más sencillo.
* **Reutilización del código**: al escribir un mismo código que se ejecuta por toda las aplicaciones, es posible reducir las inconsistencias y ejecutar varias veces el mismo procedimiento.
* **Sencillez**: los procedimientos almacenados permiten la creación de bibliotecas o funciones, lo que facilita mucho el trabajo del programador ya que se trata de características compartidas por los principales lenguajes de programación modernos.

**Sentencia "Delimiter"**

Para definir un procedimiento almacenado es necesario modificar temporalmente el carácter separador que se utiliza para delimitar las sentencias SQL.

El carácter separador que se utiliza por defecto en SQL es el punto y coma (`;`). En los ejemplos que vamos a realizar en esta unidad vamos a utilizar los caracteres **`//`** para delimitar las instrucciones SQL, pero es posible utilizar cualquier otro carácter.

#### Parámetros de entrada, salida y entrada/salida <a href="#parametros-de-entrada-salida-y-entradasalida" id="parametros-de-entrada-salida-y-entradasalida"></a>

* **Entrada**: Se indican poniendo la palabra reservada `IN` delante del nombre del parámetro. Estos parámetros no pueden cambiar su valor dentro del procedimiento, es decir, cuando el procedimiento finalice estos parámetros tendrán el mismo valor que tenían cuando se hizo la llamada al procedimiento. En programación sería equivalente al paso por valor de un parámetro.
* **Salida**: Se indican poniendo la palabra reservada `OUT` delante del nombre del parámetro. Estos parámetros cambian su valor dentro del procedimiento. Cuando se hace la llamada al procedimiento empiezan con un valor inicial y cuando finaliza la ejecución del procedimiento pueden terminar con otro valor diferente. En programación sería equivalente al paso por referencia de un parámetro.
* **Entrada/Salida**: Es una combinación de los tipos `IN` y `OUT`. Estos parámetros se indican poniendo la palabra reservada `IN/OUT` delante del nombre del parámetro.

```
/* CREAR PROCEDIMIENTO ALMACENADO NULO SIN PARAMATEROS */
delimiter //
create procedure procedure_namep ()
begin
select * from table_name;
end //
delimiter ;

delimiter //
create procedure procedure_namep ()
begin
select * from table_name;
end ;

/* CREAR PROCEDIMIENTO ALMACENADO PARAMETROS ENTRADA/SALIDA */
delimiter //
create procedure procedure_namep (in var1 int)
begin
select * from table_name where id = var1;
end //
delimiter ;

delimiter //
create procedure procedure_namep (in var1 int, out var2 int)
begin
select count(*) into var2 from table_name where id = var1;
end //
delimiter ;

/* EJECUTAR PROCEDIMIENTO ALMACENADO */
call storedprocedure_name();
call storedprocedure_name('valorx');
call storedprocedure_name('valorx', @result);
select @result;

/* VER CREACION DE PROCEDIMIENTO ALMACENADO */
show create procedure storedprocedure_name;

/* ELIMINAR PROCEDIMIENTO ALMACENADO */
drop procedure storedprocedure_name;
```
