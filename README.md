[![aledc.com](https://github.com/aledc7/Scrum-Certification/blob/master/recursos/aledc.com.svg)](https://aledc.com)
[![ingenea.com.ar](https://github.com/aledc7/Scrum-Certification/blob/master/recursos/ingenea.svg)](http://ingenea.com.ar)
[![License](https://github.com/aledc7/Scrum-Certification/blob/master/recursos/mit-license.svg)](https://aledc.com)
[![GitHub release](https://github.com/aledc7/Scrum-Certification/blob/master/recursos/release.svg)](https://aledc.com)
[![Dependencies](https://github.com/aledc7/Scrum-Certification/blob/master/recursos/dependencias-none.svg)](https://aledc.com)

![Mysql](https://github.com/aledc7/mysql/blob/master/mysql.png?raw=true)
# MYSQL - Comandos Básicos


## Luego de Instalado Mysql, se debe ejecutar el siguiente comando para poder correr mysql en cualquier carpeta:

````
sudo sh -c 'echo /usr/local/mysql/bin > /etc/paths.d/mysql'
````

## Mysql en MAC bajo MAMP
Para usar la terminal de mysql en MAMP en una MAC, correr en la terminal el siguiente comando:
```php
/Applications/MAMP/Library/bin/mysql --host=localhost -uroot -proot
`````

## Ver si tiene seteado UTF8 o alguna otra    

```php
show variables like "%character%"; 
````





## INGRESANDO A LA TERMINAL DE MYSQL
```mysql
mysql -u root -p
```
Una vez dentro de la terminal, cambiará el promp, mostrando: __mysql__
Aqui ya podremos empezar a correr los comandos propios de mysql.

## Crear Base de Datos
```mysql
mysql> create database nombre_base;
```

## Subiendo Scrip de datos a una base de datos ya creada
```php
/Applications/MAMP/Library/bin/mysql -u root -proot nombre_base < /Users/aledc/Desktop/archivo_a_subir.sql;
````


## Mostrar todas Las Bases de Datos
```mysql
mysql> show databases;
```
## Mostrar todos los usuarios
````
mysql>  SELECT User FROM mysql.user;
````
## Crear un Usuario
```mysql
mysql> CREATE USER 'nombre_usuario'@'localhost' IDENTIFIED BY 'MI_SUPER_CONTRASEÑA';
````


## Borrar un usuario especifico
```mysql
mysql> DROP USER nombre_usuario@localhost
````


## Cambiar a una Base de Datos Especifica
```mysql
mysql> use nombre_base;
````

## Mostrar todas las tablas
```mysql
mysql> show tables;
````

## Ver el formato de una tabla
```mysql
mysql> describe [table name];
````

## Borrar una Base de datos
```mysql
mysql> drop database [database name];
````

## Borrar una tabla
```mysql
mysql> drop table [table name];
````

## Mostrar todos los registros de una tabla
```mysql
mysql> SELECT * FROM [table name];
````

## Mostrar la información de una columna
```mysql
mysql> show columns from [table name];
````

## Mostrar Renglones con un Valor Específico
```mysql
mysql> SELECT * FROM [table name] WHERE [field name] = "value";
````

## Mostrar todos los registros que contengan el nombre "Algo" y el telefono 0123456789
```mysql
mysql> SELECT * FROM [table name] WHERE name = "Algo" AND phone_number = '0123456789';
````

## Show all records not containing the name "Something" AND the phone number '0123456789' order by the phone_number field.
```mysql
mysql> SELECT * FROM [table name] WHERE name != "Something" AND phone_number = '0123456789' order by phone_number;
````

## Show all records starting with the letters 'Something' AND the phone number '0123456789'.
```mysql
mysql> SELECT * FROM [table name] WHERE name like "Something%" AND phone_number = '0123456789';
````

## Show all records starting with letters 'Something' AND the phone number '0123456789' limit to records 1 through 5.
```mysql
mysql> SELECT * FROM [table name] WHERE name like "Something%" AND phone_number = '0123456789' limit 1,5;
````

## Use a regular expression to find records. Use "REGEXP BINARY" to force case-sensitivity. This finds any record beginning with a.
```mysql
mysql> SELECT * FROM [table name] WHERE rec RLIKE "^a";
````

## Show unique records.
```mysql
mysql> SELECT DISTINCT [column name] FROM [table name];
````

## Show selected records sorted in an ascending (asc) or descending (desc).
```mysql
mysql> SELECT [col1],[col2] FROM [table name] ORDER BY [col2] DESC;
````

## Return number of rows.
```mysql
mysql> SELECT COUNT(*) FROM [table name];
````

## Sum column.
```mysql
mysql> SELECT SUM(*) FROM [table name];
````

## Creating a new user. Login as root. Switch to the MySQL db. Make the user. Update privs.
```mysql
# mysql -u root -p
mysql> use mysql;
mysql> INSERT INTO user (Host,User,Password) VALUES('%','username',PASSWORD('password'));
mysql> flush privileges;
````

## Change a users password from unix shell.
```mysql
# [mysql dir]/bin/mysqladmin -u username -h hostname -ppassword 'new-password'
`````

## Change a users password from MySQL prompt. Login as root. Set the password. Update privileges.
`````

# mysql -u root -p
mysql> SET PASSWORD FOR 'user'@'hostname' = PASSWORD('password');
mysql> flush privileges;
`````

## Recover a MySQL root password. Stop the MySQL server process. Start again with no grant tables. Login to MySQL as root. Set new password. Exit MySQL and restart MySQL server.
```mysql
# /etc/init.d/mysql stop
# mysqld_safe --skip-grant-tables
# mysql -u root
mysql> use mysql;
mysql> update user set password=PASSWORD("newpassword") where User='root';
mysql> flush privileges;
mysql> quit
# /etc/init.d/mysql stop
# /etc/init.d/mysql start
````

## Set a root password if there is no root password.
```mysql
# mysqladmin -u root password newpassword
````

## Update a root password.
```mysql
# mysqladmin -u root -p oldpassword newpassword
````

## Allow the user "Someone" to connect to the server from localhost using the password "passwd". Login as root. Switch to the MySQL db. Give privs. Update privs.
```mysql
# mysql -u root -p
mysql> use mysql;
mysql> grant usage on *.* to Someone@localhost identified by 'passwd';
mysql> flush privileges;
```
## Give user privilages for a db. Login as root. Switch to the MySQL db. Grant privs. Update privs.
```mysql
# mysql -u root -p
mysql> use mysql;
mysql>INSERT INTO user(Host,Db,User,Select_priv,Insert_priv,Update_priv,Delete_priv,Create_priv,Drop_priv)
 VALUES ('%','databasename','username','Y','Y','Y','Y','Y','N');
mysql> flush privileges;
```
## or
```mysql
mysql> grant all privileges on databasename.* to username@localhost;
mysql> flush privileges;
````

## To update info already in a table.
```mysql
mysql> UPDATE [table name] SET Select_priv = 'Y',Insert_priv = 'Y',Update_priv = 'Y' where [field name] = 'user';
````

## Delete a row(s) from a table.
```mysql
mysql> DELETE from [table name] where [field name] = 'fieldvalue';
````

## Update database permissions/privilages.
```mysql
mysql> flush privileges;
````

## Delete a column.
```mysql
mysql> alter table [table name] drop column [column name];
```

## Add a new column to db.
```mysql
mysql> alter table [table name] add column [new column name] varchar (20);
````

## Change column name.
```mysql
mysql> alter table [table name] change [old column name] [new column name] varchar (50);
````

## Make a unique column so you get no dupes.
```mysql
mysql> alter table [table name] add unique ([column name]);
````

## Make a column bigger.
```mysql
mysql> alter table [table name] modify [column name] VARCHAR(3);
````

## Delete unique from table.
```mysql
mysql> alter table [table name] drop index [colmn name];
````

## Load a CSV file into a table.
```mysql
mysql> LOAD DATA INFILE '/tmp/filename.csv' replace INTO TABLE [table name] FIELDS TERMINATED BY ',' LINES TERMINATED BY '\n' (field1,field2,field3);
````

## Exportar Base de Datos Completa
```mysql
mysqldump -u username --password=MySecretPassword nombreBaseDatos > /home/aledc/BackUps/databasename.sql
````

## Exportar solo una tabla
```mysql
mysqldump -u username --password=MySecretPassword nombreBaseDatos nombretabla > /home/aledc/BackUps/tablaname.sql
````

## Importar Base de datos
```js
mysql -u nombre_usuario -p base_de_datos < archivo.sql

# Luego de esto pedirá la contraseña para la base de datos creada en donde se quiere importar el archovo.
````

## Create Table Example 1.
```mysql
mysql> CREATE TABLE [table name] (name VARCHAR(20));
````

## Create Table Example 2.
```mysql
mysql> create table [table name] (personid int(50) not null auto_increment primary key,firstname varchar(35),middlename varchar(50),lastnamevarchar(50) default 'somethiing');
````

## Buscar por nombre de columnas en todas las tablas de la Base
```mysql
SELECT DISTINCT TABLE_NAME 
    FROM INFORMATION_SCHEMA.COLUMNS
    WHERE COLUMN_NAME IN ('columna_a_buscar')
        AND TABLE_SCHEMA='nombre_base'
````

Tambien es posible usar comidines para buscar solo una parte del nombre de la columna
```mysql
SELECT TABLE_NAME, COLUMN_NAME
FROM INFORMATION_SCHEMA.COLUMNS
WHERE COLUMN_NAME LIKE '%algo%'
````

Los comodines '%' pueden combinarse usando solo al comienzo o solo al final.





