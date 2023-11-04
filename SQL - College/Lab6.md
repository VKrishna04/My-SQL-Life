Lab 6
CREATE TABLE Cust (
    custid VARCHAR(255) primary key,
    Lname VARCHAR(255),
    Fname VARCHAR(255),
    Area VARCHAR(255),
    PhoneNo INT
);

INSERT INTO Cust (custid, Lname, Fname, Area, PhoneNo) VALUES
('A01', 'Bayross', 'Ivan', 'sa', 6125467),
('A02', 'Saitwal', 'Vandana', 'mu', 5560379),
('A03', 'Jaguste', 'Pramada', 'da', 4563891),
('A04', 'Navindgi', 'Basu', 'ba', 6125401),
('A05', 'Sreedhar', 'Ravi', 'va', NULL),
('A06', NULL, 'Rukmini', 'gh', 5125274);

16.
SELECT custid, Fname
FROM Cust
WHERE Lname IS NULL;

SELECT custid, Fname
FROM Cust
WHERE COALESCE(Lname, '') = '';

17.
SELECT custid, Lname, Area
FROM Cust
WHERE PhoneNo IS NULL;

SELECT custid, Lname, Area, 
ISNULL (PhoneNo, '') AS PhoneNo
FROM Cust;

SELECT custid, Lname, Area
FROM Cust
WHERE PhoneNo IS NULL;


--------------------------

CREATE TABLE Movie (mvno varchar(10), title varchar(30), type varchar(30), star varchar(30), price decimal(10, 2));

INSERT INTO Movie values 
('1', 'Bloody Vengeance', 'action' , 'Jackie Chan', 100.00),
('2', 'The Firm', 'thriller' , 'Tom cruise', 200.00),
('3', 'Pretty Woman', 'romance' , 'Richard Gere', 150.00),
('4', 'Home Alone', 'Comedy' , 'Macaulay Culkin', 150.55),
('5', 'The Fugitive', 'Thriller' , 'Harrison Ford', 200.00),
('6', 'Coma', 'Suspense' , 'Michael Douglas', 100.00),
('7', 'Dracula', 'Horror' , 'Gary Oldman',150.25),
('8', 'Quich change', 'Comedy' , 'Bill Murray', 100.00),
('9', 'Gone with the wind', 'Drama' , 'Clarke Gale', 200.00),
('10','Carry on Doctor', 'Comedy' , 'Lesie Philips', 100.00);

select * from Movie;

SELECT mvno, title, type FROM Movie WHERE star LIKE 'M%';

SELECT mvno, title, type FROM Movie WHERE LEFT(star, 1) = 'M';


18.
select (select price from movie where title='Home Alone')/
((select price from movie where title='Home Alone')-100) as price;



--------------------------

CREATE TABLE Invo (
    invno INT,
    mvno INT,
    custid VARCHAR(10),
    issueDate VARCHAR(20),
    retDate VARCHAR(20)
);

INSERT INTO Invo (invno, mvno, custid, issueDate, retDate) 
VALUES (101, 4, 'A01', '23-Jul-93', '25-Jul-93'),
(102, 3, 'A02', '12-Aug-93', '15-Aug-93'),
(103, 6, 'A02', '15-Aug-93', '18-Aug-93'),
(104, 7, 'A03', '10-Sep-93', '13-Sep-93'),
(105, 2, 'A04', '05-Aug-93', '08-Aug-93'),
(106, 9, 'A06', '18-Sep-93', '20-Sep-93'),
(107, 9, 'A05', '07-Jul-93', '10-Jul-93'),
(108, 5, 'A01', '11-Aug-93', '14-Aug-93'),
(109, 8, 'A03', '06-Jul-93', '09-Jul-93'),
(110, 6, 'A06', '03-Sep-93', '06-Sep-93');

14.
SELECT mvno, invno
FROM Invo
WHERE invno < 105;

SELECT mvno, invno
FROM Invo
WHERE invno < (SELECT 105);