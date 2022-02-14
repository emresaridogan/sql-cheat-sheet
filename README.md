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
create table tblEmployee
(
    employee_id tinyint primary key,             
    first_name varchar(50),
    last_name varchar(50),
    dept_number tinyint,
    age tinyint,
    salary smallint
);

create table tblDepartment
(
    dept_number tinyint primary key,
    dept_name varchar(50),
    dept_location varchar(50),
    emp_id tinyint
);
```

#### Add Column
```sql
alter table tblEmployee add gender bit;
```

#### Drop Column
```sql
alter table tblEmployee drop column gender;

```

#### Modify the Datatype of column
```sql
alter table tblEmployee alter column salary real;
```

#### Truncate Table
```sql
truncate table tblEmployee; --  Delete all rows
```

#### Drop Table
```sql
drop table tblDepartment;
```

#### Drop Database
```sql
drop database db;
```

## Data Manipulation Language (DML)

#### Insertion (Complete)
```sql
insert into tblEmployee (employee_id, first_name, last_name, dept_number, age, salary) values (1, 'James', 'Clear', 1, 20, 3100.80);

insert into tblEmployee values (2, 'Cal', 'Newport', 2, 25, 4500.60);
```
#### Insertion (Partial)
```sql
insert into tblEmployee (employee_id, first_name) values (3,'Morgan');
```

#### Updating all rows
```sql
update tblEmployee set salary = 0.5 * salary;
```

#### Updating a specified row
```sql
update tblEmployee set salary = 1.2 * salary where employee_id = 1;
```

#### Delete a specified row
```sql
delete from tblEmployee where employee_id = 2;
```

#### Delete all rows
```sql
delete from tblEmployee;
```
## Data Query Language (DQL)

#### Display Table
```sql
select * from tblEmployee;
```

#### Select only specified columns
```sql
select employee_id, first_name from tblEmployee;
```

#### Select only few rows
```sql
select employee_id, first_name from tblEmployee where age > 25;
```

### Where Clause

#### Greater than(>)
```sql
select * from tblEmployee where salary > 3100;
```

#### Greater than equal to(>=)
```sql
select * from tblEmployee where salary >= 3100;
```

#### Less than(<)
```sql
select * from tblEmployee where salary < 4500;
```

#### Less than equal to(<=)
```sql
select * from tblEmployee where salary <= 4500;
```

#### Range
```sql
select * from tblEmployee where salary <= 3100 and salary < 4500;
```

#### BETWEEN and AND
```sql
select * from tblEmployee where salary between 3100 and 4500;
```

### OR
```sql
select * from tblEmployee where salary = 3100 or salary = 4500;
```

#### Null
```sql
select * from tblEmployee where salary is NULL;
```

#### Not null
```sql
select * from tblEmployee where salary is NOT NULL;
```

### ORDER BY Clause
```sql
select * from tblEmployee ORDER BY salary DESC;
```

#### Like Operator
```sql
select * from tblEmployee where last_name like '%r%';          -- Similar to *r* in regrex
```
```sql
select * from tblEmployee where first_name like 'Ca_';           -- Similar to Ca. in regrex
```