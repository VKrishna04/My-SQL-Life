# My SQL Life
Select distinct T.name 
from instructors S, instructors T 
where T.salary > S.salary and 
S.dept_name ='Biology’;

SELECT CONCAT('--', dept_name, '--', building, '--') 
AS concatenated_string FROM department;









