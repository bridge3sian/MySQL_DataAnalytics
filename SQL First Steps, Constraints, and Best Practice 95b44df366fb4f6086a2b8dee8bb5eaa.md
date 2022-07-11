# SQL First Steps, Constraints, and Best Practice

# First Steps in SQL

## Creating a Database

[Creating+a+Database+-+Part+I.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/CreatingaDatabase-PartI.pdf)

```sql
CREATE DATABASE [IF NOT EXISTS] database_name;
```

- CREATE DATABASE

creates a database as an abstract unit

- [IF NOT EXISTS]

verifies if a database with the same name exists already

the brackets around mean the statement is optional (you could either type or omit the statement)

- database_name

give a name that is short but at the same time as related to the content of the data as possible

the SQL code is not case sensitive

## Introduction to Data Types

[Introduction+to+Data+Types.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/IntroductiontoDataTypes.pdf)

We must always specify the type of data that will be inserted in each column of the table

Different data types represent different types of information that can be contained in a specific column

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled.png)

- Digits, symbols, or blank spaces can also be used in the string format

they will only convey text information

- size

indicates the memory space used by a data type

### String Data Types

[String+Data+Types.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/StringDataTypes.pdf)

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled%201.png)

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled%202.png)

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled%203.png)

### Integers

[Integers.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Integers.pdf)

numeric data types

- integer
- fixed point
- floating point

**integer**

whole numbers with no decimal point

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled%204.png)

### Fixed and floating-point data types

[Fixed-+and+Floating-Point+Data+Types.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Fixed-andFloating-PointDataTypes.pdf)

- precision

refers to the number of digits in a number

- scale

refers to the number of digits to the right of the decimal point in a number

- DECIMAL ( 5 , 3 ) means precision = 5, scale = 3

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled%205.png)

DECIMAL has a synonymous data type. It is called NUMERIC.

DECIMAL = NUMERIC

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled%206.png)

- used for approximate values only
- aims to balance between range and precision ( => “floating” )

will not give us a warning

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled%207.png)

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled%208.png)

### Other useful data types

[Other+Useful+Data+Types.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/OtherUsefulDataTypes.pdf)

- DATETIME

represents the date shown on the calendar and the time shown on the clock

- TIMESTAMP

used for a well-defined, exact point in time

records the moment in time as the number of seconds passed after the 1st of January 1970 00:00:00 UTC

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled%209.png)

### Creating a table

[Creating+a+Table.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/CreatingaTable.pdf)

```sql
CREATE DATABASE [IF NOT EXISTS] sales;
CREATE TABLE table_name (column);
```

compulsory requirement: add at least one column

```sql
CREATE TABLE table_name
(
column_1 data_type constraints,
column_2 data_type constraints,
…
column_n data_type constraints
);
```

```sql
CREATE TABLE sales                                           
(
    purchase_number INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    date_of_puchase DATE NOT NULL,
    customer_id INT,
    item_code varchar(10) NOT NULL
);
```

- AUTO_INCREMENT

frees you from having to insert all purchase numbers manually through the INSERT command at a later stage

assigns 1 to the first record of the table and automatically increments by 1 for every subsequent row

### Using databases and tables

[Using+Databases+and+Tables.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/UsingDatabasesandTables.pdf)

### Additional notes on using tables

[Additional+Notes+on+Using+Tables.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/AdditionalNotesonUsingTables.pdf)

# Constraints

## PRIMARY KEY constraint

[PRIMARY+KEY+Constraint.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/PRIMARYKEYConstraint.pdf)

constraints: specific rules, or limits, that we define in our tables

the role of constraints is to outline the existing relationships between different tables in our database

e.g. NOT NULL

```sql
CREATE TABLE sales                                           
(
    purchase_number INT AUTO_INCREMENT,
    date_of_puchase DATE NOT NULL,
    customer_id INT,
    item_code varchar (10),
PRIMARY KEY (purchase_number)
);
```

## FOREIGN KEY constraint

[FOREIGN+KEY+Constraint.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/FOREIGNKEYConstraint.pdf)

**foreign key**

points to a column of another table and, thus, links the two tables

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled%2010.png)

```sql
CREATE TABLE sales                                           
(
    purchase_number INT AUTO_INCREMENT,
    date_of_puchase DATE NOT NULL,
    customer_id INT,
    item_code varchar (10),
PRIMARY KEY (purchase_number)
FOREIGN KEY (customer_id) REFERENCES customers (customer_id) ON DELETE CASCADE
);
```

- **ON DELETE CASCADE**

if a specific value from the parent table’s primary key has been deleted, all the records from the child table referring to this value will be removed as well

```sql
ALTER TABLE sales                                           
ADD FOREIGN KEY (customer_id) REFERENCES customers (customer_id) ON DELETE CASCADE;
```

```sql
ALTER TABLE sales                                           
DROP FOREIGN KEY sales_ibfk_1; # foreign_key_name as in the INFO DDL
```

**OR**

Use GUI

![Untitled](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/Untitled%2011.png)

## UNIQUE Constraint

[UNIQUE+Constraint.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/UNIQUEConstraint.pdf)

- unique key

used whenever you would like to specify that you don’t want to see duplicate data in a given field

unique keys are implemented in SQL through a constraint – the UNIQUE Constraint

if you attempt to insert an already existing, duplicate value in the unique column, SQL will display an error

Syntax JUST AS  FOREIGN KEY constraint

- Indexes

unique keys in MySQL have the same role as indexes

**the reverse isn’t true !!!**

index of a table is an organizational unit that helps retrieve data more easily

```sql
ALTER TABLE customers
ADD UNIQUE KEY (email_address);
```

```sql
ALTER TABLE table_name
DROP INDEX unique_key_field;
```

## DEFAULT Constraint

[DEFAULT+Constraint.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/DEFAULTConstraint.pdf)

```sql
CREATE TABLE customers
(
	customer_id INT,
	first_name VARCHAR(255),
	last_name VARCHAR(255),
	email_address VARCHAR(255),
	number_of_complaints INT DEFAULT 0,
PRIMARY KEY (customer_id)
);
```

```sql
# Set Default
ALTER TABLE customers
CHANGE COLOUM number_of_complaints number_of_complaints INT DEFAULT 0;
```

```sql
# Drop Default
ALTER TABLE customers
ALTER COLUMN column_name DROP DEFAULT;
```

## NOT NULL Constraint

[NOT+NULL+Constraint.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/NOTNULLConstraint.pdf)

```sql
CREATE TABLE companies
(
	company_id INT AUTO_INCREMENT,
	headquarters_phone_number VARCHAR(255),
	company_name VARCHAR(255) NOT NULL,
PRIMARY KEY (company_id)
);
```

```sql
# Drop not-null constraint
ALTER TABLE companies
MODIFY company_name VARCHAR(255) NULL;
```

```sql
ALTER TABLE companies
CHANGE COLUMN company_name company_name VARCHAR(255) NOT NULL;
```

# SQL Best Practices

[Coding+Techniques+and+Best+Practices.pdf](SQL%20First%20Steps,%20Constraints,%20and%20Best%20Practice%2095b44df366fb4f6086a2b8dee8bb5eaa/CodingTechniquesandBestPractices.pdf)