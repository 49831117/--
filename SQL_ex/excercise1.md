# SQL
> [線上SQL](http://sqlfiddle.com/)

## 建立表格、插入資料

```SQL
CREATE TABLE DEPARTMENTS(
  department_id INT,
  name varchar(50)
);

INSERT INTO `DEPARTMENTS` (`department_id`, `name`) VALUES
  ('1', 'IT'),
  ('2', 'HR'),
  ('3', 'Sales'),
  ('4', 'Marketing');

CREATE TABLE EMPLOYEES(
  employee_id INT,
  department_id INT,
  manager_id char(1),
  name varchar(50),
  salary INT
);

INSERT INTO `EMPLOYEES` (`employee_id`, `department_id`, `manager_id`, `name`, `salary`) VALUES
  ('1', '1', '', 'Dale', '100000'),
  ('2', '1', '1', 'Ben', '100000'),
  ('3', '1', '1', 'Aaron', '90000'),
  ('4', '2', '5', 'Phoenix', '250000'),
  ('5', '2', '', 'Lyot', '200000'),
  ('6', '1', '5', 'Joseph', '90000');
  
```

> Output
> - Table 1：DEPARTMENTS
> 
>  |department_id|name|
>  |:----:|:----:|
>  |1|IT|
>  |2|HR|
>  |3|Sales|
>  |4|Marketing|
> 
> - Table 2：EMPLOYEES
> 
>  |employee_id|department_id|manager_id|name|salary|
>  |:----:|:----:|:----:|:----:|:----:|
>  |1|1||Dale|100000|
>  |2|1|1|Ben|100000|
>  |3|1|1|Aaron|90000|
>  |4|2|5|Phoenix|250000|
>  |5|2||Lyot|200000|
>  |6|1|5|Joseph|90000|

- Data description: 
    - employee_id:1 is the manager of department_id:1
    - employee_id:5 is the manager of department_id:2

## Q1：Query employees (name) who have a bigger salary than their manager
```SQL
SELECT name
FROM EMPLOYEES e
WHERE e.salary > ( SELECT m.salary 
                   FROM EMPLOYEES m 
                   WHERE e.manager_id = m.employee_id);
```
## Q2：Query employees(name) who have the biggest salary in their departments
```SQL
SELECT
    DEPARTMENTS.name AS department,
    EMPLOYEES.name AS employee,
    salary
FROM
    EMPLOYEES JOIN DEPARTMENTS ON EMPLOYEES.department_id = DEPARTMENTS.department_id
WHERE
    (EMPLOYEES.department_id, salary) IN
    (SELECT department_id, MAX(salary) FROM EMPLOYEES GROUP BY department_id)

```
