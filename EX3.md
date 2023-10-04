# EX-3-SubQueries-Views-and-Joins
## Aim:
To view implement SubQueries, Views and Joins.

### Create employee Table
```
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
### Insert the values
```
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```
### Create department table
```
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
#### Insert the values in the department table
```
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```
### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.
### QUERY:
```
SELECT ename FROM EMP WHERE sal > (SELECT sal FROM EMP WHERE empno = 7566);
```
### OUTPUT:
![image](https://github.com/SandhiyaR1/EX-3-SubQueries-Views-and-Joins/assets/113497571/03d45076-1b8a-4596-9b76-6a4ca9effb0e)


### Q2) List the ename,job,sal of the employee who get minimum salary in the company.
### QUERY:
```
SELECT ename,job,sal FROM EMP WHERE sal = (SELECT MIN(sal) FROM EMP);
```
### OUTPUT:
![image](https://github.com/SandhiyaR1/EX-3-SubQueries-Views-and-Joins/assets/113497571/b72d327a-de6f-49c8-9ba3-eb4c30c6a087)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.
### QUERY:
```
SELECT ename,job FROM EMP WHERE deptno = 10 AND job IN (SELECT job FROM EMP WHERE job = 'sales');
```
### OUTPUT:
![image](https://github.com/SandhiyaR1/EX-3-SubQueries-Views-and-Joins/assets/113497571/b1df97f3-d755-4d35-82e8-77dfcfb9f5b3)


#### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.
### QUERY:
```
create view empv5 as select EMPNO,ENAME,JOB from EMP where DEPTNO=10;
SELECT * FROM empv5;
```
### OUTPUT:
![image](https://github.com/SandhiyaR1/EX-3-SubQueries-Views-and-Joins/assets/113497571/3a9c971f-6379-44af-8481-e0d192636421)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.
### QUERY:
```
create view empv30 AS select EMPNO,ENAME,SAL from EMP where DEPTNO=30;
SELECT * FROM empv30;
```
### OUTPUT:
![image](https://github.com/SandhiyaR1/EX-3-SubQueries-Views-and-Joins/assets/113497571/628fb414-33ef-498b-ba4d-fddef73f0b3a)


### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table
### QUERY:
```
UPDATE EMP SET sal = sal * 1.1 WHERE job = 'CLERK';
create view empv5 as select EMPNO,ENAME,SALARY,JOB from EMP;
```
### OUTPUT:
![271561329-be0ccabb-4c4c-43bb-910e-b5a1c08ef992](https://github.com/SandhiyaR1/EX-3-SubQueries-Views-and-Joins/assets/113497571/3116aa85-de7f-469b-9c50-b794701b969f)



### Create a Customer1 Table
```
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
### Inserting Values to the Table
```
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
``
### Create a Salesperson1 table
``sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
### Inserting Values to the Table
```
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.
### QUERY:
```
select s.name,c.cust_name,s.city from salesman1 s ,customer1 c where s.city=c.city;
```
### OUTPUT:
![271562728-cb190aae-e864-4c98-bda8-e91534a5bd6b](https://github.com/SandhiyaR1/EX-3-SubQueries-Views-and-Joins/assets/113497571/526d1b4b-46c3-4fdd-adaf-e9dfce027911)



### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.
### QUERY:
```
select s.name,c.cust_name,c.city,s.commission from salesman1 s inner join customer1 c on s.city=c.city where s.commission>0.13;
```
### OUTPUT:

![271562993-6571157c-2296-4864-a83d-6e92584f6a88](https://github.com/SandhiyaR1/EX-3-SubQueries-Views-and-Joins/assets/113497571/c8887146-c48c-4944-a04a-b48883c961fc)

### Q9) Perform Natural join on both tables
### QUERY:
```
 select * from salesman1 s natural join customer1 c;
```
### OUTPUT:
![271564646-1a78b401-85cf-4d47-8ba7-e8563f6d8526](https://github.com/SandhiyaR1/EX-3-SubQueries-Views-and-Joins/assets/113497571/01a6b6ba-295f-4204-be0c-0060e09e5b7f)
606

### Q10) Perform Left and right join on both tables
### QUERY:
```
select s.name,c.cust_name,c.city,s.commission from salesman1 s left join customer1 c on s.salesman_id=c.salesman_id;

select s.name,c.cust_name,c.city,s.commission from salesman1 s right join customer1 c on s.salesman_id=c.salesman_id;
```
### OUTPUT:

### Left Join:

![271565038-55269f4a-2362-4e22-a32a-f12e403328bb](https://github.com/SandhiyaR1/EX-3-SubQueries-Views-and-Joins/assets/113497571/6db7cbb4-1ec2-422e-b55b-d5754eff7a42)


### Right Join:

![271565231-4c457c84-8c15-4121-ad37-e2c1292dcab3](https://github.com/SandhiyaR1/EX-3-SubQueries-Views-and-Joins/assets/113497571/121916de-d226-48cd-924e-764fed1623c5)


## Result:
 a database is created and implementation of views,subqueries and joins is executed successfully.
