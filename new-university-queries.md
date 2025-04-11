/*Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia*/
SELECT students.id, students.name, students.surname, degrees.name
FROM students
JOIN degrees ON students.degree_id = degrees.id
WHERE degrees.name = 'Corso di Laurea in Economia';

/*Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze*/
SELECT degrees.id, degrees.name AS degree_name, departments.name AS department_name
FROM departments
JOIN degrees ON departments.id = degrees.department_id
WHERE departments.name = 'Dipartimento di Neuroscienze'
AND degrees.name LIKE 'Corso di Laurea Magistrale %';

/*Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)*/
SELECT courses.id, teachers.name, teachers.surname, courses.name
FROM teachers 
JOIN course_teacher ON teachers.id = course_teacher.teacher_id
JOIN courses ON courses.id = course_teacher.course_id
WHERE teachers.id = 44;

/*Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome*/
SELECT students.surname, students.name, students.id, degrees.name AS 'degree_name', departments.name AS 'department_name'
FROM students
JOIN degrees ON students.degree_id = degrees.id
JOIN departments ON departments.id = degrees.department_id
ORDER BY students.surname ASC, students.name ASC;

/*Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti*/
SELECT degrees.id, degrees.name AS degree_name, courses.name AS course_name, teachers.name AS teacher_name, teachers.surname AS teacher_surname
FROM degrees
JOIN courses ON degrees.id = courses.degree_id
JOIN course_teacher ON courses.id = course_teacher.course_id
JOIN teachers ON teachers.id = course_teacher.teacher_id
ORDER BY degrees.id ASC;

/*Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)*/
SELECT DISTINCT teachers.id, teachers.name AS teacher_name, teachers.surname AS teacher_surname, departments.name AS department_name
FROM departments
JOIN degrees ON departments.id = degrees.department_id
JOIN courses ON degrees.id = courses.degree_id
JOIN course_teacher ON courses.id = course_teacher.course_id
JOIN teachers ON teachers.id = course_teacher.teacher_id
WHERE departments.name = 'Dipartimento di Matematica'
ORDER BY teachers.id;

/*Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. 
Successivamente, filtrare i tentativi con voto minimo 18.*/
SELECT students.id, students.name, students.surname, exams.id AS exam_id, MAX(exam_student.vote) AS highest_vote, COUNT(*) AS exam_attempts
FROM students
JOIN exam_student ON students.id = exam_student.student_id
JOIN exams ON exams.id = exam_student.exam_id
WHERE exam_student.vote >= 18
GROUP BY students.id, exams.id
ORDER BY students.id, exams.id;

/*Contare quanti iscritti ci sono stati ogni anno*/
SELECT YEAR(enrolment_date) AS enrolment_year, COUNT(*) AS students_count
FROM students
GROUP BY enrolment_year
ORDER BY enrolment_year ASC;

/*Contare gli insegnanti che hanno l'ufficio nello stesso edificio*/
SELECT office_address, COUNT(*) AS teachers_in_same_address_count
FROM teachers
GROUP BY office_address
ORDER BY teachers_in_same_address_count DESC;

/*Calcolare la media dei voti di ogni appello d'esame*/
SELECT exam_id, AVG(vote) AS average_vote
FROM exam_student
GROUP BY exam_id;

/*Contare quanti corsi di laurea ci sono per ogni dipartimento*/
SELECT departments.name AS department_name, COUNT(*) AS degrees_count
FROM degrees
JOIN departments ON departments.id = degrees.department_id
GROUP BY department_id;

/*Selezionare tutti gli insegnanti*/
SELECT id, name, surname
FROM teachers;

/*Selezionare tutti i referenti per ogni dipartimento*/
SELECT name, head_of_department
FROM departments;

/*Selezionare tutti gli studenti il cui nome inizia per "E" (373)*/
SELECT id, name, surname
FROM students
WHERE name LIKE 'E%';

/*Selezionare tutti gli studenti che si sono iscritti nel 2021 (734)*/
SELECT id, name, surname, enrolment_date
FROM students
WHERE enrolment_date LIKE '2021-%';

/*Selezionare tutti i corsi che non hanno un sito web (676)*/
SELECT id, name
FROM courses
WHERE website IS NULL;

/*Selezionare tutti gli insegnanti che hanno un numero di telefono (50)*/
SELECT *
FROM teachers
WHERE phone IS NOT NULL;

/*Selezionare tutti gli appelli d'esame dei mesi di giugno e luglio 2020 (2634)*/
SELECT *
FROM exams
WHERE date LIKE '2020-06-%' OR date LIKE '2020-07-%';

/*Qual è il numero totale degli studenti iscritti? (5000)*/
SELECT COUNT(id) AS students_total
FROM students;