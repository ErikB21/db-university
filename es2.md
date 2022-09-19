1)
SELECT COUNT(id) AS "Number_Students", YEAR(`enrolment_date`) AS "Year" FROM `students` 
GROUP BY YEAR(`enrolment_date`);

2)
SELECT COUNT(id) AS "teachers_number",`office_address` 
FROM `teachers` 
GROUP BY `office_address`;

3)
SELECT AVG(`vote`) AS "average" 
FROM `exam_student` 
WHERE `vote`;

4)
SELECT COUNT(*) AS "Number_courses", `department_id` 
FROM `degrees` 
GROUP BY `department_id`;