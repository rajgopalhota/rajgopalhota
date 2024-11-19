Here are **80 SQL interview questions** across various topics, with **code snippets** for queries where applicable:

---

### **Basic SQL**

1. **What is SQL?**
   - SQL (Structured Query Language) is a language used to interact with relational databases, allowing users to create, modify, query, and manage data.

2. **What is the difference between `WHERE` and `HAVING`?**
   - **WHERE** is used to filter records before aggregation.
   - **HAVING** is used to filter records after aggregation.
   
   **Example:**
   ```sql
   SELECT department, COUNT(*)
   FROM employees
   GROUP BY department
   HAVING COUNT(*) > 10;
   ```

3. **What is a SELECT statement in SQL?**
   - The `SELECT` statement is used to query the database and retrieve data.

   **Example:**
   ```sql
   SELECT first_name, last_name FROM employees;
   ```

4. **What is a `DISTINCT` keyword?**
   - The `DISTINCT` keyword is used to eliminate duplicate rows from the result set.

   **Example:**
   ```sql
   SELECT DISTINCT department FROM employees;
   ```

5. **What is a `NULL` value in SQL?**
   - `NULL` represents the absence of a value or unknown value in a column.

6. **How can you prevent SQL injection?**
   - Use **prepared statements** with bound parameters and **parameterized queries**.

7. **What is a `LIMIT` clause in SQL?**
   - The `LIMIT` clause is used to specify the number of rows to return.

   **Example:**
   ```sql
   SELECT * FROM employees LIMIT 5;
   ```

8. **What is the difference between `INNER JOIN` and `OUTER JOIN`?**
   - **INNER JOIN** returns records that have matching values in both tables.
   - **OUTER JOIN** returns records with matching values from both tables and non-matching records from one or both tables.

   **Example:**
   ```sql
   SELECT employees.name, departments.department
   FROM employees
   INNER JOIN departments ON employees.dept_id = departments.dept_id;
   ```

9. **What is a `GROUP BY` clause?**
   - The `GROUP BY` clause groups rows that have the same values into summary rows.

   **Example:**
   ```sql
   SELECT department, COUNT(*) 
   FROM employees
   GROUP BY department;
   ```

10. **What is an aggregate function in SQL?**
    - Aggregate functions perform a calculation on a set of values and return a single value.

    **Example:**
    ```sql
    SELECT AVG(salary) FROM employees;
    ```

---

### **Intermediate SQL**

11. **What is a `LEFT JOIN`?**
    - A `LEFT JOIN` returns all records from the left table and the matched records from the right table. If no match is found, `NULL` values are returned for columns of the right table.

    **Example:**
    ```sql
    SELECT employees.name, departments.department
    FROM employees
    LEFT JOIN departments ON employees.dept_id = departments.dept_id;
    ```

12. **What is a `RIGHT JOIN`?**
    - A `RIGHT JOIN` returns all records from the right table and the matched records from the left table. If no match is found, `NULL` values are returned for columns of the left table.

    **Example:**
    ```sql
    SELECT employees.name, departments.department
    FROM employees
    RIGHT JOIN departments ON employees.dept_id = departments.dept_id;
    ```

13. **What is a `FULL JOIN`?**
    - A `FULL JOIN` returns records when there is a match in either left or right table.

    **Example:**
    ```sql
    SELECT employees.name, departments.department
    FROM employees
    FULL OUTER JOIN departments ON employees.dept_id = departments.dept_id;
    ```

14. **What is a `UNION` operator?**
    - The `UNION` operator combines the results of two or more `SELECT` statements and removes duplicate rows.

    **Example:**
    ```sql
    SELECT first_name FROM employees
    UNION
    SELECT first_name FROM customers;
    ```

15. **What is a `UNION ALL` operator?**
    - `UNION ALL` combines results from two `SELECT` statements but includes duplicates.

    **Example:**
    ```sql
    SELECT first_name FROM employees
    UNION ALL
    SELECT first_name FROM customers;
    ```

