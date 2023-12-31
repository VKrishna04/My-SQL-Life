# My SQL Life

\c --mysql as root@localhost

show databases;

\use <!-- database name -->

show tables;

-----------------------------------

+--------------------+
| Database           |
+--------------------+
| 19cse202_lab1      |
| 19cse202_lab2      |
| 19cse202_lab4      |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+

+-------------------------+
| Tables_in_19cse202_lab1 |
+-------------------------+
| department              |
+-------------------------+

+------------+----------+--------+------------+
| Name       | Building | Budget | Classrooms |
+------------+----------+--------+------------+
| Biology    | Watson   | 200.00 |          7 |
| CSE        | Taylor   | 100.00 |          6 |
| Electrical | Taylor   | 300.00 |          3 |
| Finance    | Painter  | 500.00 |          5 |
| History    | Painter  | 600.00 |          3 |
| Music      | Packard  | 400.00 |          4 |
| Physics    | Watson   | 700.00 |          2 |
+------------+----------+--------+------------+
```sql
CREATE TABLE departments (
    Name VARCHAR(255),
    Building VARCHAR(255),
    Budget DECIMAL(10, 2),
    Classrooms INT
);

INSERT INTO departments (Name, Building, Budget, Classrooms)
VALUES
    ('Biology', 'Watson', 200.00, 7),
    ('CSE', 'Taylor', 100.00, 6),
    ('Electrical', 'Taylor', 300.00, 3),
    ('Finance', 'Painter', 500.00, 5),
    ('History', 'Painter', 600.00, 3),
    ('Music', 'Packard', 400.00, 4),
    ('Physics', 'Watson', 700.00, 2);

```
-------------------------------------
+-------------------------+
| Tables_in_19cse202_lab2 |
+-------------------------+
| courses                 |
| department              |
| instructors             |
| section                 |
| table1                  |
| table2                  |
| teaches                 |
+-------------------------+

+-----------+---------------------------+------------+---------+
| course_Id | title                     | dept_name  | credits |
+-----------+---------------------------+------------+---------+
| BIO-101   | Intro to Biology          | Biology    |       4 |
| BIO-301   | Genetics                  | Biology    |       4 |
| BIO-399   | Computational Biology     | Biology    |       3 |
| CS-101    | Intro to Computer science | CSE        |       4 |
| CS-190    | Game design               | CSE        |       4 |
| CS-315    | Robotics                  | CSE        |       3 |
| CS-319    | Image Processing          | CSE        |       3 |
| CS-347    | Database system concepts  | CSE        |       3 |
| EE-181    | Intro to Digital systems  | Electrical |       3 |
| FIN-201   | Investment Banking        | Finance    |       3 |
| HIS-351   | World History             | History    |       3 |
| MU-199    | Music video production    | Music      |       3 |
| PHY-101   | Physical Principles       | Physics    |       4 |
+-----------+---------------------------+------------+---------+

```sql
CREATE TABLE courses (

    course_Id VARCHAR(10),
    title VARCHAR(255),
    dept_name VARCHAR(255),
    credits INT
);

INSERT INTO courses (course_Id, title, dept_name, credits)
VALUES
    ('BIO-101', 'Intro to Biology', 'Biology', 4),
    ('BIO-301', 'Genetics', 'Biology', 4),
    ('BIO-399', 'Computational Biology', 'Biology', 3),
    ('CS-101', 'Intro to Computer Science', 'CSE', 4),
    ('CS-190', 'Game Design', 'CSE', 4),
    ('CS-315', 'Robotics', 'CSE', 3),
    ('CS-319', 'Image Processing', 'CSE', 3),
    ('CS-347', 'Database System Concepts', 'CSE', 3),
    ('EE-181', 'Intro to Digital Systems', 'Electrical', 3),
    ('FIN-201', 'Investment Banking', 'Finance', 3),
    ('HIS-351', 'World History', 'History', 3),
    ('MU-199', 'Music Video Production', 'Music', 3),
    ('PHY-101', 'Physical Principles', 'Physics', 4);
```

