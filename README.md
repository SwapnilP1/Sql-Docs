# PL = SQL 


PL/SQL (Procedural Language/Structured Query Language) is Oracle Corporation's procedural extension for SQL (Structured Query Language). 

It is a powerful and flexible programming language that is closely integrated with the Oracle Database. PL/SQL allows developers to write procedural code that can be executed directly within the database engine.


Here are some key concepts and features of PL/SQL:


Block Structure:

PL/SQL programs are organized into blocks. A block consists of declarations, executable statements, and exception handlers. The basic structure of a PL/SQL block looks like this:

DECLARE
  -- Declarations (optional)
BEGIN
  -- Executable statements
EXCEPTION
  -- Exception handling (optional)
END;



Variables and Constants:

You can declare variables and constants in the declaration section of a PL/SQL block. Variables are used to store and manipulate data within the block.


Data Types:

PL/SQL supports various data types, including scalar types (such as VARCHAR2, NUMBER, DATE), composite types (such as records and tables), and reference types.




Control Structures:

PL/SQL supports standard programming constructs like IF-THEN-ELSE, CASE, LOOP, WHILE, and FOR loops for controlling the flow of execution.


PL/SQL allows you to create reusable units of code called procedures and functions. Procedures are designed to perform specific tasks, and functions return a value.



CREATE OR REPLACE PROCEDURE my_procedure
IS
BEGIN
  -- Procedure logic
END my_procedure;

- Exception Handling:

PL/SQL provides a robust exception handling mechanism to deal with errors. You can define exception handlers within your blocks to handle specific errors that may occur during execution.


EXCEPTION
  WHEN others THEN
    -- Handle exceptions here

-  Cursors: PL/SQL uses cursors to process result sets from SQL queries. You can use explicit cursors for more control over the data retrieval process

-  Triggers: -  PL/SQL triggers are special types of stored procedures that are automatically executed (or "triggered") in response to certain events, such as INSERT, UPDATE, or DELETE operations on a table.

Packages:
-  Packages are a way to organize related procedures, functions, variables, and other PL/SQL constructs into a single named unit. They promote modularity and code reuse.


CREATE OR REPLACE PACKAGE my_package
IS
  PROCEDURE procedure_in_package;
END my_package;

CREATE OR REPLACE PACKAGE BODY my_package
IS
  PROCEDURE procedure_in_package
  IS
  BEGIN
    -- Procedure logic
  END procedure_in_package;
END my_package;

-  Dynamic SQL:
        PL/SQL allows you to construct and execute SQL statements dynamically at runtime using the EXECUTE IMMEDIATE statement.
   
- EXECUTE IMMEDIATE 'CREATE TABLE my_table (id NUMBER, name VARCHAR2(50))';


PL/SQL is used extensively in Oracle Database environments for creating stored procedures, triggers, and other database-centric applications.
It enhances the capabilities of SQL by adding procedural constructs, making it a powerful tool for building complex database-driven applications.




use  case - 



CREATE TABLE employees (
   employee_id NUMBER,
   employee_name VARCHAR2(50),
   salary NUMBER,
   department_id NUMBER
);

INSERT INTO employees VALUES (1, 'John Doe', 50000, 101);
INSERT INTO employees VALUES (2, 'Jane Smith', 60000, 101);
INSERT INTO employees VALUES (3, 'Bob Johnson', 75000, 102);
-- Add more sample data as needed
`


select
  firstname,
  lastname,
  mobile_number,
  email,
  dob,
  CASE
    WHEN month = 1 THEN 'Jan'
    WHEN month = 2 THEN 'Feb'
    WHEN month = 3 THEN 'Mar'
    WHEN month = 4 THEN 'Apr'
    WHEN month = 5 THEN 'May'
    WHEN month = 6 THEN 'Jun'
    WHEN month = 7 THEN 'Jul'
    WHEN month = 8 THEN 'Aug'
    WHEN month = 9 THEN 'Sep'
    WHEN month = 10 THEN 'Oct'
    WHEN month = 11 THEN 'Nov'
    WHEN month = 12 THEN 'Dec'
    ELSE 'Unknown'
  END AS Months,
  gender,
  location
from
  (
    select
      firstname,
      lastname,
      mobile_number,
      email,
      dob,
      month(dob) as month,
      gender,
      location
    from
      precheckin_guests
    where
      precheckin_guests.id >= '88683'
      and dob is not null
    order by
      precheckin_guests.id desc
  ) a




