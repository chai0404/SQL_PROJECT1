# SQL_PROJECT1

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| ass1               |
| assignment         |
| chaitanya12        |
| chaitu1            |
| cjcdac1            |
| dbexam1            |
| information_schema |
| instagram          |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| world              |
+--------------------+
13 rows in set (0.04 sec)

mysql> create database dbt_project1;
Query OK, 1 row affected (0.09 sec)

mysql> use dbt_project1;
Database changed
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| ass1               |
| assignment         |
| chaitanya12        |
| chaitu1            |
| cjcdac1            |
| dbexam1            |
| dbt_project1       |
| information_schema |
| instagram          |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| world              |
+--------------------+
14 rows in set (0.00 sec)

mysql> use dbt_project1;
Database changed
mysql> CREATE TABLE dept (
    ->     deptno INT PRIMARY KEY,
    ->     dname VARCHAR(50),
    ->     loc VARCHAR(50)
    -> );
Query OK, 0 rows affected (0.09 sec)

mysql>
mysql> CREATE TABLE emp (
    ->     empno INT PRIMARY KEY,
    ->     ename VARCHAR(50),
    ->     job VARCHAR(50),
    ->     mgr INT,
    ->     hiredate DATE,
    ->     sal DECIMAL(10,2),
    ->     comm DECIMAL(10,2),
    ->     deptno INT,
    ->     FOREIGN KEY (deptno) REFERENCES dept(deptno)
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql>
mysql> CREATE TABLE salgrade (
    ->     grade INT PRIMARY KEY,
    ->     losal INT,
    ->     hisal INT
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql> INSERT INTO dept VALUES (10,'ACCOUNTING','NEW YORK');
Query OK, 1 row affected (0.06 sec)

mysql> INSERT INTO dept VALUES (20,'RESEARCH','DALLAS');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO dept VALUES (30,'SALES','CHICAGO');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO dept VALUES (40,'OPERATIONS','BOSTON');
Query OK, 1 row affected (0.00 sec)

mysql>
mysql> INSERT INTO emp VALUES (7839,'KING','PRESIDENT',NULL,'1981-11-17',5000,NULL,10);
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO emp VALUES (7698,'BLAKE','MANAGER',7839,'1981-05-01',2850,NULL,30);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO emp VALUES (7566,'JONES','MANAGER',7839,'1981-04-02',2975,NULL,20);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO emp VALUES (7900,'JAMES','CLERK',7698,'1981-12-03',950,NULL,30);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO emp VALUES (7369,'SMITH','CLERK',7902,'1980-12-17',800,NULL,20);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO emp VALUES (7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO emp VALUES (7654,'MARTIN','SALESMAN',7698,'1981-09-28',1250,1400,30);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO emp VALUES (7844,'TURNER','SALESMAN',7698,'1981-09-08',1500,0,30);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO emp VALUES (7876,'MILLER','CLERK',7698,'1982-03-15',900,NULL,20);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO emp VALUES (7782,'SCOTT','ANALYST',7566,'1982-12-09',3000,NULL,20);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO emp VALUES (7902,'FORD','ANALYST',7566,'1981-12-03',3000,NULL,20);
Query OK, 1 row affected (0.00 sec)

mysql>
mysql> INSERT INTO salgrade VALUES (1,700,1200);
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO salgrade VALUES (2,1201,1400);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO salgrade VALUES (3,1401,2000);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO salgrade VALUES (4,2001,3000);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO salgrade VALUES (5,3001,99999);
Query OK, 1 row affected (0.00 sec)

mysql> SELECT * FROM salgrade;
+-------+-------+-------+
| grade | losal | hisal |
+-------+-------+-------+
|     1 |   700 |  1200 |
|     2 |  1201 |  1400 |
|     3 |  1401 |  2000 |
|     4 |  2001 |  3000 |
|     5 |  3001 | 99999 |
+-------+-------+-------+
5 rows in set (0.00 sec)

mysql> SELECT * FROM emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
|  7782 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000.00 |    NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
|  7876 | MILLER | CLERK     | 7698 | 1982-03-15 |  900.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
+-------+--------+-----------+------+------------+---------+---------+--------+
11 rows in set (0.00 sec)

mysql> SELECT * FROM dept;
+--------+------------+----------+
| deptno | dname      | loc      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
4 rows in set (0.00 sec)

mysql> SELECT * FROM emp WHERE sal BETWEEN 1000 AND 2000;
+-------+--------+----------+------+------------+---------+---------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7499 | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
+-------+--------+----------+------+------------+---------+---------+--------+
3 rows in set (0.00 sec)

mysql> SELECT deptno, dname FROM dept ORDER BY dname;
+--------+------------+
| deptno | dname      |
+--------+------------+
|     10 | ACCOUNTING |
|     40 | OPERATIONS |
|     20 | RESEARCH   |
|     30 | SALES      |
+--------+------------+
4 rows in set (0.00 sec)

mysql> SELECT DISTINCT job FROM emp;
+-----------+
| job       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
+-----------+
5 rows in set (0.00 sec)

mysql> SELECT * FROM emp WHERE deptno IN (10,20) ORDER BY ename;
+-------+--------+-----------+------+------------+---------+------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm | deptno |
+-------+--------+-----------+------+------------+---------+------+--------+
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 | NULL |     20 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 | NULL |     10 |
|  7876 | MILLER | CLERK     | 7698 | 1982-03-15 |  900.00 | NULL |     20 |
|  7782 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000.00 | NULL |     20 |
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800.00 | NULL |     20 |
+-------+--------+-----------+------+------------+---------+------+--------+
6 rows in set (0.00 sec)

mysql> SELECT ename, job FROM emp WHERE job = 'CLERK' AND deptno = 20;
+--------+-------+
| ename  | job   |
+--------+-------+
| SMITH  | CLERK |
| MILLER | CLERK |
+--------+-------+
2 rows in set (0.00 sec)

mysql> SELECT ename FROM emp
    -> WHERE UPPER(ename) LIKE '%TH%' OR UPPER(ename) LIKE '%LL%';
+--------+
| ename  |
+--------+
| SMITH  |
| ALLEN  |
| MILLER |
+--------+
3 rows in set (0.05 sec)

mysql> SELECT * FROM emp WHERE mgr IS NOT NULL;
+-------+--------+----------+------+------------+---------+---------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK    | 7902 | 1980-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
|  7566 | JONES  | MANAGER  | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
|  7782 | SCOTT  | ANALYST  | 7566 | 1982-12-09 | 3000.00 |    NULL |     20 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
|  7876 | MILLER | CLERK    | 7698 | 1982-03-15 |  900.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST  | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
+-------+--------+----------+------+------------+---------+---------+--------+
10 rows in set (0.00 sec)

mysql> SELECT ename, sal + COALESCE(comm,0) AS total_remuneration FROM emp;
+--------+--------------------+
| ename  | total_remuneration |
+--------+--------------------+
| SMITH  |             800.00 |
| ALLEN  |            1900.00 |
| JONES  |            2975.00 |
| MARTIN |            2650.00 |
| BLAKE  |            2850.00 |
| SCOTT  |            3000.00 |
| KING   |            5000.00 |
| TURNER |            1500.00 |
| MILLER |             900.00 |
| JAMES  |             950.00 |
| FORD   |            3000.00 |
+--------+--------------------+
11 rows in set (0.00 sec)

mysql> SELECT ename,
    ->        (sal * 12) AS annual_salary,
    ->        COALESCE(comm,0) AS commission
    -> FROM emp
    -> WHERE job = 'SALESMAN' AND sal > COALESCE(comm,0)
    -> ORDER BY sal DESC, ename ASC;
+--------+---------------+------------+
| ename  | annual_salary | commission |
+--------+---------------+------------+
| ALLEN  |      19200.00 |     300.00 |
| TURNER |      18000.00 |       0.00 |
+--------+---------------+------------+
2 rows in set (0.00 sec)

mysql> SELECT ename, hiredate FROM emp WHERE YEAR(hiredate) = 1982;
+--------+------------+
| ename  | hiredate   |
+--------+------------+
| SCOTT  | 1982-12-09 |
| MILLER | 1982-03-15 |
+--------+------------+
2 rows in set (0.00 sec)

mysql> SELECT CONCAT(ename, ' - ', job) AS `Name - Job` FROM emp;
+-------------------+
| Name - Job        |
+-------------------+
| SMITH - CLERK     |
| ALLEN - SALESMAN  |
| JONES - MANAGER   |
| MARTIN - SALESMAN |
| BLAKE - MANAGER   |
| SCOTT - ANALYST   |
| KING - PRESIDENT  |
| TURNER - SALESMAN |
| MILLER - CLERK    |
| JAMES - CLERK     |
| FORD - ANALYST    |
+-------------------+
11 rows in set (0.05 sec)

mysql> SELECT CONCAT(ename, ' (', job, ')') AS `Name (Job)` FROM emp;
+-------------------+
| Name (Job)        |
+-------------------+
| SMITH (CLERK)     |
| ALLEN (SALESMAN)  |
| JONES (MANAGER)   |
| MARTIN (SALESMAN) |
| BLAKE (MANAGER)   |
| SCOTT (ANALYST)   |
| KING (PRESIDENT)  |
| TURNER (SALESMAN) |
| MILLER (CLERK)    |
| JAMES (CLERK)     |
| FORD (ANALYST)    |
+-------------------+
11 rows in set (0.00 sec)

mysql> SELECT ename,
    ->        CASE WHEN job = 'SALESMAN' THEN 'SALESPERSON' ELSE job END AS job
    -> FROM emp;
+--------+-------------+
| ename  | job         |
+--------+-------------+
| SMITH  | CLERK       |
| ALLEN  | SALESPERSON |
| JONES  | MANAGER     |
| MARTIN | SALESPERSON |
| BLAKE  | MANAGER     |
| SCOTT  | ANALYST     |
| KING   | PRESIDENT   |
| TURNER | SALESPERSON |
| MILLER | CLERK       |
| JAMES  | CLERK       |
| FORD   | ANALYST     |
+--------+-------------+
11 rows in set (0.00 sec)

mysql>