select * from departments;
+------------+----------+--------+
| dept_name  | building | budget |
+------------+----------+--------+
| Biology    | Watson   |  90000 |
| CSE        | Taylor   | 100000 |
| Electrical | Taylor   |  85000 |
| Finance    | Painter  | 120000 |
| History    | Painter  |  50000 |
| Music      | Packard  |  80000 |
| Physics    | Watson   |  70000 |
+------------+----------+--------+
```sql
CREATE TABLE departments (
    dept_name VARCHAR(255),
    building VARCHAR(255),
    budget INT
);

INSERT INTO departments (dept_name, building, budget)
VALUES
    ('Biology', 'Watson', 90000),
    ('CSE', 'Taylor', 100000),
    ('Electrical', 'Taylor', 85000),
    ('Finance', 'Painter', 120000),
    ('History', 'Painter', 50000),
    ('Music', 'Packard', 80000),
    ('Physics', 'Watson', 70000);
```
select * from instructors;
+-------+------------+------------+--------+
| ID    | name       | dept_name  | salary |
+-------+------------+------------+--------+
| 10101 | Srinivasan | CSE        |  65000 |
| 12121 | Wu         | Finance    |  90000 |
| 15151 | Mozart     | Music      |  40000 |
| 22222 | Einstein   | Physics    |  95000 |
| 32343 | El Said    | History    |  60000 |
| 33456 | Gold       | Physics    |  87000 |
| 45565 | Katz       | CSE        |  75000 |
| 58583 | Califieri  | History    |  62000 |
| 76543 | Singh      | Finance    |  80000 |
| 76766 | Crick      | Biology    |  72000 |
| 83821 | Brandi     | CSE        |  92000 |
| 98345 | Kim        | Electrical |  80000 |
+-------+------------+------------+--------+
```sql
CREATE TABLE instructors (
    ID INT,
    name VARCHAR(255),
    dept_name VARCHAR(255),
    salary INT
);
INSERT INTO instructors (ID, name, dept_name, salary)
VALUES
    (10101, 'Srinivasan', 'CSE', 65000),
    (12121, 'Wu', 'Finance', 90000),
    (15151, 'Mozart', 'Music', 40000),
    (22222, 'Einstein', 'Physics', 95000),
    (32343, 'El Said', 'History', 60000),
    (33456, 'Gold', 'Physics', 87000),
    (45565, 'Katz', 'CSE', 75000),
    (58583, 'Califieri', 'History', 62000),
    (76543, 'Singh', 'Finance', 80000),
    (76766, 'Crick', 'Biology', 72000),
    (83821, 'Brandi', 'CSE', 92000),
    (98345, 'Kim', 'Electrical', 80000);
```
select * from section;
+-----------+--------+----------+------+----------+-------------+--------------+
| course_id | sec_id | semester | year | building | room_number | time_slot_id |
+-----------+--------+----------+------+----------+-------------+--------------+
| BIO-101   | 1      | Summer   | 2009 | Painter  | 514         | B            |
| BIO-301   | 1      | Summer   | 2010 | Painter  | 514         | A            |
| CS-101    | 1      | Fall     | 2009 | Packard  | 101         | H            |
| CS-101    | 1      | Spring   | 2010 | Packard  | 101         | F            |
| CS-190    | 1      | Spring   | 2009 | Taylor   | 3128        | E            |
| CS-190    | 2      | Spring   | 2009 | Taylor   | 3128        | A            |
| CS-315    | 1      | Spring   | 2010 | Watson   | 120         | D            |
| CS-319    | 1      | Spring   | 2010 | Watson   | 100         | B            |
| CS-319    | 2      | Spring   | 2010 | Taylor   | 3128        | C            |
| CS-347    | 1      | Fall     | 2009 | Taylor   | 3128        | A            |
| EE-181    | 1      | Spring   | 2009 | Taylor   | 3128        | C            |
| FIN-201   | 1      | Spring   | 2010 | Packard  | 101         | B            |
| HIS-351   | 1      | Spring   | 2010 | Painter  | 514         | C            |
| MU-199    | 1      | Spring   | 2010 | Packard  | 101         | D            |
| PHY-101   | 1      | Fall     | 2009 | Watson   | 100         | A            |
+-----------+--------+----------+------+----------+-------------+--------------+
```sql
CREATE TABLE section (
    course_id VARCHAR(10),
    sec_id INT,
    semester VARCHAR(255),
    year INT,
    building VARCHAR(255),
    room_number VARCHAR(10),
    time_slot_id VARCHAR(5)
);
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id)
VALUES
    ('BIO-101', 1, 'Summer', 2009, 'Painter', '514', 'B'),
    ('BIO-301', 1, 'Summer', 2010, 'Painter', '514', 'A'),
    ('CS-101', 1, 'Fall', 2009, 'Packard', '101', 'H'),
    ('CS-101', 1, 'Spring', 2010, 'Packard', '101', 'F'),
    ('CS-190', 1, 'Spring', 2009, 'Taylor', '3128', 'E'),
    ('CS-190', 2, 'Spring', 2009, 'Taylor', '3128', 'A'),
    ('CS-315', 1, 'Spring', 2010, 'Watson', '120', 'D'),
    ('CS-319', 1, 'Spring', 2010, 'Watson', '100', 'B'),
    ('CS-319', 2, 'Spring', 2010, 'Taylor', '3128', 'C'),
    ('CS-347', 1, 'Fall', 2009, 'Taylor', '3128', 'A'),
    ('EE-181', 1, 'Spring', 2009, 'Taylor', '3128', 'C'),
    ('FIN-201', 1, 'Spring', 2010, 'Packard', '101', 'B'),
    ('HIS-351', 1, 'Spring', 2010, 'Painter', '514', 'C'),
    ('MU-199', 1, 'Spring', 2010, 'Packard', '101', 'D'),
    ('PHY-101', 1, 'Fall', 2009, 'Watson', '100', 'A');
```
select * from table1;
+----+------+
| ID | Name |
+----+------+
| a  | abc  |
| b  | xyz  |
| c  | def  |
| e  | ghi  |
+----+------+
```sql
CREATE TABLE table1 (
    ID CHAR(1),
    Name VARCHAR(255)
);
INSERT INTO table1 (ID, Name)
VALUES
    ('a', 'abc'),
    ('b', 'xyz'),
    ('c', 'def'),
    ('e', 'ghi');
```

