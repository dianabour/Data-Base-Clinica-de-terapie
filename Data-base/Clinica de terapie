DATABASE_PROJECT
Application under test: Clinica de terapie

Tools used: MySQL Workbench

Database description:Clinica de terapie ,,Kids Therapy’’ are ca scop recuperarea copiilor cu TSA (Tulburare de spectru autist) si alte intarzieri in dezvoltare.
Aceasta este formata dintr-o echipa de 3 terapeuti, si un coordonator de programe. Fiecare terapeut are minim un copil in programul de terapie, si maxim 4 copii. O sedinta de terapie dureaza 2 ore (120 min). 
Copiii din cadrul clinicii de terapie au varste cuprinse intre 2 si 8 ani.
Exista mai multe tipuri de terapie in cadrul clinicii (ABA, Logopedie, Ludoterapie, Meloterapie).
Fiecare copil beneficiaza de un plan de interventie personalizat pe nevoile sale, in concordanta cu cele 5 arii de dezvoltare la copil(motricitate,limbaj, socializare, cognitie, autoservire). Acesta este conceput de catre coordonatorul de programe.
Activitatea se desfasoara zilnic, de luni pana vineri, iar parintii pot opta pentru un program full de terapie, sau doar de cateva ori pe saptamana, in functie de nevoi.
Participarea copiilor in cadrul sedintelor de terapie va fi inregistrata in fisa de prezenta disponibila.


1. Database schema:
You can find below the database schema that was generated through Reverse Engineer and which contains all the tables and the relationships between them.
The tables are connected in the following way:

You can find below the database schema that was generated through Reverse Engineer and which contains all the tables and the relationships between them.
The tables are connected in the following way:

**PROGRAM** is connected with **PACIENTI** through a **ONE TO MANY** relationship which was implemented through 
**PROGRAM.ID_PROGRAM** as a primary key and **PROGRAM.CNP_PACIENT** as a foreign key.
**PROGRAM** is connected with **TERAPEUTI** through a **ONE TO MANY** relationship which was implemented through 
**PROGRAM.ID_PROGRAM** as a primary key and **PROGRAM.CNP_TERAPEUTI** as a foreign key.
**PROGRAM** is connected with **ZILE** through a **ONE TO MANY** relationship which was implemented through 
**PROGRAM.ID_PROGRAM** as a primary key and **PROGRAM.ID_ZI** as a foreign key
**PLAN_DE_INTERVENTIE** is connected with **PACIENTI** through a **ONE TO MANY** relationship which was implemented through 
**PLAN_DE_INTERVENTIE.CNP_TERAPEUT** as a primary key and **PLAN_DE_INTERVENTIE.CNP_PACIENT** as a foreign key.
**PLAN_DE_INTERVENTIE** is connected with **ARII_DEZVOLTARE** through a **ONE TO MANY** relationship which was implemented through 
**PLAN_DE_INTERVENTIE.CNP_TERAPEUT** as a primary key and **PLAN_DE_INTERVENTIE.ID_ARIE** as a foreign key.
**PLAN_DE_INTERVENTIE** is connected with **TERAPII_INTEGRATE** through a **ONE TO MANY** relationship which was implemented through 
**PLAN_DE_INTERVENTIE.CNP_TERAPEUT** as a primary key and **PLAN_DE_INTERVENTIE.ID_ARIE** as a foreign key.
**PREZENTA** is connected with **ZILE** through a **ONE TO ONE** relationship which was implemented through 
**PREZENTA.ID_PREZENTA** as a primary key and **PREZENTA.ID_ZI** as a foreign key.

2. Database Queries

DDL (Data Definition Language)
The following instructions were written in the scope of CREATING the structure of the database (CREATE INSTRUCTIONS).
CREATE DATABASE CLINICA_TERAPIE;

USE CLINICA_TERAPIE;