16. **How do you rename a column in SQL?**
    - Use the `AS` keyword to rename a column in a `SELECT` statement.

    **Example:**
    ```sql
    SELECT first_name AS "Employee First Name" FROM employees;
    ```

17. **What is a `CASE` statement in SQL?**
    - The `CASE` statement is used to return values based on conditions.

    **Example:**
    ```sql
    SELECT first_name, 
           CASE 
               WHEN age < 18 THEN 'Minor'
               WHEN age >= 18 THEN 'Adult'
           END AS age_group
    FROM employees;
    ```

18. **What is a `SELF JOIN`?**
    - A `SELF JOIN` is a join where a table is joined with itself.

    **Example:**
    ```sql
    SELECT e1.first_name, e2.first_name
    FROM employees e1
    JOIN employees e2 ON e1.manager_id = e2.employee_id;
    ```

19. **What is a subquery?**
    - A subquery is a query nested inside another query.

    **Example:**
    ```sql
    SELECT first_name
    FROM employees
    WHERE dept_id = (SELECT dept_id FROM departments WHERE department = 'Sales');
    ```

20. **What is the difference between `DELETE` and `TRUNCATE`?**
    - **DELETE** removes rows based on a condition, while **TRUNCATE** removes all rows in a table and is faster.

    **Example:**
    ```sql
    DELETE FROM employees WHERE employee_id = 5;
    ```

    ```sql
    TRUNCATE TABLE employees;
    ```

---

### **Advanced SQL**

21. **What is an index in SQL?**
    - An index improves the speed of data retrieval operations on a database table at the cost of additional space and slower write operations.

    **Example:**
    ```sql
    CREATE INDEX idx_employee_name ON employees(first_name);
    ```

22. **What is normalization?**
    - Normalization is the process of organizing the fields and tables of a database to minimize redundancy and dependency.

23. **What is denormalization?**
    - Denormalization is the process of combining tables to improve query performance at the cost of redundancy.

24. **What are the different normal forms?**
    - **1NF**: Eliminate repeating groups.
    - **2NF**: Remove partial dependency.
    - **3NF**: Remove transitive dependency.

25. **What is a `TRIGGER` in SQL?**
    - A trigger is a set of SQL statements automatically executed when a specified event occurs in a table.

    **Example:**
    ```sql
    CREATE TRIGGER update_employee
    AFTER UPDATE ON employees
    FOR EACH ROW
    BEGIN
       INSERT INTO employee_audit (employee_id, action)
       VALUES (OLD.employee_id, 'Updated');
    END;
    ```

26. **What is a stored procedure in SQL?**
    - A stored procedure is a precompiled collection of one or more SQL statements that can be executed repeatedly.

    **Example:**
    ```sql
    CREATE PROCEDURE GetEmployeeInfo (IN emp_id INT)
    BEGIN
       SELECT * FROM employees WHERE employee_id = emp_id;
    END;
    ```

27. **What is a function in SQL?**
    - A function is a stored routine that can return a single value and can be used in queries.

    **Example:**
    ```sql
    CREATE FUNCTION GetEmployeeCount() 
    RETURNS INT
    BEGIN
       RETURN (SELECT COUNT(*) FROM employees);
    END;
    ```

28. **What is the difference between `WHERE` and `HAVING`?**
    - `WHERE` filters rows before aggregation, while `HAVING` filters after aggregation.

29. **What is the `ROLLBACK` command in SQL?**
    - The `ROLLBACK` command undoes changes made by a transaction.

    **Example:**
    ```sql
    ROLLBACK;
    ```

30. **What is the `COMMIT` command in SQL?**
    - The `COMMIT` command saves all changes made during a transaction.

    **Example:**
    ```sql
    COMMIT;
    ```

---

### **Database Design & Constraints**

31. **What is a primary key?**
    - A primary key uniquely identifies each record in a table.

    **Example:**
    ```sql
    CREATE TABLE employees (
        employee_id INT PRIMARY KEY,
        first_name VARCHAR(50),
        last_name VARCHAR(50)
    );
    ```