select * from table2;
+----+-----------+
| ID | Course_Id |
+----+-----------+
| a  | c1        |
| b  | c2        |
| c  | c3        |
+----+-----------+
```sql

CREATE TABLE table2 (
    ID CHAR(1),
    Course_Id CHAR(2)
);
INSERT INTO table2 (ID, Course_Id)
VALUES
    ('a', 'c1'),
    ('b', 'c2'),
    ('c', 'c3');
```

select * from teaches;
+-------+-----------+--------+----------+------+
| ID    | course_Id | Sec_Id | semester | year |
+-------+-----------+--------+----------+------+
| 10101 | CS-101    |      1 | Fall     | 2009 |
| 10101 | CS-315    |      1 | Spring   | 2010 |
| 10101 | CS-347    |      1 | Fall     | 2009 |
| 12121 | FIN-201   |      1 | Spring   | 2010 |
| 15151 | MU-199    |      1 | Spring   | 2010 |
| 22222 | PHY-101   |      1 | Fall     | 2009 |
| 32343 | HIS-351   |      1 | Spring   | 2010 |
| 45565 | CS-101    |      1 | Spring   | 2010 |
| 45565 | CS-319    |      1 | Spring   | 2010 |
| 76766 | BIO-101   |      1 | Summer   | 2009 |
| 76766 | BIO-301   |      1 | Summer   | 2010 |
| 83821 | CS-190    |      1 | Spring   | 2009 |
| 83821 | CS-190    |      2 | Spring   | 2009 |
| 83821 | CS-319    |      2 | Spring   | 2010 |
| 98345 | EE-181    |      1 | Spring   | 2009 |
+-------+-----------+--------+----------+------+

