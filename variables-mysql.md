# Variables MySQL

En **MySQL** se pueden usar **variables** como en los lenguajes de programación y puede resultar bastante útil. Las variables se usan para pasar un valor de una instrucción SQL a otra instrucción SQL.&#x20;

MySQL reconoce diferentes tipos de variables. El primer tipo son las variables definidas por el usuario, identificadas por un símbolo `@` usado como prefijo y posteriormente el nombre de la variable (`@variable_name`) con una longitud de máximo 64 caracteres alfanuméricos.

Las variables definidas por el usuario no distinguen entre mayúsculas y minúsculas, significa que `@id` y `@ID` son iguales.

```
/*VARIABLE CON VALOR NULO*/
select @var0;

/* CREAR VARIABLE Y UTILZAR EN CONSULTA */
set @var_name = 7;
select * from table_name where id = @var_name;

/* GUARDAR VALOR EN VARIABLE */
set @age_total = 0;
select count(*) into @age_total from table_name where age = @var_name;

/*ASIGNAR VALOR A VARIABLE DE UNA CONSULTA */
SELECT @var3 := column01 FROM table_name where id = 7;

/* CONSULTAR VARIABLE */
select @var1;
select @var1, @var2, @var3;
select @var1 + @var2;
```