32. **What is a foreign key?**
    - A foreign key is a column that creates a relationship between two tables.

    **Example:**
    ```sql
    CREATE TABLE orders (
        order_id INT PRIMARY KEY,
        customer_id INT,
        FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
    );
    ```

33. **What are the types of constraints in SQL?**
    - **NOT NULL**
    - **UNIQUE**
    - **PRIMARY

 KEY**
    - **FOREIGN KEY**
    - **CHECK**
    - **DEFAULT**

34. **What is an entity relationship diagram (ERD)?**
    - An ERD visually represents the structure of a database, showing entities and relationships.

35. **What is a composite key?**
    - A composite key is a primary key composed of two or more columns.

Here are more SQL questions, continuing from where we left off:

---

### **Advanced SQL (Continued)**

36. **What is a recursive query in SQL?**
   - A recursive query is one that refers to itself in order to retrieve hierarchical data, often used with Common Table Expressions (CTEs).

   **Example:**
   ```sql
   WITH RECURSIVE EmployeeHierarchy AS (
       SELECT employee_id, manager_id, first_name
       FROM employees
       WHERE manager_id IS NULL
       UNION ALL
       SELECT e.employee_id, e.manager_id, e.first_name
       FROM employees e
       INNER JOIN EmployeeHierarchy eh ON e.manager_id = eh.employee_id
   )
   SELECT * FROM EmployeeHierarchy;
   ```

37. **What is a Common Table Expression (CTE)?**
   - A CTE is a temporary result set that can be referenced within a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement.

   **Example:**
   ```sql
   WITH DepartmentCount AS (
       SELECT department_id, COUNT(*) AS total_employees
       FROM employees
       GROUP BY department_id
   )
   SELECT * FROM DepartmentCount WHERE total_employees > 10;
   ```

38. **What is a window function in SQL?**
   - Window functions perform calculations across a set of rows related to the current row, without collapsing the result set.

   **Example:**
   ```sql
   SELECT employee_id, salary, 
          RANK() OVER (ORDER BY salary DESC) AS salary_rank
   FROM employees;
   ```

39. **What is the `COALESCE` function in SQL?**
   - The `COALESCE` function returns the first non-NULL expression from the list of expressions.

   **Example:**
   ```sql
   SELECT COALESCE(middle_name, 'N/A') AS middle_name FROM employees;
   ```

40. **What is the `NULLIF` function in SQL?**
   - The `NULLIF` function compares two expressions and returns `NULL` if they are equal; otherwise, it returns the first expression.

   **Example:**
   ```sql
   SELECT NULLIF(5, 5) AS result;  -- Returns NULL
   SELECT NULLIF(5, 6) AS result;  -- Returns 5
   ```

41. **What is the `EXISTS` clause in SQL?**
   - The `EXISTS` clause checks if a subquery returns any result. It returns `TRUE` if the subquery returns at least one record, otherwise `FALSE`.

   **Example:**
   ```sql
   SELECT first_name, last_name
   FROM employees
   WHERE EXISTS (SELECT 1 FROM departments WHERE employees.dept_id = departments.dept_id);
   ```

42. **What is the `IN` clause in SQL?**
   - The `IN` clause is used to filter the result set by matching values in a list or subquery.

   **Example:**
   ```sql
   SELECT first_name, last_name
   FROM employees
   WHERE department IN ('Sales', 'Marketing');
   ```

43. **What is the difference between `INNER JOIN` and `LEFT JOIN` in SQL?**
   - **INNER JOIN** returns only the rows where there is a match in both tables.
   - **LEFT JOIN** returns all rows from the left table, and matched rows from the right table; for non-matching rows, `NULL` values are returned for the right table columns.

   **Example:**
   ```sql
   SELECT e.name, d.department
   FROM employees e
   LEFT JOIN departments d ON e.dept_id = d.dept_id;
   ```

44. **What is a cross join in SQL?**
   - A `CROSS JOIN` returns the Cartesian product of two tables, i.e., every row from the first table is combined with every row from the second table.

   **Example:**
   ```sql
   SELECT employees.name, departments.department
   FROM employees
   CROSS JOIN departments;
   ```

