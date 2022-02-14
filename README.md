# MSSQL Cheat Sheet

## Data Types

#### Integers

```sql
INT -- Between -2 billion / +2 billion. It uses 4 bytes of Storage.
```

```sql
TINYINT -- Used for data from 0 to 255. It uses 1 bytes of Storage
```

```sql
SMALLINT -- Between -32.768 and 32.768. It uses 2 bytes of Storage
```

```sql
BIT -- It can be used in cases of two different situations. E.g. girl/boy
```

```sql
BIGINT -- Between 2⁶³ and 2⁶³. It uses 8 bytes of Storage
```

#### Float

```sql
FLOAT(size,d) -- The total number of digits is specified in size. The number of digits after the decimal point is specified in the d parameter. E.g. float(5,2) is 190,39.
```

#### Decimal

```sql
DECIMAL(size,d)  -- The total number of digits is specified in size. The number of digits after the decimal point is specified in the d parameter. E.g. Decimal(4,2) is 78,65 or Decimal(4,1) is 125,8.
```

#### String

```sql
CHAR(n) -- It is not support unicode. Used in characters of fixed length. For example, it is used in statements such as identification number and phone number. It takes up as much space as the input size, even if fewer characters are entered than specified (n). n parameter can be from 0 to 255.
```

```sql
NCHAR(n) -- Unlike char, it supports unicode.
```

```sql
VARCHAR(n)  -- Unlike char, it takes up as much space as the size of the data. n parameter can be from 0 to 65535.
```

```sql
NVARCHAR(n)  -- Unlike varchar, it supports unicode.
```

```sql
TEXT(n) -- Up to 65.535 bytes (approximately 64 KB) of data can be stored.
```

#### Date

```sql
DATE -- Format - (YYYY-MM-DD)
```

#### Date Time

```sql
DATETIME -- Format - (YYYY-MM-DD HH:MM:SS)
```

#### Time

```sql
TIME -- Format - (HH:MM:SS)
```

## Comments

```sql
/* Multi
line
comment */
```

```sql
-- Single Line Comment
```

## Data Definition Language (DDL)

#### Create Database

```sql
create database db;
```

#### Use Database

```sql
use db;
```

#### Create Table

```sql
create table tblStudents
(
    student_id tinyint identity (1,1) primary key,
    first_name varchar(50),
    last_name varchar(50),
    gender varchar(6),
    age tinyint,
	club varchar(50),
	city varchar(25)
);

create table tblLessons
(
	lesson_id tinyint identity (1,1) primary key,
	lesson_name varchar(20)
)

create table tblResults
(
    result_id tinyint identity (1,1) primary key,
    student_id tinyint,
    lesson_id tinyint,
    exam1 smallint,
    exam2 smallint,
	average decimal(5,2),
	result bit
);

```

#### Drop Column

```sql
alter table tblStudents drop column gender;

```

#### Add Column

```sql
alter table tblStudents add gender bit;
```

#### Modify the Datatype of column

```sql
alter table tblStudents alter column average tinyint;
```

#### Truncate Table

```sql
truncate table tblStudents; --  Delete all rows
```

#### Drop Table

```sql
drop table tblLessons;
```

#### Drop Database

```sql
drop database db;
```

## Data Manipulation Language (DML)

#### Insertion (Complete)

```sql
insert into tblStudents (first_name, last_name, gender, age, club, city) values('Ali','Yıldırım','Male',21,'Chess','İzmir');
insert into tblStudents values('Baran','Doğu','Male',20,'Football','Malatya');
```

#### Insertion (Partial)

```sql
insert into tblStudents (first_name, last_name) values('Emre','Sarı');
```

#### Updating all rows

```sql
update tblResults set average=(exam1+exam2)/2;
```

#### Updating a specified row

```sql
update tblResults set average = average + 10 where student_id = 1;
```

#### Delete a specified row

```sql
delete from tblStudents where student_id = 2;
```

#### Delete all rows

```sql
delete from tblStudents;
```

## Data Query Language (DQL)

#### Display Table

```sql
select * from tblStudents;
```

#### Select only specified columns

```sql
select student_id, first_name from tblStudents;
```

#### Select only few rows

```sql
select student_id, first_name from tblStudents where age > 20;
```

### Where Clause

#### Greater than(>)

```sql
select * from tblResults where average > 49;
```

#### Greater than equal to(>=)

```sql
select * from tblResults where average >= 50;
```

#### Less than(<)

```sql
select * from tblResults where average < 50;
```

#### Less than equal to(<=)

```sql
select * from tblResults where average <= 49;
```

#### Range

```sql
select * from tblResults where average >= 50 and average < 80;
```

#### BETWEEN and AND

```sql
select * from tblResults where average between 50 and 80;
```

### OR

```sql
select * from tblResults where average = 50 or average = 75;
```

#### Null

```sql
select * from tblStudents where gender is NULL;
```

#### Not null

```sql
select * from tblStudents where gender is NOT NULL;
```

### ORDER BY Clause

```sql
select * from tblStudents ORDER BY age DESC; --large to small sorting
select * from tblStudents ORDER BY age asc; -- small to large sorting
```

#### Like Operator

```sql
select * from tblStudents where last_name like '%a%'; -- Similar to *a* in regrex
```

```sql
select * from tblStudents where first_name like 'Al_'; -- Similar to Al. in regrex
```

## Aggregation

#### Sum function

```sql
select sum(exam1) from tblResults;
```

#### Average function

```sql
select avg(exam1) from tblResults;
```

#### Count function

```sql
select count(exam1) from tblResults;
```

#### Maximum function

```sql
select max(exam1) from tblResults;
```

#### Minimum function

```sql
select min(exam1) from tblResults;
```

## Group By

```sql
select gender, count(*) as 'Count Of Students' from tblStudents group by gender
```

## Having

```sql
select age, count(*) as 'Count Of Students' from tblStudents group by age having count(*) < 2 -- Adds that the number of students must be less than 2
```
