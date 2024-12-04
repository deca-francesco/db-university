# Consegna
Modellare la struttura di un database per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi Insegnanti;
- ogni Corso prevede più appelli d'Esame;
- ogni Studente è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.

Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni.

Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

Utilizzare https://www.drawio.com/ per la creazione dello schema come visto in classe ed esportare quindi il diagramma in png caricandolo nella repo come fatto nel live coding questa mattina



## tables
- dipartimenti
- corsi
- materie
- insegnanti
- appelli
- studenti
- voti

## dipartimenti (1 => many corsi)
- id | BIGINT AI PK
- nome | VARCHAR(150) NOTNULL

## corsi (1 => many materie)

- id | BIGINT AI PK
- id_dipartimento | BIGINT AI FK
- nome | VARCHAR(50) NOTNULL
- descrizione | TEXT(500) NOTNULL

## materie
- id | BIGINT AI PK
- id_corso | BIGINT AI FK
- nome | VARCHAR(50) NOTNULL
- descrizione | TEXT(500) NOTNULL

## Pivot: materia_insegnante
- id_materia | BIGINT AI FK
- id_insegnante | BIGINT AI FK

## insegnanti
- id | BIGINT AI PK
- nome | VARCHAR(50) NOTNULL
- cognome | VARCHAR(50) NOTNULL

## appelli
- id | BIGINT AI PK
- id_materia | BIGINT AI FK
- data | DATETIME NULL DEFAULT(NULL)

## Pivot: appello_studente
- id_studente FK
- id_appello FK
- voto | TINYINT NOTNULL

## studenti
- id | BIGINT AI PK
- id_corso | BIGINT AI FK
- nome | VARCHAR(50) NOTNULL
- cognome | VARCHAR(50) NOTNULL