45. **What are `TRANSACTION` commands in SQL?**
   - Transaction commands ensure the atomicity of SQL operations. These include:
     - **START TRANSACTION**: Begins a transaction.
     - **COMMIT**: Saves all changes made during the transaction.
     - **ROLLBACK**: Undoes all changes made during the transaction.

   **Example:**
   ```sql
   START TRANSACTION;
   UPDATE employees SET salary = salary + 1000 WHERE employee_id = 1;
   COMMIT;
   ```

46. **What is a `VIEW` in SQL?**
   - A `VIEW` is a virtual table created by a query joining one or more tables, and it can be used like a regular table in queries.

   **Example:**
   ```sql
   CREATE VIEW EmployeeView AS
   SELECT employee_id, first_name, last_name FROM employees WHERE status = 'Active';
   ```

47. **What is the difference between `VIEW` and `MATERIALIZED VIEW`?**
   - **VIEW**: A virtual table created by a `SELECT` query.
   - **MATERIALIZED VIEW**: Similar to a view, but it stores the query result physically, improving performance at the cost of storage and freshness.

48. **What is an `AUTO_INCREMENT` in SQL?**
   - `AUTO_INCREMENT` is used to automatically generate unique numeric values for primary key columns.

   **Example:**
   ```sql
   CREATE TABLE employees (
       employee_id INT AUTO_INCREMENT PRIMARY KEY,
       first_name VARCHAR(50)
   );
   ```

49. **What is the `TRUNCATE` command in SQL?**
   - The `TRUNCATE` command is used to delete all rows from a table, but it does not log individual row deletions.

   **Example:**
   ```sql
   TRUNCATE TABLE employees;
   ```

50. **What is a `CHECK` constraint in SQL?**
   - The `CHECK` constraint is used to limit the range of values that can be stored in a column.

   **Example:**
   ```sql
   CREATE TABLE employees (
       employee_id INT PRIMARY KEY,
       salary DECIMAL CHECK (salary > 0)
   );
   ```

---

### **Performance Optimization**

51. **What is query optimization in SQL?**
   - Query optimization is the process of improving the performance of a query by rewriting it, using indexes, or modifying database schema.

52. **What is an index in SQL and why is it used?**
   - An index is a data structure that improves the speed of data retrieval operations on a database table.

   **Example:**
   ```sql
   CREATE INDEX idx_employee_name ON employees(first_name);
   ```

53. **What is the `EXPLAIN` keyword used for in SQL?**
   - The `EXPLAIN` keyword shows the execution plan for a SQL query, helping identify how the query will be executed.

   **Example:**
   ```sql
   EXPLAIN SELECT * FROM employees WHERE first_name = 'John';
   ```

54. **What are `Joins` and why are they important for performance optimization?**
   - `Joins` combine data from two or more tables. Optimizing joins, using appropriate indexes, and avoiding unnecessary joins are key to improving query performance.

55. **What is denormalization and when should it be used?**
   - Denormalization involves merging tables to improve query performance at the cost of data redundancy. It is used when the query performance is more important than data normalization.

56. **What is a partition in SQL?**
   - Partitioning divides a table into smaller, manageable pieces, but still allows it to be treated as a single table. It helps with performance in large tables.

57. **What is a foreign key index and why is it important?**
   - An index on a foreign key column improves the performance of `JOIN` queries by speeding up lookups and enforcing referential integrity.

58. **What is `EXPLAIN ANALYZE` in SQL?**
   - `EXPLAIN ANALYZE` provides detailed information about the query execution plan and actual runtime statistics.

   **Example:**
   ```sql
   EXPLAIN ANALYZE SELECT * FROM employees WHERE department = 'Sales';
   ```

59. **What is the importance of query profiling?**
   - Query profiling is essential for understanding how a query performs, identifying bottlenecks, and improving execution times.

60. **What is a database normalization?**
   - Database normalization is the process of organizing a relational database to reduce redundancy and improve data integrity.

