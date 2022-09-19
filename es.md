//Query con SELECT

1) 
SELECT * 
FROM `students`
WHERE YEAR(`date_of_birth`) = 1990;

2)
SELECT * 
FROM `courses` 
WHERE `cfu` > 10;

3)
SELECT * 
FROM `students` 
WHERE `date_of_birth` > "1992-09-18";

4)
SELECT * 
FROM `courses` 
WHERE `period` 
NOT LIKE "_I%" 
AND `year` = 1;

5)
SELECT * 
FROM `exams` 
WHERE HOUR(`hour`) >= 14 
AND `date` = "2020-06-20";

6)
SELECT * 
FROM `degrees`
WHERE `level` LIKE ("M%");

7)
SELECT COUNT(id) 
AS 'number_departments' 
FROM `departments`

8)
SELECT * 
FROM `teachers` 
WHERE `phone` IS NULL;