CREATE TABLE TERAPEUTI (
	CNP INT PRIMARY KEY,
	NUME CHAR(10),
	PRENUME VARCHAR(20),
	STUDII VARCHAR(25),
	VARSTA INT,
	DATA_INCEPERE DATE,
	DATA_INCHEIERE DATE,
	COORDONATOR CHAR(10)
);
CREATE TABLE PACIENTI (
	CNP INT PRIMARY KEY,
	NUME VARCHAR(20),
	PRENUME CHAR(10),
	DIAGNOSTIC VARCHAR(25),
	VARSTA INT,
	NIVEL_EDUCATIONAL VARCHAR(25)
);
CREATE TABLE TERAPII_INTEGRATE (
ID_TERAPIE INT NOT NULL AUTO_INCREMENT,
DENUMIRE VARCHAR(20),
PRIMARY KEY (ID_TERAPIE)
);
CREATE TABLE ARII_DEZVOLTARE (
ID_ARIE INT NOT NULL AUTO_INCREMENT,
ARIE VARCHAR(20),
PRIMARY KEY (ID_ARIE)
);
CREATE TABLE ZILE (
ID_ZI INT NOT NULL AUTO_INCREMENT,
ZI CHAR(10),
PRIMARY KEY (ID_ZI)
);
CREATE TABLE PROGRAM (
ID_PROGRAM INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
CNP_TERAPEUT INT,
CNP_COPIL INT,
ORA_INCEPERE INT,
ORA_INCHEIERE INT,
ID_ZI INT REFERENCES ZILE (ID_ZI)
);
CREATE TABLE PREZENTA (
ID_ZI INT REFERENCES ZILE (ID_ZI),
DATAA DATE,
PREZENTA CHAR(10)
);
CREATE TABLE PLAN_DE_INTERVENTIE (
CNP_TERAPEUT INT,
CNP_PACIENT INT,
ID_ARIE INT REFERENCES ARII_DEZVOLTARE (ID_ARIE),
ID_TERAPIE INT REFERENCES TERAPII_INTEGRATE (ID_TERAPIE),
ACTIVITATI VARCHAR(50)
);

After the database and the tables have been created, a few ALTER instructions were written in order to update the structure of the database, as described below:
ALTER TABLE PLAN_DE_INTERVENTIE ADD CONSTRAINT FK_ID_ARIE FOREIGN KEY (ID_ARIE) REFERENCES ARII_DEZVOLTARE(ID_ARIE);

ALTER TABLE PLAN_DE_INTERVENTIE ADD CONSTRAINT FK_ID_TERAPIE FOREIGN KEY (ID_TERAPIE) REFERENCES TERAPII_INTEGRATE(ID_TERAPIE);

ALTER TABLE PLAN_DE_INTERVENTIE ADD CONSTRAINT FK_CNP_PACIENT FOREIGN KEY (CNP_PACIENT) REFERENCES PACIENTI(CNP);

ALTER TABLE PROGRAM ADD CONSTRAINT FK_ID_ZI FOREIGN KEY (ID_ZI) REFERENCES ZILE(ID_ZI);

ALTER TABLE ARII_DEZVOLTARE CHANGE ARIE ARIA VARCHAR(20);

ALTER TABLE PREZENTA ADD CONSTRAINT FK_zi_prezenta FOREIGN KEY (ID_ZI) REFERENCES ZILE(ID_ZI);

ALTER TABLE PROGRAM ADD CONSTRAINT FK_CNP_TERAPEUT FOREIGN KEY (CNP_TERAPEUT) REFERENCES TERAPEUTI(CNP);

ALTER TABLE PROGRAM ADD CONSTRAINT FK_CNP_COPIL FOREIGN KEY (CNP_COPIL) REFERENCES PACIENTI(CNP);

DML (Data Manipulation Language)
In order to be able to use the database I populated the tables with various data necessary in order to perform queries and manipulate the data. In the testing process, this necessary data is identified in the Test Design phase and created in the Test Implementation phase.