61. **What are the disadvantages of using too many indexes?**
   - While indexes improve query performance, too many indexes can slow down `INSERT`, `UPDATE`, and `DELETE` operations due to the overhead of maintaining indexes.

62. **What is database sharding?**
   - Sharding is the process of splitting large datasets into smaller, more manageable pieces, called shards, often to improve scalability.

63. **What is a stored procedure and how does it affect performance?**
   - A stored procedure is a precompiled set of SQL statements that can be reused. It reduces the amount of code sent to the database, improving performance.

64. **What are database triggers and how do they affect performance?**
   - Triggers automatically execute SQL code in response to certain events on a table. While useful, they can affect performance if not optimized properly.

---

### **Advanced Queries**

65. **How do you find the second highest salary from the `employees` table?**
   - Using a subquery:
   ```sql
   SELECT MAX(salary) 
   FROM employees 
   WHERE salary <

 (SELECT MAX(salary) FROM employees);
   ```

66. **How do you calculate the running total in SQL?**
   - Using a window function:
   ```sql
   SELECT employee_id, salary,
          SUM(salary) OVER (ORDER BY employee_id) AS running_total
   FROM employees;
   ```

67. **How do you find duplicate records in a table?**
   ```sql
   SELECT first_name, last_name, COUNT(*)
   FROM employees
   GROUP BY first_name, last_name
   HAVING COUNT(*) > 1;
   ```

68. **How can you find the common records between two tables?**
   ```sql
   SELECT * 
   FROM employees
   WHERE employee_id IN (SELECT employee_id FROM employees_archive);
   ```

69. **How can you find the number of records in each department?**
   ```sql
   SELECT department_id, COUNT(*) 
   FROM employees
   GROUP BY department_id;
   ```

70. **How do you retrieve all columns of a table?**
   ```sql
   SELECT * FROM employees;
   ```

71. **How can you find the first and last record in a table?**
   ```sql
   SELECT * FROM employees ORDER BY employee_id LIMIT 1;  -- First record
   SELECT * FROM employees ORDER BY employee_id DESC LIMIT 1;  -- Last record
   ```

72. **How do you compare two tables to check for differences?**
   - Using `EXCEPT`:
   ```sql
   SELECT * FROM table1
   EXCEPT
   SELECT * FROM table2;
   ```

73. **How can you find the highest salary in each department?**
   ```sql
   SELECT department_id, MAX(salary)
   FROM employees
   GROUP BY department_id;
   ```

74. **How do you perform a self-join?**
   ```sql
   SELECT a.employee_id, a.first_name, b.first_name AS manager_name
   FROM employees a
   JOIN employees b ON a.manager_id = b.employee_id;
   ```

75. **How do you find the average salary per department?**
   ```sql
   SELECT department_id, AVG(salary)
   FROM employees
   GROUP BY department_id;
   ```

Here are the next set of 30 SQL code snippets covering various topics:

---

### **SQL Code Snippets**

76. **Get all employees who do not have a manager (NULL manager_id):**
   ```sql
   SELECT * FROM employees
   WHERE manager_id IS NULL;
   ```

77. **Get employees whose salary is between $50,000 and $80,000:**
   ```sql
   SELECT * FROM employees
   WHERE salary BETWEEN 50000 AND 80000;
   ```

78. **Get all departments with more than 10 employees:**
   ```sql
   SELECT department_id, COUNT(*) AS total_employees
   FROM employees
   GROUP BY department_id
   HAVING COUNT(*) > 10;
   ```

79. **Get the names of employees who earn more than their manager:**
   ```sql
   SELECT e1.first_name, e2.first_name AS manager_name
   FROM employees e1
   JOIN employees e2 ON e1.manager_id = e2.employee_id
   WHERE e1.salary > e2.salary;
   ```

80. **Get the highest paid employee in each department:**
   ```sql
   SELECT department_id, MAX(salary) AS highest_salary
   FROM employees
   GROUP BY department_id;
   ```

