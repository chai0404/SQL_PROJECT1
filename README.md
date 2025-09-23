# SQL Project 1  

This is a **basic MySQL project** where I practiced database creation, table design, data insertion, and SQL queries.  
The project simulates a simple company database with **Departments, Employees, and Salary Grades**.  

---

## 📌 Database & Tables  

### Create Database
```sql
CREATE DATABASE dbt_project1;
USE dbt_project1;
CREATE TABLE dept (
    deptno INT PRIMARY KEY,
    dname VARCHAR(50),
    loc VARCHAR(50)
);
CREATE TABLE emp (
    empno INT PRIMARY KEY,
    ename VARCHAR(50),
    job VARCHAR(50),
    mgr INT,
    hiredate DATE,
    sal DECIMAL(10,2),
    comm DECIMAL(10,2),
    deptno INT,
    FOREIGN KEY (deptno) REFERENCES dept(deptno)
);
CREATE TABLE salgrade (
    grade INT PRIMARY KEY,
    losal INT,
    hisal INT
);
INSERT INTO dept VALUES (10,'ACCOUNTING','NEW YORK');
INSERT INTO dept VALUES (20,'RESEARCH','DALLAS');
INSERT INTO dept VALUES (30,'SALES','CHICAGO');
INSERT INTO dept VALUES (40,'OPERATIONS','BOSTON');
INSERT INTO emp VALUES (7839,'KING','PRESIDENT',NULL,'1981-11-17',5000,NULL,10);
INSERT INTO emp VALUES (7698,'BLAKE','MANAGER',7839,'1981-05-01',2850,NULL,30);
INSERT INTO emp VALUES (7566,'JONES','MANAGER',7839,'1981-04-02',2975,NULL,20);
INSERT INTO emp VALUES (7900,'JAMES','CLERK',7698,'1981-12-03',950,NULL,30);
INSERT INTO emp VALUES (7369,'SMITH','CLERK',7902,'1980-12-17',800,NULL,20);
INSERT INTO emp VALUES (7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30);
INSERT INTO emp VALUES (7654,'MARTIN','SALESMAN',7698,'1981-09-28',1250,1400,30);
INSERT INTO emp VALUES (7844,'TURNER','SALESMAN',7698,'1981-09-08',1500,0,30);
INSERT INTO emp VALUES (7876,'MILLER','CLERK',7698,'1982-03-15',900,NULL,20);
INSERT INTO emp VALUES (7782,'SCOTT','ANALYST',7566,'1982-12-09',3000,NULL,20);
INSERT INTO emp VALUES (7902,'FORD','ANALYST',7566,'1981-12-03',3000,NULL,20);
INSERT INTO salgrade VALUES (1,700,1200);
INSERT INTO salgrade VALUES (2,1201,1400);
INSERT INTO salgrade VALUES (3,1401,2000);
INSERT INTO salgrade VALUES (4,2001,3000);
INSERT INTO salgrade VALUES (5,3001,99999);
1. Display all employees
SELECT * FROM emp;

2. Employees with salary between 1000 and 2000
SELECT * FROM emp WHERE sal BETWEEN 1000 AND 2000;

3. Departments ordered by name
SELECT deptno, dname FROM dept ORDER BY dname;

4. Distinct job roles
SELECT DISTINCT job FROM emp;

5. Employees from dept 10 & 20 ordered by name
SELECT * FROM emp WHERE deptno IN (10,20) ORDER BY ename;

6. Clerks in Department 20
SELECT ename, job FROM emp WHERE job = 'CLERK' AND deptno = 20;

7. Employees with "TH" or "LL" in name
SELECT ename FROM emp 
WHERE UPPER(ename) LIKE '%TH%' OR UPPER(ename) LIKE '%LL%';

8. Employees with manager assigned
SELECT * FROM emp WHERE mgr IS NOT NULL;

9. Total remuneration (salary + commission)
SELECT ename, sal + COALESCE(comm,0) AS total_remuneration FROM emp;

10. Salesmen annual salary vs commission
SELECT ename, (sal * 12) AS annual_salary, COALESCE(comm,0) AS commission
FROM emp
WHERE job = 'SALESMAN' AND sal > COALESCE(comm,0)
ORDER BY sal DESC, ename ASC;

11. Employees hired in 1982
SELECT ename, hiredate FROM emp WHERE YEAR(hiredate) = 1982;

12. Concatenate employee name and job
SELECT CONCAT(ename, ' - ', job) AS "Name - Job" FROM emp;

13. Replace job title using CASE
SELECT ename, 
    CASE WHEN job = 'SALESMAN' THEN 'SALESPERSON' ELSE job END AS job
FROM emp;

🎯 Learning Outcomes

Practiced database creation in MySQL.

Created tables with Primary Key and Foreign Key constraints.

Inserted sample realistic employee & department data.

Applied SQL queries: filtering, ordering, string functions, case, joins.

Built strong fundamentals for SQL & Database Developer roles.

