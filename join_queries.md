
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze:

SELECT `degrees`.*, `departments`.`name` AS `nome_dipartimento` 
FROM `degrees` 
JOIN `departments` 
ON `departments`.`id` = `degrees`.`department_id` 
WHERE `departments`.`name` LIKE 'Dipartimento di Neuroscienze' AND `degrees`.`level` = 'magistrale';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `courses`.`id`, `courses`.`degree_id` AS `id_corso_laurea`
FROM `courses`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`
WHERE `teachers`.`name` = 'Fulvio' AND `teachers`.`surname` = 'Amato';

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)

SELECT DISTINCT `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname` 
FROM `teachers` 
JOIN `course_teacher` ON `course_teacher`.`teacher_id` = `teachers`.`id` JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id` 
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id` 
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id` 
WHERE `departments`.`name` = 'Dipartimento di Matematica' 
ORDER BY `teacher_surname` ASC;