81. **Get the total salary expense for each department:**
   ```sql
   SELECT department_id, SUM(salary) AS total_salary_expense
   FROM employees
   GROUP BY department_id;
   ```

82. **Update the salary of an employee:**
   ```sql
   UPDATE employees
   SET salary = salary + 5000
   WHERE employee_id = 1;
   ```

83. **Delete an employee from the employees table:**
   ```sql
   DELETE FROM employees
   WHERE employee_id = 10;
   ```

84. **Get employees who joined after 2020:**
   ```sql
   SELECT * FROM employees
   WHERE hire_date > '2020-01-01';
   ```

85. **Get the first 5 employees from the employees table:**
   ```sql
   SELECT * FROM employees
   LIMIT 5;
   ```

86. **Get the last 5 employees from the employees table:**
   ```sql
   SELECT * FROM employees
   ORDER BY employee_id DESC
   LIMIT 5;
   ```

87. **Find all employees who have the same first and last name:**
   ```sql
   SELECT * FROM employees
   WHERE first_name = last_name;
   ```

88. **Find all employees who have not been assigned to a department:**
   ```sql
   SELECT * FROM employees
   WHERE department_id IS NULL;
   ```

89. **Get employees who are also managers (have subordinates):**
   ```sql
   SELECT DISTINCT manager_id
   FROM employees
   WHERE manager_id IS NOT NULL;
   ```

90. **Get the number of employees in each department, including those with no department:**
   ```sql
   SELECT department_id, COUNT(*) AS total_employees
   FROM employees
   GROUP BY department_id
   WITH ROLLUP;
   ```

91. **Get the employees who earn the minimum salary:**
   ```sql
   SELECT * FROM employees
   WHERE salary = (SELECT MIN(salary) FROM employees);
   ```

92. **Get the employees with the third highest salary:**
   ```sql
   SELECT * FROM employees
   WHERE salary = (SELECT DISTINCT salary FROM employees ORDER BY salary DESC LIMIT 1 OFFSET 2);
   ```

93. **Get employees who joined in the last 6 months:**
   ```sql
   SELECT * FROM employees
   WHERE hire_date > CURRENT_DATE - INTERVAL 6 MONTH;
   ```

94. **Find all employees who have a salary greater than the average salary:**
   ```sql
   SELECT * FROM employees
   WHERE salary > (SELECT AVG(salary) FROM employees);
   ```

95. **Join two tables to get employee names and department names:**
   ```sql
   SELECT e.first_name, e.last_name, d.department_name
   FROM employees e
   JOIN departments d ON e.department_id = d.department_id;
   ```

96. **Get employees who earn more than $50,000 and belong to the 'IT' department:**
   ```sql
   SELECT * FROM employees
   WHERE salary > 50000 AND department = 'IT';
   ```

97. **Create a new employee record:**
   ```sql
   INSERT INTO employees (first_name, last_name, salary, department_id)
   VALUES ('John', 'Doe', 60000, 3);
   ```

98. **Find all employees with a salary greater than 70% of the highest salary:**
   ```sql
   SELECT * FROM employees
   WHERE salary > (SELECT MAX(salary) * 0.7 FROM employees);
   ```

99. **Get the average salary per department, ordered by average salary:**
   ```sql
   SELECT department_id, AVG(salary) AS average_salary
   FROM employees
   GROUP BY department_id
   ORDER BY average_salary DESC;
   ```

100. **Check if any employees are assigned to more than one department (using a self-join):**
   ```sql
   SELECT e1.employee_id, e1.first_name, e2.department_id
   FROM employees e1
   JOIN employees e2 ON e1.employee_id = e2.employee_id AND e1.department_id != e2.department_id;
   ```

101. **Get a list of employees who have worked in both 'HR' and 'Finance' departments:**
   ```sql
   SELECT e.employee_id, e.first_name
   FROM employees e
   WHERE e.department_id IN (SELECT department_id FROM departments WHERE department_name IN ('HR', 'Finance'))
   GROUP BY e.employee_id, e.first_name
   HAVING COUNT(DISTINCT e.department_id) = 2;
   ```

