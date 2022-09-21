//Query con JOIN

1)
SELECT `students`.`id`, `students`.`name`, `students`.`surname`, `degrees`.`name` AS "name_degree" 
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = "Corso di Laurea in Economia";


2)
SELECT `degrees`.`id` AS "degree_id", `departments`.`name`, `degrees`.`name`, `degrees`.`level`
FROM `departments` 
JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id` 
WHERE `departments`.`name` = "Dipartimento di Neuroscienze"


3)
SELECT DISTINCT `teachers`.`id`, `teachers`.`name` AS "name", `teachers`.`surname` AS "surname", `courses`.`name` AS "course" 
FROM `teachers` 
JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` 
JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id`
WHERE `teachers`.`name` = "Fulvio"
AND `teachers`.`surname` = "Amato"
AND `teachers`.`id` = 44


4)
SELECT `students`.`surname` AS "surname",`students`.`name` AS "name", `degrees`.`name` AS "degree", `departments`.`name` AS "department"
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `surname` ASC;


5)
SELECT `degrees`.`name` AS "degree", `courses`.`name` AS "course", `teachers`.`surname` AS "teacher_surname",  `teachers`.`name` AS "teacher_name" 
FROM `teachers`
JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id` 
JOIN `degrees` ON `degrees`.`id` = `courses`.`degree_id`
ORDER BY `teacher_surname` ASC;


6)
SELECT DISTINCT `teachers`.`name`, `teachers`.`surname`
FROM `teachers` 
JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` 
JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id` 
JOIN `degrees` ON `degrees`.`id` = `courses`.`degree_id` 
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name` = "Dipartimento di Matematica"
ORDER BY `teachers`.`surname` ASC;


7-bonus)
SELECT  `students`.`name`, `students`.`surname`, `students`.`registration_number`,
COUNT(`exam_student`.`vote`) AS "tentativi",
MAX(`exam_student`.`vote`) AS "voto_massimo"
FROM `students`
JOIN `exam_student`ON `students`.`id` = `exam_student`.`student_id`
JOIN `exams` ON `exams`.`id` = `exam_student`.`exam_id`
JOIN `courses` ON `courses`.`id` = `exams`.`course_id`
GROUP BY `students`.`id`, `courses`.`id`
HAVING `voto_massimo` >= 18
ORDER BY `voto_massimo` ASC;