Below you can find all the insert instructions that were created in the scope of this project:
INSERT INTO TERAPEUTI (CNP, NUME, PRENUME, STUDII, VARSTA, DATA_INCEPERE, DATA_INCHEIERE, COORDONATOR)
VALUES (21212, 'BOUR', 'DIANA', 'Superioare -FPSE', 26, '2024-07-01', NULL, 'FALSE'),
	   (23232, 'POSTELNICU', 'ANA-MARIA', 'SUPERIOARE-FPSE', 25, '2022-12-15', NULL, 'FALSE'),
	   (24242, 'GHIOC', 'DENISA', 'SUPERIOARE-FPSE', 32, '2023-02-28', NULL, 'FALSE'),
	   (25252, 'CRISMARU', 'ELIZA', 'SUPERIOARE-FPSE', 33, '2022-07-01', NULL, 'TRUE'),
       (26262, 'POPESCU', 'ION', 'SUPERIOARE-FPSE', 29, '2022-08-03', '2022-12-10', 'FALSE'),
       (27272, 'IONESCU', 'ALEXANDRU', 'SUPERIOARE-FPSE', 27, '2022-10-15', '2023-02-01', 'FALSE'),
       (28282, 'STANCIU', 'MIHAELA', 'SUPERIOARE-FPSE', 26, '2023-11-15', '2024-05-20', 'FALSE');

INSERT INTO PACIENTI (CNP, NUME, PRENUME, DIAGNOSTIC, VARSTA, NIVEL_EDUCATIONAL)
VALUES (31313, 'ANDREI', 'PAUL', 'TSA', 4, 'GRADINITA-GRUPA MICA'),
	   (32323, 'MORARU', 'LUCA', 'TSA', 4, 'GRADINITA-GRUPA MICA'),
       (34343, 'NECULA', 'STEFAN', 'TSA', 3, 'GRADINITA-GRUPA MICA'),
       (35353, 'DUMITRU', 'CRISTIAN', 'TSA/SINDROM HIPERKINETIC', 8, 'SCOALA PRIMARA-CLASA 1'),
       (41414, 'DIMITRIU', 'DEBORAH', 'TSA', 4, 'GRADINITA-GRUPA MARE'),
       (42424, 'VLADA', 'ERIC', 'TSA', 4, 'GRADINITA-GRUPA MARE'),
       (43434, 'RUSU', 'MATTEO', 'TSA', 4, 'GRADINITA-GRUPA MARE'),
       (45454, 'ABUDICIOAEI', 'ZIAN', 'TSA', 8, 'SCOALA PRIMARA-CLASA 1'),
	   (51515, 'MARITA', 'MATTEO', 'INTARZIERE IN DEZVOLTARE', 2, 'CRESA'),
       (52525, 'MUTU', 'VICTORIA', 'TSA', 2, 'CRESA'),
       (53535, 'ION', 'LUCA', 'TSA', 8, 'SCOALA PRIMARA-CLASA 1'),
       (54545, 'BOSTAN', 'TEODOR', 'TSA', 4, 'GRADINITA-GRUPA MARE'),
       (11111, 'liber', 'liber', '-', 0, 'liber');

INSERT INTO TERAPII_INTEGRATE (ID_TERAPIE, DENUMIRE)
VALUES (1, 'ABA'),
       (2, 'LOGOPEDIE'),
       (3, 'LUDOTERAPIE'),
	   (4, 'MELOTERAPIE');

INSERT INTO ARII_DEZVOLTARE (ID_ARIE, ARIA)
VALUES (1, 'MOTRICITATE'),
       (2, 'LIMBAJ'),
       (3, 'SOCIALIZARE'),
       (4, 'COGNITIV'),
       (5, 'AUTOSERVIRE');

INSERT INTO ZILE (ID_ZI, ZI)
VALUES (1, 'LUNI'),
	   (2, 'MARTI'),
       (3, 'MIERCURI'),
       (4, 'JOI'),
       (5, 'VINERI');

