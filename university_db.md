# University DB
Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi `Dipartimenti` (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più `Corsi di Laurea` (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi `Corsi`(es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi `Insegnanti`;
ogni Corso prevede più `appelli d'Esame`;
ogni `Studente` è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.
Utilizzare https://www.drawio.com/ per la creazione dello schema.
Esportare quindi il diagramma in pnge caricarlo nella repo come visto in classe

## Entities
-department
-degree_program
-course
-professor
-exam session
-student

## Tables 
-departments
-degree_programs
-courses
-professors
-exam sessions
-students


### departments
-id | BIGINT AUTO_INCREMENTAL PRIMARY_KEY UNIQUE NOTNULL
-name | VARCHAR (70)
-head_of_department | VARCHAR (50)
-website | VARCHAR (50)
-phone | VARCHAR (15)

### degree_programs
-id | BIGINT AUTO_INCREMENTAL PRIMARY_KEY UNIQUE NOTNULL
-department_id | FOREIGN_KEY
-name | VARCHAR (100)
-website | VARCHAR (50)
-email | VARCHAR (50)
-address | VARCHAR (50)

### courses
-id | BIGINT AUTO_INCREMENTAL PRIMARY_KEY UNIQUE NOTNULL
-degree_programs_id | FOREIGN_KEY
-name | VARCHAR (50)
-description | TEXT (500)
-year | YEAR (YYYY)
-credits training | TINYINT
-website |  VARCHAR (50)

### pivot: course_teacher
-course_id
-teacher_id
pk (course_id + teacher_id)

### professors
-id | BIGINT AUTO_INCREMENTAL PRIMARY_KEY UNIQUE NOTNULL
-name | VARCHAR (50)
-lastname | VARCHAR(50)
-phone | VARCHAR (15)
-email | VARCHAR (50)
-office_address | VARCHAR (50)
-office_phone | VARCHAR (15) 

### exam_session
-id | BIGINT AUTO_INCREMENTAL PRIMARY_KEY UNIQUE NOTNULL
-course_id | FOREIGN_KEY
-date | DATETIME (YYYY-MM-GG HH:II:SS)
-address | VARCHAR (50)

### pivot: exam_session_student
-student_id
-exam_session_id
-score | TINYINT
pk (exam_sessions_id + students_id)

### students
-id | BIGINT AUTO_INCREMENTAL PRIMARY_KEY UNIQUE NOTNULL
-degree_id FOREIGN_KEY
-name | VARCHAR (50)
-lastname | VARCHAR(50)
-enrollment _data| DATE (YYYY-MM-GG)