102. **Create a table for employees with foreign keys:**
   ```sql
   CREATE TABLE employees (
       employee_id INT PRIMARY KEY,
       first_name VARCHAR(50),
       last_name VARCHAR(50),
       department_id INT,
       FOREIGN KEY (department_id) REFERENCES departments(department_id)
   );
   ```

103. **Get the top 3 highest paid employees:**
   ```sql
   SELECT * FROM employees
   ORDER BY salary DESC
   LIMIT 3;
   ```

104. **Add a new column to an existing table:**
   ```sql
   ALTER TABLE employees
   ADD date_of_birth DATE;
   ```

105. **Update an employee's department:**
   ```sql
   UPDATE employees
   SET department_id = 4
   WHERE employee_id = 10;
   ```

106. **Find employees who do not have a salary (NULL salary):**
   ```sql
   SELECT * FROM employees
   WHERE salary IS NULL;
   ```

107. **Find employees who have both 'Manager' and 'Sales' roles (use `OR` condition):**
   ```sql
   SELECT * FROM employees
   WHERE role = 'Manager' OR role = 'Sales';
   ```

108. **Retrieve the last record from a sorted table using `ORDER BY` and `LIMIT`:**
   ```sql
   SELECT * FROM employees
   ORDER BY employee_id DESC
   LIMIT 1;
   ```

109. **Get employees who have not received any bonus (assuming `bonus` column exists):**
   ```sql
   SELECT * FROM employees
   WHERE bonus IS NULL;
   ```

110. **Select all columns from `employees` and join with `departments` where department name is 'Sales':**
   ```sql
   SELECT e.*, d.department_name
   FROM employees e
   JOIN departments d ON e.department_id = d.department_id
   WHERE d.department_name = 'Sales';
   ```

Here are additional SQL code snippets to continue from the previous list:

---

### **SQL Code Snippets (Continued)**

111. **Find employees whose name starts with the letter 'A':**
   ```sql
   SELECT * FROM employees
   WHERE first_name LIKE 'A%';
   ```

112. **Get a list of employees with a specific role using `IN` clause:**
   ```sql
   SELECT * FROM employees
   WHERE role IN ('Manager', 'Team Lead', 'Developer');
   ```

113. **Get employees with the same salary as a specific employee (e.g., employee_id = 5):**
   ```sql
   SELECT * FROM employees
   WHERE salary = (SELECT salary FROM employees WHERE employee_id = 5);
   ```

114. **Find employees who have not been assigned any department:**
   ```sql
   SELECT * FROM employees
   WHERE department_id IS NULL;
   ```

115. **List all employees who report to a specific manager (e.g., manager_id = 3):**
   ```sql
   SELECT * FROM employees
   WHERE manager_id = 3;
   ```

116. **Count the total number of employees in each department:**
   ```sql
   SELECT department_id, COUNT(*) AS total_employees
   FROM employees
   GROUP BY department_id;
   ```

117. **Find the average salary in each department excluding the 'HR' department:**
   ```sql
   SELECT department_id, AVG(salary) AS average_salary
   FROM employees
   WHERE department_id != (SELECT department_id FROM departments WHERE department_name = 'HR')
   GROUP BY department_id;
   ```

118. **Update the salary for employees who have worked for more than 5 years:**
   ```sql
   UPDATE employees
   SET salary = salary + 2000
   WHERE hire_date <= CURRENT_DATE - INTERVAL 5 YEAR;
   ```

119. **Find all employees who have been with the company for more than 3 years:**
   ```sql
   SELECT * FROM employees
   WHERE hire_date <= CURRENT_DATE - INTERVAL 3 YEAR;
   ```

120. **Get the maximum salary in each department:**
   ```sql
   SELECT department_id, MAX(salary) AS max_salary
   FROM employees
   GROUP BY department_id;
   ```

121. **Find employees who are not managers (i.e., their employee_id does not appear in manager_id):**
   ```sql
   SELECT * FROM employees
   WHERE employee_id NOT IN (SELECT manager_id FROM employees WHERE manager_id IS NOT NULL);
   ```