```sql

CREATE TABLE teaches (
    ID INT,
    course_Id VARCHAR(10),
    Sec_Id INT,
    semester VARCHAR(255),
    year INT
);

INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year)
VALUES
    (10101, 'CS-101', 1, 'Fall', 2009),
    (10101, 'CS-315', 1, 'Spring', 2010),
    (10101, 'CS-347', 1, 'Fall', 2009),
    (12121, 'FIN-201', 1, 'Spring', 2010),
    (15151, 'MU-199', 1, 'Spring', 2010),
    (22222, 'PHY-101', 1, 'Fall', 2009),
    (32343, 'HIS-351', 1, 'Spring', 2010),
    (45565, 'CS-101', 1, 'Spring', 2010),
    (45565, 'CS-319', 1, 'Spring', 2010),
    (76766, 'BIO-101', 1, 'Summer', 2009),
    (76766, 'BIO-301', 1, 'Summer', 2010),
    (83821, 'CS-190', 1, 'Spring', 2009),
    (83821, 'CS-190', 2, 'Spring', 2009),
    (83821, 'CS-319', 2, 'Spring', 2010),
    (98345, 'EE-181', 1, 'Spring', 2009);
```

---------------------------------

show tables;
+-------------------------+
| Tables_in_19cse202_lab4 |
+-------------------------+
| aaa                     |
| bbb                     |
+-------------------------+

select * from aaa;
+-----+
| AAA |
+-----+
| A   |
| B   |
| C   |
| D   |
| E   |
| E   |
+-----+

```sql
CREATE TABLE aaa (
    AAA CHAR(1)
);
INSERT INTO aaa (AAA)
VALUES
    ('A'),
    ('B'),
    ('C'),
    ('D'),
    ('E'),
    ('E');

```

select * from bbb;
+-----+
| BBB |
+-----+
| A   |
| B   |
| F   |
| A   |
+-----+

```sql
CREATE TABLE bbb (
    BBB CHAR(1)
);

INSERT INTO bbb (BBB)
VALUES
    ('A'),
    ('B'),
    ('F'),
    ('A');
```

--------------------------
# OracleSQL

-- Creating sample tables
CREATE TABLE departments (
    Name VARCHAR2(255),
    Building VARCHAR2(255),
    Budget NUMBER(10, 2),
    Classrooms NUMBER
);

INSERT INTO departments (Name, Building, Budget, Classrooms) VALUES ('Biology', 'Watson', 200.00, 7);
INSERT INTO departments (Name, Building, Budget, Classrooms) VALUES ('CSE', 'Taylor', 100.00, 6);
INSERT INTO departments (Name, Building, Budget, Classrooms) VALUES ('Electrical', 'Taylor', 300.00, 3);
INSERT INTO departments (Name, Building, Budget, Classrooms) VALUES ('Finance', 'Painter', 500.00, 5);
INSERT INTO departments (Name, Building, Budget, Classrooms) VALUES ('History', 'Painter', 600.00, 3);
INSERT INTO departments (Name, Building, Budget, Classrooms) VALUES ('Music', 'Packard', 400.00, 4);
INSERT INTO departments (Name, Building, Budget, Classrooms) VALUES ('Physics', 'Watson', 700.00, 2);

CREATE TABLE courses (
    course_Id VARCHAR2(10),
    title VARCHAR2(255),
    dept_name VARCHAR2(255),
    credits NUMBER
);

INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('BIO-101', 'Intro to Biology', 'Biology', 4);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('BIO-301', 'Genetics', 'Biology', 4);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('BIO-399', 'Computational Biology', 'Biology', 3);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('CS-101', 'Intro to Computer Science', 'CSE', 4);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('CS-190', 'Game Design', 'CSE', 4);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('CS-315', 'Robotics', 'CSE', 3);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('CS-319', 'Image Processing', 'CSE', 3);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('CS-347', 'Database System Concepts', 'CSE', 3);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('EE-181', 'Intro to Digital Systems', 'Electrical', 3);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('FIN-201', 'Investment Banking', 'Finance', 3);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('HIS-351', 'World History', 'History', 3);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('MU-199', 'Music Video Production', 'Music', 3);
INSERT INTO courses (course_Id, title, dept_name, credits) VALUES ('PHY-101', 'Physical Principles', 'Physics', 4);
    
CREATE TABLE departments (
    dept_name VARCHAR2(255),
    building VARCHAR2(255),
    budget NUMBER
);

INSERT INTO departments (dept_name, building, budget) VALUES ('Biology', 'Watson', 90000);
INSERT INTO departments (dept_name, building, budget) VALUES ('CSE', 'Taylor', 100000);
INSERT INTO departments (dept_name, building, budget) VALUES ('Electrical', 'Taylor', 85000);
INSERT INTO departments (dept_name, building, budget) VALUES ('Finance', 'Painter', 120000);
INSERT INTO departments (dept_name, building, budget) VALUES ('History', 'Painter', 50000);
INSERT INTO departments (dept_name, building, budget) VALUES ('Music', 'Packard', 80000);
INSERT INTO departments (dept_name, building, budget) VALUES ('Physics', 'Watson', 70000);

CREATE TABLE instructors (
    ID NUMBER,
    name VARCHAR2(255),
    dept_name VARCHAR2(255),
    salary NUMBER
);

INSERT INTO instructors (ID, name, dept_name, salary) VALUES (10101, 'Srinivasan', 'CSE', 65000);
INSERT INTO instructors (ID, name, dept_name, salary) VALUES (12121, 'Wu', 'Finance', 90000);
INSERT INTO instructors (ID, name, dept_name, salary) VALUES (15151, 'Mozart', 'Music', 40000);
INSERT INTO instructors (ID, name, dept_name, salary) VALUES (22222, 'Einstein', 'Physics', 95000);
INSERT INTO instructors (ID, name, dept_name, salary) VALUES (32343, 'El Said', 'History', 60000);
INSERT INTO instructors (ID, name, dept_name, salary) VALUES (33456, 'Gold', 'Physics', 87000);
INSERT INTO instructors (ID, name, dept_name, salary) VALUES (45565, 'Katz', 'CSE', 75000);
INSERT INTO instructors (ID, name, dept_name, salary) VALUES (58583, 'Califieri', 'History', 62000);
INSERT INTO instructors (ID, name, dept_name, salary) VALUES (76543, 'Singh', 'Finance', 80000);
INSERT INTO instructors (ID, name, dept_name, salary) VALUES (76766, 'Crick', 'Biology', 72000);
INSERT INTO instructors (ID, name, dept_name, salary) VALUES (83821, 'Brandi', 'CSE', 92000);
INSERT INTO instructors (ID, name, dept_name, salary) VALUES (98345, 'Kim', 'Electrical', 80000);

CREATE TABLE section (
    course_id VARCHAR2(10),
    sec_id NUMBER,
    semester VARCHAR2(255),
    year NUMBER,
    building VARCHAR2(255),
    room_number VARCHAR2(10),
    time_slot_id VARCHAR2(5)
);

INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('BIO-101', 1, 'Summer', 2009, 'Painter', '514', 'B');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('BIO-301', 1, 'Summer', 2010, 'Painter', '514', 'A');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('CS-101', 1, 'Fall', 2009, 'Packard', '101', 'H');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('CS-101', 1, 'Spring', 2010, 'Packard', '101', 'F');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('CS-190', 1, 'Spring', 2009, 'Taylor', '3128', 'E');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('CS-190', 2, 'Spring', 2009, 'Taylor', '3128', 'A');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('CS-315', 1, 'Spring', 2010, 'Watson', '120', 'D');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('CS-319', 1, 'Spring', 2010, 'Watson', '100', 'B');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('CS-319', 2, 'Spring', 2010, 'Taylor', '3128', 'C');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('CS-347', 1, 'Fall', 2009, 'Taylor', '3128', 'A');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('EE-181', 1, 'Spring', 2009, 'Taylor', '3128', 'C');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('FIN-201', 1, 'Spring', 2010, 'Packard', '101', 'B');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('HIS-351', 1, 'Spring', 2010, 'Painter', '514', 'C');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('MU-199', 1, 'Spring', 2010, 'Packard', '101', 'D');
INSERT INTO section (course_id, sec_id, semester, year, building, room_number, time_slot_id) VALUES ('PHY-101', 1, 'Fall', 2009, 'Watson', '100', 'A');

CREATE TABLE table1 (
    ID CHAR(1),
    Name VARCHAR2(255)
);

INSERT INTO table1 (ID, Name) VALUES ('a', 'abc');
INSERT INTO table1 (ID, Name) VALUES ('b', 'xyz');
INSERT INTO table1 (ID, Name) VALUES ('c', 'def');
INSERT INTO table1 (ID, Name) VALUES ('e', 'ghi');

CREATE TABLE table2 (
    ID CHAR(1),
    Course_Id CHAR(2)
);

INSERT INTO table2 (ID, Course_Id) VALUES ('a', 'c1');
INSERT INTO table2 (ID, Course_Id) VALUES ('b', 'c2');
INSERT INTO table2 (ID, Course_Id) VALUES ('c', 'c3');

CREATE TABLE teaches (
    ID NUMBER,
    course_Id VARCHAR2(10),
    Sec_Id NUMBER,
    semester VARCHAR2(255),
    year NUMBER
);

INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (10101, 'CS-101', 1, 'Fall', 2009);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (10101, 'CS-315', 1, 'Spring', 2010);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (10101, 'CS-347', 1, 'Fall', 2009);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (12121, 'FIN-201', 1, 'Spring', 2010);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (15151, 'MU-199', 1, 'Spring', 2010);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (22222, 'PHY-101', 1, 'Fall', 2009);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (32343, 'HIS-351', 1, 'Spring', 2010);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (45565, 'CS-101', 1, 'Spring', 2010);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (45565, 'CS-319', 1, 'Spring', 2010);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (76766, 'BIO-101', 1, 'Summer', 2009);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (76766, 'BIO-301', 1, 'Summer', 2010);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (83821, 'CS-190', 1, 'Spring', 2009);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (83821, 'CS-190', 2, 'Spring', 2009);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (83821, 'CS-319', 2, 'Spring', 2010);
INSERT INTO teaches (ID, course_Id, Sec_Id, semester, year) VALUES (98345, 'EE-181', 1, 'Spring', 2009);

-- Creating sample table aaa
CREATE TABLE aaa (
    AAA CHAR(1)
);

-- Inserting values into table aaa
INSERT INTO aaa (AAA) VALUES ('A');
INSERT INTO aaa (AAA) VALUES ('B');
INSERT INTO aaa (AAA) VALUES ('C');
INSERT INTO aaa (AAA) VALUES ('D');
INSERT INTO aaa (AAA) VALUES ('E');
INSERT INTO aaa (AAA) VALUES ('E');

-- Creating sample table bbb
CREATE TABLE bbb (
    BBB CHAR(1)
);

-- Inserting values into table bbb
INSERT INTO bbb (BBB) VALUES ('A');
INSERT INTO bbb (BBB) VALUES ('B');
INSERT INTO bbb (BBB) VALUES ('F');
INSERT INTO bbb (BBB) VALUES ('A');