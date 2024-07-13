## What's A database
- a database is an organized collection of data so that it can be easily accessed.
- To manage these databases , Databases Mangment System (DBMS) are used

# Types of DBMS
- non-relational (DBMS): file , json , xml...
- relational (RDBMS): mysql , sql-server Oracle...

# why databases
- the dealing with normal files(DBMS) is so hard compared with databases(RDBMS).

- row = entity = record
- column = field = attribute = feature
- table = Entity set

## Data vs Information vs Knowledge vs wisdom
	# Data vs Information
		- A data is raw facts
		- information is data in context(insigts from this data)
		- Data + Meaning = Information
		- data is unstructured , info is structered
		- data is unanalized m info is analyzed
	# Wisdom vs Knowledge
		- information with time = knowledge
		- knowledge with practice (applied) = wisdom
## database essintials

# what is null.
	- null = nothing ( has no value , missing)
	- null != 0 or blank space
	- it's distinct value in database
	- if the attribute is optional is set to null

# Data Analysis with SQL
## MySql
- OpenSource DBMS Build with Michel Beta3 ... see sql directory
- Easy to understand , has few features , has many forks (mariadb , Percona , MySql Enterprise (oracle))
- Mysql = Oracle

[!PLEASENOTE] You need To understand containers.

- we will start with installing it on an ubuntu container.
- `docker run -it -v $(pwd)/databases:/usr/databases ubuntu:latest` = pulling ubuntu image
- `container$ apt install mysql-server`
- `sudo usermod -d /var/lib/mysql/ mysql`
- `/etc/init.d/mysqld start`

# Setting up Environment

- `docker-compose -f sql/mysql.yml up -d`
- the compose file contains 3 services , mysql official image (please ensure that your cpu version supports x64_86_v2 technology other wise edit the latest tag into 8.0.32) , the second one is mysql-workbensh , the third one is jupeter

- Mysql-WorkBensh is a GUI representation for mysql db.

- Databases in mysql is called schemas or databases (you may see it on mysql-workbench)
# SQL
- `SHOW DATABASES;` shows all databaess on mysql engine.
- `ALTER USER `root`@localhost INDETIFIED WITH mysql_native_password BY `PASS`` grants privleges to the root user with the PASS password

- `mysql -u root -pPASS` = login with root user with PASS password (with no spaces !)
- `show variables where variable_name = `datadir`;` , gets the system variable named datadir that contains the databases directory

- `CREATE database testdb;` creates a new database
- `each database in mysql is being stored in /var/lib/mysql/[dbname]` this directory contains the tables of that database.
- `USE [dbname];` changes the database to dbname
- `CREATE TABLE tbl1 (id INT , name VARCHAR(20))` , creates a table with 2 columns (id , name)
- `Show tables from [dbname];` shows the tables in the database

# Restoring Database
- `SOURCE /usr/databases/sakila-db/sakila-schema.sql` , sakila-db is a famouse testing db , this will create the meta-data (empty tables)

- `SOURCE /usr/databases/sakila-db/sakila-data.sql;` , this will fill the sakila database with actual data

- `SELECT * FROM actor limit 10` SHOWS FIRST 10 ROWS IN A TABLE;
- `show create table actor\G` shows the sql-statment of the created table;


	 