INSERT INTO PROGRAM (ID_PROGRAM, CNP_TERAPEUT, CNP_COPIL, ORA_INCEPERE, ORA_INCHEIERE, ID_ZI)
VALUES (1, 21212, 54545, 8, 10, 1),
		(2, 23232, 41414, 8, 10, 1),
		(3, 24242, 32323, 8, 10, 1),
		(4, 21212, 52525, 10, 12, 1),
		(5, 23232, 42424, 10, 12, 1),
		(6, 24242, 31313, 10, 12, 1),
		(7, 21212, 11111, 12, 14, 1),
		(8, 23232, 43434, 12, 14, 1),
		(9, 24242, 34343, 12, 14, 1),
		(10, 21212, 54545,	14, 16,	1),
		(11, 23232, 45454,	14, 16,	1),
		(12, 24242, 35353, 14, 16,	1),
		(13, 21212, 51515,	8, 10, 2),
		(14, 23232, 41414,	8, 10, 2),
		(15, 24242, 11111,	8, 10, 2),
		(17, 23232, 42424,10, 12, 2),
		(18, 24242, 11111, 10, 12, 2),
		(19, 21212, 11111, 12, 14, 2),
		 (20, 23232, 43434, 12, 14, 2),
		 (21, 24242, 34343, 12, 14, 2),
		 (22, 21212, 54545, 14, 16, 2),
		 (23, 23232, 45454, 14, 16, 2),
		 (24, 24242, 35353, 14, 16, 2),
		 (25, 21212, 51515, 8, 10, 3),
		 (26, 23232, 41414, 8, 10, 3),
		 (27, 24242, 32323, 8, 10, 3),
		 (28, 21212, 52525, 10, 12, 3),
		 (29, 23232, 11111, 10, 12,	3),
		 (30, 24242, 31313, 10, 12, 3),
		 (31, 21212, 53535, 12, 14,	3),
		 (32, 23232, 43434, 12, 14, 3),
		 (33, 24242, 34343, 12, 14,	3),
		(34, 21212, 54545, 14, 16, 3),
		(35, 23232, 45454, 14, 16, 3),
		(36, 24242, 35353, 14, 16, 3),
		(37, 21212, 51515, 8, 10, 4),
		(38, 23232, 41414, 8, 10, 4),
		(39, 24242, 11111, 8, 10, 4),
		(40, 21212, 52525, 10, 12,4),
		(41, 23232, 42424, 10, 12, 4),
		(42, 24242, 11111,	10, 12,	4),
		(43, 21212, 53535, 12, 14, 4),
		(44, 23232, 43434, 12, 14, 4),
		 (45, 24242, 34343, 12, 14, 4),
		 (46, 21212, 54545, 14, 16, 4),
		 (47, 23232, 45454, 14, 16, 4),
		(48, 24242, 35353, 14, 16, 4),
		(49, 21212, 51515, 8, 10, 5),
		(50, 23232, 41414, 8, 10, 5),
		(51, 24242, 32323, 8, 10, 5),
		(52, 21212, 52525, 10, 12, 5),
		(53, 23232, 42424, 10, 12, 5),
		(54, 24242, 31313, 10, 12, 5),
		(55, 21212, 53535, 12, 14, 5),
		(56, 21212, 54545, 12, 14, 5),
		(57, 23232, 43434, 12, 14, 5),
		(58, 24242, 34343,	12, 14,	5),
		(59, 24242, 35353, 12, 14, 5),
        #######
        (60, 27272, 42424, 10, 12, 1),
        (61, 27272, 43434, 10, 12, 2),
        (62, 25252, 53535, 10, 12, 2),
        (63, 25252, 51515, 10, 12, 2),
        (64, 25252, 43434, 10, 12, 2);

INSERT INTO PREZENTA (ID_ZI, DATAA, PREZENTA)
VALUES (1, '2024-05-06', 'TRUE'),
		(1, '2024-05-13', 'TRUE'),
		(1, '2024-05-20', 'TRUE'),
		(1, '2024-05-27', 'TRUE'),
		(2, '2024-05-07', 'TRUE'),
		(2, '2024-05-14', 'TRUE'),
		(2, '2024-05-21', 'FALSE'),
		(2, '2024-05-28', 'TRUE'),
		(3, '2024-05-01', 'TRUE'),
		(3, '2024-05-08', 'TRUE'),
		(3, '2024-05-15', 'TRUE'),
		(3, '2024-05-22', 'TRUE'),
		(3, '2024-05-29', 'TRUE'),
		(4, '2024-05-02', 'TRUE'),
		(4, '2024-05-09', 'TRUE'),
		(4, '2024-05-16', 'FALSE'),
		(4, '2024-05-23', 'FALSE'),
		(4, '2024-05-30', 'TRUE'),
		(5, '2024-05-03', 'TRUE'),
		(5, '2024-05-10', 'TRUE'),
		(5, '2024-05-17', 'TRUE'),
		(5, '2024-05-24', 'TRUE'),
		(5, '2024-05-31', 'TRUE');

