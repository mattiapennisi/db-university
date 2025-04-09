## Table name: 'dipartimenti'

** Columns: ** 

- id: BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- nome: VARCHAR(50) - NOTNULL
- indirizzo: VARCHAR(50) - NOTNULL
- email: VARCHAR(50) - NOTNULL

## Table name: 'corsi_di_laurea'

** Columns: ** 

- id: BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- nome: VARCHAR(50) - NOTNULL
- dipartimento_id: BIGINT - FOREIGN KEY - NOTNULL 
- tipo: VARCHAR(20) - NOTNULL

## Table name: 'corsi'

** Columns: **

- id: BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- nome: VARCHAR(50) - NOTNULL
- anno: YEAR() - NOTNULL
- cfu: TINYINT - NOTNULL

## Table name: 'insegnanti'

** Columns: **

- id: BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- nome: VARCHAR(50) - NOTNULL
- cognome: VARCHAR(50) - NOTNULL
- email: VARCHAR(50) - NOTNULL

## Table name: 'appelli'

** Columns: **

- id: BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- corso_id: BIGINT - FOREIGN KEY 
- data: DATE() - NOTNULL
- orario: TIME() - NOTNULL

## Table name: 'studenti'

** Columns: **

- id: BIGINT - PRIMARY_KEY - AUTO-INCREMENT - NOTNULL
- nome: VARCHAR(50) - NOTNULL
- cognome: VARCHAR(50) - NOTNULL
- corso_di_laurea_id: BIGINT - FOREIGN KEY - NOTNULL 