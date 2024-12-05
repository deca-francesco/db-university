# TODO:

## Group by:
1.  Contare quanti iscritti ci sono stati ogni anno
2.  Contare gli insegnanti che hanno l'ufficio nello stesso edificio
3.  Calcolare la media dei voti di ogni appello d'esame
4.  Contare quanti corsi di laurea ci sono per ogni dipartimento

## Joins:
5.  Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
6.  Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
7.  Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
8.  Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
9.  Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
10. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

## BONUS:
11. Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.




1.  SELECT COUNT(id) , YEAR(enrolment_date)
    FROM students
    GROUP BY YEAR(enrolment_date)

2.  SELECT COUNT(id) , office_address
    FROM teachers
    GROUP BY office_address

3.  SELECT AVG(vote) as media_voto , exam_id
    FROM exam_student
    GROUP BY exam_id

4.  SELECT COUNT(id) , department_id
    FROM degrees
    GROUP BY department_id

5.  SELECT *
    FROM students
    JOIN degrees
    ON students.degree_id = degrees.id
    WHERE degrees.name = "Corso di Laurea in Economia"

6.  SELECT *
    FROM degrees
    JOIN departments
    ON degrees.department_id = departments.id
    WHERE departments.name = "Dipartimento di Neuroscienze"
    AND degrees.level = "magistrale"

7.  SELECT *
    FROM course_teacher
    JOIN courses
    ON course_teacher.course_id = courses.id
    WHERE teacher_id = 44

8.  SELECT *
    FROM students
    JOIN degrees
    ON students.degree_id = degrees.id
    JOIN departments
    ON degrees.department_id = departments.id
    ORDER BY students.surname , students.name

9.  