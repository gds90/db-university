1. Contare quanti iscritti ci sono stati ogni anno:

SELECT COUNT(id) AS `totale_iscritti`, YEAR(`enrolment_date`) AS `anno` 
FROM `students` 
GROUP BY YEAR(`enrolment_date`);

3. Calcolare la media dei voti di ogni appello d'esame:

SELECT ROUND(AVG(`vote`), 2) AS `media_voto`, `exam_id` 
FROM `exam_student` 
GROUP BY `exam_id`;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento:

SELECT `department_id`, COUNT(id) as `totale_corsi_laurea` 
FROM `degrees` 
GROUP BY `department_id`;
