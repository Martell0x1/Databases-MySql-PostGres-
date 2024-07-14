## What's A database
- a database is an organized collection of data so that it can be easily accessed.
- To manage these databases , Databases Mangment System (DBMS) are used

# Introduction to RDBMS
-  a Database is a perceived form of data ... a data that can be saved on anything (text file , json file ...etc)

- the situation was pretty missy ... peices of data in anyware .. until 1970 , when IBM came up with the `hierarchical database` which is very old database design (database model) (a way to connect different entities)

- in 1970 , `edgar Godd` published a paper explaining the idea of the Relational Databases (Data Bank)

- A `Relational Database` is a tabled form of database ... when you look at the database it will look like a table of columns and rows , the colum y has a relation with the row x

- Dr.Ramez El Masrey has a signifcant book , talking about Databases called [Fundamentals of Database Systems](https://www.auhd.edu.ye/upfiles/elibrary/Azal2020-01-22-12-28-11-76901.pdf)



# Types of DBMS
- non-relational (DBMS): file , json , xml...
- relational (RDBMS): mysql , sql-server Oracle...

# why databases
- the dealing with normal files(DBMS) is so hard compared with databases(RDBMS).

- row = record = relation
- column = field = attribute = feature
- table = Entity

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

# Modeling and Designing
- In RDB (Relational Database) a database appears in tables but the data itself isn't stored on the hard-disk in tables (not as .csv file) i will tell you how.

- Always Remember that the data in the table infornt of you represents a story you can tell , if you for any reason faild to tell that story(look at the database-design.ipynb file , if you looked at suosan smith you will fail to tell her story) , you should edit your design.

+------------+---------+-----------------------+------+
| GivenNames | Surname | CourseName            | Pctg |
+------------+---------+-----------------------+------+
| John Paul  | Bloggs  | Data Science          |   72 |
| Sarah      | Doe     | Programming 1         |   87 |
| John Paul  | Bloggs  | Computing Mathematics |   43 |
| John Paul  | Bloggs  | Computing Mathematics |   65 |
| Sarah      | Doe     | Data Science          |   65 |
| Susan      | Smith   | Computing Mathematics |   75 |
| Susan      | Smith   | Programming 1         |   55 |
| Susan      | Smith   | Computing Mathematics |   80 |
+------------+---------+-----------------------+------+

- you would notice a problem that the girl named susan smith has different degree in the same subject in this way you will not be able to tell her story.

- that's why we should edit this design and add another attribute / column called Id wich will make every student has it's own data so the story will be rright (the girl which has id x and her name is susan smith got A in prog 1)

+------------+------------+---------+-----------------------+------+
| StudentID  | GivenNames | Surname | CourseName            | Pctg |
+------------+------------+---------+-----------------------+------+
| 12345678   | John Paul  | Bloggs  | Data Science          |   72 |
| 12345121   | Sarah      | Doe     | Programming 1         |   87 |
| 12345678   | John Paul  | Bloggs  | Computing Mathematics |   43 |
| 12345678   | John Paul  | Bloggs  | Computing Mathematics |   65 |
| 12345121   | Sarah      | Doe     | Data Science          |   65 |
| 12345876   | Susan      | Smith   | Computing Mathematics |   75 |
| 12345876   | Susan      | Smith   | Programming 1         |   55 |
| 12345303   | Susan      | Smith   | Computing Mathematics |   80 |
+------------+------------+---------+-----------------------+------+

- in this edit also you would notice something that john paul is failed in the same subject ... did he failed or passed ??

- that's why we should think about adding more details (chaning the design)
+------------+------------+---------+-----------------------+------+-----+------+
| StudentID  | GivenNames | Surname | CourseName            | Year | Sem | Pctg |
+------------+------------+---------+-----------------------+------+-----+------+
| 12345678   | John Paul  | Bloggs  | Data Science          | 2019 |   2 |   72 |
| 12345121   | Sarah      | Doe     | Programming 1         | 2020 |   1 |   87 |
| 12345678   | John Paul  | Bloggs  | Computing Mathematics | 2019 |   2 |   43 |
| 12345678   | John Paul  | Bloggs  | Computing Mathematics | 2020 |   1 |   65 |
| 12345121   | Sarah      | Doe     | Data Science          | 2020 |   1 |   65 |
| 12345876   | Susan      | Smith   | Computing Mathematics | 2019 |   1 |   75 |
| 12345876   | Susan      | Smith   | Programming 1         | 2019 |   2 |   55 |
| 12345303   | Susan      | Smith   | Computing Mathematics | 2020 |   1 |   80 |
+------------+------------+---------+-----------------------+------+-----+------+


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


	 
