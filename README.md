### Nth-Highest-salary-Leetcode-solution

Table: Employee


| Column Name | Type |
|-----------  | -----
| id          | int  |
| salary      | int  |


id is the primary key column for this table.
Each row of this table contains information about the salary of an employee.
 

Write an SQL query to report the nth highest salary from the Employee table. If there is no nth highest salary, the query should report null.

The query result format is in the following example.

Example 1:

Input: 
Employee table:

| id | salary |
|----|--------|
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |

n = 2
Output: 

| getNthHighestSalary(2) |
|------------------------|
| 200                    |


Example 2:

Input: 
Employee table:

| id | salary |
|----|--------|
| 1  | 100    |

n = 2
Output: 

| getNthHighestSalary(2) |
|------------------------|
| null                   |


### MYSQL Solution
```sql
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
  RETURN (
      SELECT nth_value(salary, N) OVER()
      FROM employee
      LIMIT N,1  #Select records from Nth position and only take 1 
      
  );
END
```