122. **Get employees who joined between two specific dates:**
   ```sql
   SELECT * FROM employees
   WHERE hire_date BETWEEN '2022-01-01' AND '2023-12-31';
   ```

123. **Delete all employees in a specific department (e.g., department_id = 4):**
   ```sql
   DELETE FROM employees
   WHERE department_id = 4;
   ```

124. **Get a list of departments with at least one employee:**
   ```sql
   SELECT department_id, department_name
   FROM departments
   WHERE department_id IN (SELECT DISTINCT department_id FROM employees);
   ```

125. **Get the total number of employees in each department and show the department name:**
   ```sql
   SELECT d.department_name, COUNT(e.employee_id) AS total_employees
   FROM departments d
   LEFT JOIN employees e ON d.department_id = e.department_id
   GROUP BY d.department_name;
   ```

126. **Get all employees who share the same last name:**
   ```sql
   SELECT last_name, COUNT(*) AS count
   FROM employees
   GROUP BY last_name
   HAVING COUNT(*) > 1;
   ```

127. **Create a table for storing sales orders with foreign keys referencing employees:**
   ```sql
   CREATE TABLE sales_orders (
       order_id INT PRIMARY KEY,
       employee_id INT,
       order_date DATE,
       total_amount DECIMAL(10, 2),
       FOREIGN KEY (employee_id) REFERENCES employees(employee_id)
   );
   ```

128. **Find employees who earn more than the average salary in their department:**
   ```sql
   SELECT e.first_name, e.last_name, e.salary, e.department_id
   FROM employees e
   WHERE e.salary > (SELECT AVG(salary) FROM employees WHERE department_id = e.department_id);
   ```

129. **List all employees who have no bonus (assuming the `bonus` column exists):**
   ```sql
   SELECT * FROM employees
   WHERE bonus IS NULL;
   ```

130. **Get employees who have been promoted (i.e., their job title has changed):**
   ```sql
   SELECT * FROM employees
   WHERE previous_role IS NOT NULL;
   ```

131. **Get the total salary expense for all employees in each department:**
   ```sql
   SELECT department_id, SUM(salary) AS total_salary_expense
   FROM employees
   GROUP BY department_id;
   ```

132. **Get the number of employees who have been assigned to more than one department:**
   ```sql
   SELECT employee_id, COUNT(DISTINCT department_id) AS num_departments
   FROM employees
   GROUP BY employee_id
   HAVING num_departments > 1;
   ```

133. **Get employees who have not received a salary increase in the last 2 years:**
   ```sql
   SELECT * FROM employees
   WHERE last_salary_increase <= CURRENT_DATE - INTERVAL 2 YEAR;
   ```

134. **Get the details of employees who belong to a specific department and have a salary greater than a threshold:**
   ```sql
   SELECT * FROM employees
   WHERE department_id = 2 AND salary > 50000;
   ```

135. **Add a column for employee performance rating in the `employees` table:**
   ```sql
   ALTER TABLE employees
   ADD performance_rating INT;
   ```

136. **Get the top 5 highest salaries from the employees table:**
   ```sql
   SELECT * FROM employees
   ORDER BY salary DESC
   LIMIT 5;
   ```

137. **Find employees who work in either the 'IT' or 'HR' departments:**
   ```sql
   SELECT * FROM employees
   WHERE department IN ('IT', 'HR');
   ```

138. **Get employees who were hired in the last 30 days:**
   ```sql
   SELECT * FROM employees
   WHERE hire_date > CURRENT_DATE - INTERVAL 30 DAY;
   ```

139. **Get employees who have a certain keyword in their job titles:**
   ```sql
   SELECT * FROM employees
   WHERE job_title LIKE '%Manager%';
   ```

140. **Find the second highest salary from the employees table:**
   ```sql
   SELECT MAX(salary) AS second_highest_salary
   FROM employees
   WHERE salary < (SELECT MAX(salary) FROM employees);
   ```
