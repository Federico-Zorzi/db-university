1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```
SELECT
	`students`.*,
    `degrees`.`name` AS `degrees_name`
FROM `students`
INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = "Corso di Laurea in Economia";
```

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
   Neuroscienze

```
SELECT
	`degrees`.*,
    `departments`.`name` AS `departments_name`,
    `departments`.`address` AS `departments_address`,
    `departments`.`website` AS `departments_website`,
    `departments`.`email` AS `departments_email`
FROM `degrees`

INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level` = "magistrale" AND `departments`.`name` = "Dipartimento di Neuroscienze" ;
```

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```
SELECT
`teachers`.*,
`courses`.`name` AS `courses_name`,
`courses`.`description` AS `courses_description`,
`courses`.`period` AS `courses_period`,
`courses`.`year` AS `courses_year`,
`courses`.`cfu` AS `courses_cfu`
FROM `teachers`

INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`

INNER JOIN `courses`
ON `course_teacher`.`course_id` = `courses`.`id`
WHERE `teachers`.`id` = 44;
```

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```
SELECT
	`students`.*,
	`degrees`.`id` AS `degrees_id`,
    `degrees`.`name` AS `degrees_name`,
    `degrees`.`level` AS `degrees_level`,
	`departments`.`id` AS `departments_id`,
    `departments`.`name` AS `departments_name`,
    `departments`.`website` AS `departments_website`,
    `departments`.`head_of_department` AS `departments_head_of_department`
FROM `students`

INNER JOIN `degrees`
ON `students`.`degree_id`=`degrees`.`id`

INNER JOIN `departments`
ON `degrees`.`department_id`=`departments`.`id`
ORDER BY `students`.`name`, `students`.`surname`;
```

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```
SELECT
	`degrees`.*,
    `courses`.`name` AS `courses_name`,
    `courses`.`description` AS `courses_description`,
    `courses`.`period` AS `courses_period`,
    `courses`.`year` AS `courses_year`,
    `courses`.`cfu` AS `courses_cfu`,
    `course_teacher`.*,
    `teachers`.`name` AS `teachers_name`,
	`teachers`.`surname` AS `teachers_surname`,
    `teachers`.`email` AS `teachers_email`
FROM `degrees`

INNER JOIN `courses`
ON `degrees`.`id` = `courses`.`degree_id`

INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`

INNER JOIN `teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`;
```

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
   Matematica (54)

```
SELECT *
FROM `teachers`

INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`

INNER JOIN `courses`
ON `course_teacher`.`course_id` = `courses`.`id`

INNER JOIN `degrees`
ON `courses`.`degree_id` = `degrees`.`id`

INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`

WHERE `departments`.`name` = "Dipartimento di Matematica";
```

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
   per ogni esame, stampando anche il voto massimo. Successivamente,
   filtrare i tentativi con voto minimo 18.```

```

```
