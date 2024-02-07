
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

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome

SELECT `students`.`id`,`students`.`name` , `students`.`surname`, `degrees`.`name` AS `corso_di_laurea`, `degrees`.`level` AS `livello_corso_laurea`,`degrees`.`address` AS `indirizzo_corso_laurea`,`degrees`.`website` AS `sito_corso_laurea`,`degrees`.`email` AS `email_corso_laurea`,`departments`.`name` AS `dipartimento` 
FROM `students` 
JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id` 
JOIN `departments`ON `departments`.`id`= `degrees`.`department_id` 
ORDER BY `students`.`surname` ASC,`students`.`name` ASC;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT `degrees`.`name` AS `nome_corso_laurea`, `degrees`.`level`, `degrees`.`address`, `degrees`.`email`, `degrees`.`website`, `courses`.`name` AS `corso`, `courses`.`description` AS `descrizione_corso`, `teachers`.`name` AS `nome_insegnante`, `teachers`.`surname` AS `cognome_insegnante`
FROM `degrees`
JOIN `courses` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`  
ORDER BY `nome_corso_laurea` ASC;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)

SELECT DISTINCT `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname` 
FROM `teachers` 
JOIN `course_teacher` ON `course_teacher`.`teacher_id` = `teachers`.`id` JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id` 
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id` 
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id` 
WHERE `departments`.`name` = 'Dipartimento di Matematica' 
ORDER BY `teacher_surname` ASC;

