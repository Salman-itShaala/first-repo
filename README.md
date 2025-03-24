# first-repo

## sql queries from string and date-time functions session

CREATE DATABASE stringDateFunction;

USE stringDateFunction;

CREATE TABLE employees(
id INT PRIMARY KEY,
name VARCHAR(50),
department VARCHAR(50),
joining_date DATE,
salary INT
);

INSERT INTO employees VALUES
(1, "John Doe", "IT", "2020-06-15", 60000),
(2, "Alice Brown", "HR", "2019-09-05", 55000),
(3,"Bob Smith", "IT", "2022-01-10", 70000),
(4, "David Clark", "Finance", "2018-03-05", 80000),
(5, "Emma White", "HR", "2021-07-25", 50000);

SELECT \* FROM employees;

SELECT name, UPPER(name) as uppercase_name FROM employees;

SELECT department, LOWER(department) FROM employees;

SELECT name,
LENGTH(name) as name_length
FROM employees
WHERE LENGTH(name) > 10;

INSERT INTO employees VALUES
(6, " SALMAN ", "IT", "2021-07-25" , 55000);

-- "SALMAN " --> RTRIM

SELECT name,
LTRIM(name) as l_trim,
RTRIM(name) as r_trim,
TRIM(name) as trim
FROM employees WHERE id = 6;

-- " SALMAN" --> LRTIM

-- " SALMAN " --> TRIM

-- SUBSTRING(string, start, no_of_chars)

SELECT name,
SUBSTRING(name, 4, 5)
FROM employees;

-- CONCAT(str1, str2, str3);

SELECT CONCAT("SALMAN", "---" ,"SHAIKH") as full_name;

-- "SALMANSHAIKH"

SELECT REPLACE("How are you??", "How", "Who") as question;

SELECT \*
FROM employees WHERE INSTR(name, "a") = 2;

SELECT NOW(); -- yyyy-mm-dd hh-mm-ss

SELECT CURDATE(); -- yyyy-mm-dd

SELECT YEAR("2025-03-24");
SELECT MONTH("2025-03-24");
SELECT DAY("2025-03-24");

SELECT \* FROM employees;

SELECT id, name, department
FROM employees
WHERE YEAR(joining_date) = "2021";

SELECT TIMESTAMPDIFF(YEAR, "2000-03-24", "2025-03-24") as yrs,
TIMESTAMPDIFF(DAY, "2000-03-24", "2025-03-24") as days,
TIMESTAMPDIFF(MONTH, "2000-03-24", "2025-03-24") as months;

SELECT DATEDIFF("2000-03-24", "2025-03-24");

SELECT DATE_ADD("2000-03-24", INTERVAL 6 DAY);

SELECT DATE_SUB(CURDATE(), INTERVAL 25 YEAR);

SELECT id, name, joining_date,
TIMESTAMPDIFF(YEAR, joining_date, CURDATE()) as no_of_yrs_worked
FROM employees;
