# SQL Cheat Sheet

## Data Types

#### Integers

```sql
INT -- Between -2 billion / +2 billion. Size : 4 byte
```
```sql
TINYINT -- Used for data from 0 to 255. Size : 1 byte
```
```sql
SMALLINT -- Between -32.768 and 32.768. Size : 2 byte
```
```sql
BIT -- It can be used in cases of two different situations. E.g. girl/boy
```
```sql
BIGINT -- Between 2⁶³ and 2⁶³. Size : 8 byte
```
#### Float

```sql
FLOAT(size,d) -- The total number of digits is specified in size. The number of digits after the decimal point is specified in the d parameter. E.g. float(5,2) is 190,39. Size : 4 byte
```

#### Double

```sql
DOUBLE(size,d) -- The total number of digits is specified in size. The number of digits after the decimal point is specified in the d parameter. E.g. double(4,2) is 19,07. Size : 8 byte 
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
BLOB(n) or TEXT(n) -- Up to 65.535 bytes (approximately 64 KB) of data can be stored.
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