INSERT INTO PLAN_DE_INTERVENTIE (CNP_TERAPEUT, CNP_PACIENT, ID_ARIE, ACTIVITATI)
VALUES (25252, 31313, 1, 'INSIRAT OBIECTE PE SNUR'),
		(25252, 31313, 2, 'IMITATIE VERBALA'),
		(25252, 31313, 3, 'DA NOROC CU COPII'),
		(25252, 31313, 4, 'POTRIVIRE OBIECTE 3D-3D'),
		(25252, 31313, 5, 'MANANCA INDEPENDENT'),
		(25252, 32323, 1, 'COLORAT'),
		(25252, 32323, 2, 'RECIPROCITATE CU OBIECT'),
		(25252, 32323, 3, 'ASTEPTAREA RANDULUI'),
		(25252, 32323, 4, 'INTREBARI DE CULTURA GENERALA'),
		(25252, 32323, 5, 'IMBRACAT INDEPENDENT'),
		(25252, 34343, 1, 'SARE IN 2 PICIOARE'),
	    (25252, 34343, 2, 'IMITATIE VERBALA PE PROPOZITII'),
		(25252, 34343,	3, 'SALUTA COPIII CU BUNA/PA'),
		(25252, 34343, 4, 'EXPRESIV PARTILE CORPULUI'),
		(25252, 34343, 5, 'IA UN BOL SI PUNE IN CHIUVETA'),
		(25252, 35353, 1, 'SCRIS LITERE/CIFRE'),
		(25252, 35353, 2, 'EXPRIMAREA NEVOILOR'),
		(25252, 35353, 3, 'JOC SIMBOLIC IN GRUP'),
		 (25252, 35353,	4, 'BUNELE MANIERE'),
		 (25252, 35353,	5, 'DA CU MATURA SINGUR'),
		 (25252, 41414, 1, 'COLORAT IN CONTUR'),
		 (25252, 41414,	2, 'CERERI COMPLEXE'),
		 (25252, 41414,	3, 'CONTACT VIZUAL CU COPIII'),
		 (25252, 41414,	4, 'NOTIUNI/ANALOGII OPUSE'),
		(25252, 41414, 5, 'IMBRACAT INDEPENDENT'),
		(25252, 42424, 1, 'SARIT INTR-UN PICIOR'),
		(25252, 42424, 2, 'IMITATIE VERBALA PE VOCALE'),
		(25252, 42424, 3, 'BATE PALMA CU COPIII'),
		 (25252, 42424, 4, 'RECEPTIV OBIECTE DIN  MEDIU'),
		(25252, 42424, 5, 'MANANCA INDEPENDENT'),
		(25252, 43434, 1, 'TINE CREIONUL IN MANA'),
		(25252, 43434, 2, 'IMITATIE VERBALA PE CUVINTE'),
		 (25252, 43434,	3, 'SALUTA CU BUNA SI PA'),
		(25252, 43434, 4, 'EXPRESIV FRUCTE SI LEGUME'),
		(25252, 43434, 5, 'DESCALTAT INDEPENDENT'),
		(25252, 45454, 1, 'SCRIS LITERE DE MANA'),
		(25252, 45454, 2, 'PUNE INTREBARI PERSOANELOR'),
		(25252, 45454, 3, 'FACE CUNOSTINTA CU PERSOANE'),
		 (25252, 45454,	4, 'NUMARAT 1-20/20-1'),
		(25252, 45454, 5, 'AJUTA PARINTII PRIN CASA'),
		(25252, 51515, 1, 'INCHIDE/DESCHIDE PUMNUL'),
		(25252, 51515, 2, 'INTREBARI SOCIALE'),
		(25252, 51515, 3, 'INTRA IN JOCUL COPIILOR'),
		(25252, 51515, 4, 'MESERII/LOCATII/INCAPERI'),
		 (25252, 51515, 5, 'TRAINING DE TOALETA'),
		 (25252, 52525, 1, 'PUNE PIONEZE'),
		 (25252, 52525,	2, 'IMITATIE VERBALA PE ONOMATOPEE'),
		(25252, 52525, 3, 'BATE PALMA CU COPIII'),
		(25252, 52525, 4, 'POTRIVIRE NON-IDENTICA'),
		(25252,	52525, 5, 'BEA APA DIN CANA'),
		(25252,	53535, 1, 'SCRIS LITERE/CIFRE'),
		(25252,	53535, 2, 'VORBIT IN PROPOZITII'),
		(25252,	53535, 3, 'JOC LA COMUN CU COPII'),
		(25252,	53535,	4, 'BUNE MANIERE'),
		(25252,	53535,	5,	'AJUTA PARINTII PRIN CASA'),
		(25252, 54545, 1, 'PREGATIRE PENTRU SCRIS'),
		(25252,	54545, 2, 'CERERI COMPLEXE/EXPRIMAREA NEVOILOR'),
		(25252,	54545, 3, 'IMPARTE JUCARIILE CU COPII'),
		(25252,	54545, 4, 'INTREBARI DE CULTURA GENERALA'),
		(25252,	54545, 5, 'INCHIDE FERMOARUL INDEPENDENT');

