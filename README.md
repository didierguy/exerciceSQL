CREATE DATABASE team;

USE team;

REQ: Créer les deux tables en sql:
CREATE TABLE `effectif` (
  `id` INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
  `prenom` VARCHAR(50) NOT NULL,
  `profession` VARCHAR(50) NOT NULL,
  `dateemb` DATE NOT NULL,
  `salaire` INT(5) NULL,
  `commission` INT (5) NULL,
  `id_departement`INT (2) NULL
);

CREATE TABLE `departement` (
  `id` INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
  `nom` VARCHAR(50) NOT NULL,
  `ville` VARCHAR(50) NOT NULL,
  `numerodepartement` INT (2) NOT NULL
);

REQ0: Insérez les données dans les tables:
INSERT INTO effectif (prenom, profession, dateemb, salaire, commission, id_departement)
 VALUES
 ('Pierre', 'Ingénieur', '1993-10-01', 4000, 3000, 1),
 ('Paul', 'Technicien', '1988-05-10', 3000, 2000, 2),
 ('Jacques', 'Vendeur', '1980-10-29', 5000, 5000, 2),
 ('Yavuz', 'Président', '2019-10-29', 10000, 10000, 3),
 ('Aljio', 'Vendeur', '1980-10-29', 7000, 2000, 2),
 ('Bill', 'Stagiaire', '2018-10-29', 1000, 0, 1);

INSERT INTO departement (nom, ville, numerodepartement)
 VALUES
 ('Commercial', 'Strasbourg', 67),
 ('Developpement', 'Lyon', 69),
 ('Dierction', 'Paris', 75);
 
REQ1: Donnez la liste des employés ayant une commision:
SELECT *
FROM effectif
WHERE commission >0;

REQ2: Donnez les prenoms, professions et salaires des employés par profession croissant, et pour chaque profession, par salaire décroissant:
SELECT prenom, profession, salaire
FROM effectif
ORDER BY profession ASC, salaire DESC;

REQ3: Donnez le salaire moyen des employés par nom département:
SELECT nom, AVG(E.salaire)
FROM effectif E, departement D
WHERE d.id=E.id_departement
GROUP BY nom;

REQ4: Donnez le salaire moyen du département Developpement:
SELECT AVG(salaire)
FROM effectif
WHERE id_departement= 2;

REQ5: Donnez les numéros de département et leur salaire maximum:
SELECT D.numerodepartement, MAX(E.salaire)
FROM effectif E, Departement D 
WHERE E.id_departement=D.id 
GROUP BY E.id_departement;

REQ6: Donnez les employés ayant le salaire maximum pour chaque nom département:
SELECT E.prenom, MAX(salaire) 
FROM effectif E, Departement D 
WHERE D.id=E.id_departement 
GROUP BY D.nom;

REQ7: Donnez les différentes professions et leur salaire moyen:
SELECT profession, AVG(salaire) 
FROM effectif 
GROUP BY profession;

REQ8: Donnez le salaire moyen par profession:
SELECT AVG(salaire) as Moyenne 
FROM effectif 
GROUP BY profession 
ORDER BY Moyenne 
ASC LIMIT 1;