DQL (Data Query Language)
In order to simulate various scenarios that might happen in real life I created the following queries that would cover multiple potential real-life situations:
## Afisarea tuturor datelor personale disponibile pentru toti pacientii
SELECT * FROM PACIENTI;

## Afisarea CNP-ului, numelui si prenumelui tuturor pacientilor clinicii 
SELECT CNP, NUME, PRENUME FROM PACIENTI;

## Afisarea CNP-ului, numelui si prenumelui tuturor pacientilor in varsta de 4 ani 
SELECT CNP, NUME, VARSTA FROM PACIENTI WHERE VARSTA = 4;

## Afisarea CNP-ului, numelui si prenumelui tuturor pacientilor in varsta de PESTE 4 ani 
SELECT CNP, NUME, VARSTA FROM PACIENTI WHERE VARSTA >= 4;

## Afisarea CNP-ului, numelui si prenumelui tuturor pacientilor in varsta de SUB 4 ani
SELECT CNP, NUME, VARSTA FROM PACIENTI WHERE VARSTA <= 4;

## Afisarea CNP-ului, numelui si prenumelui tuturor pacientilor cu varsta mai mare decat media varstei pacientilor din clinica
SELECT CNP, NUME, VARSTA FROM PACIENTI 
where varsta >= (select avg(varsta) from pacienti); 

## Care este cel mai in varsta pacient? 
SELECT CNP, NUME, PRENUME, VARSTA
FROM PACIENTI
WHERE VARSTA = (SELECT MAX(VARSTA) FROM Pacienti);                  

## Afisare tabela CNP din Pacienti unde CNP-ul cuprinde caracterele '21' (dar nu se cunosc toate caracterele) sau numele este Dumitru
SELECT * FROM PACIENTI 
WHERE CNP LIKE '31%'  
or NUME = 'Dumitru';

## Afisarea detaliilor pentru pacientii cu numele Marita si prenumele Matteo sau numele Andrei si prenumele Paul
SELECT NUME, PRENUME FROM PACIENTI 
WHERE (NUME = 'MARITA' AND PRENUME = 'MATTEO')
   OR (NUME = 'ANDREI' AND PRENUME = 'PAUL');

## Cati pacienti sunt in clinica la data curenta?
SELECT sysdate(), COUNT(*) FROM PACIENTI;

## Care sunt pacientii (nume, prenume si varsta) terapeutului Diana Bour?
SELECT distinct p.nume, p.prenume, p.varsta FROM PACIENTI P
JOIN PROGRAM PR  ON PR.CNP_COPIL    = P.CNP
JOIN TERAPEUTI T ON PR.CNP_TERAPEUT = T.CNP
WHERE T.NUME = 'Bour'
and T.PRENUME = 'Diana'; 

## Care sunt terapeutii cu numar de pacienti de peste 5 pacienti?
SELECT t.nume, t.prenume, count(*) FROM PACIENTI P
JOIN PROGRAM PR  ON PR.CNP_COPIL    = P.CNP
JOIN TERAPEUTI T ON PR.CNP_TERAPEUT = T.CNP
group by t.nume, t.prenume
having count(*) > 5;

## Care sunt activitatile specifice ariei de dezvoltare de motricitate? 
select pdi.activitati
FROM plan_de_interventie pdi
JOIN arii_dezvoltare ad ON ad.id_arie = pdi.id_arie
WHERE ad.aria = 'motricitate';
