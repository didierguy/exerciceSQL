CREATE DATABASE team;

USE team;

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

SELECT *
FROM effectif
WHERE commission >0;

SELECT prenom, profession, salaire
FROM effectif
ORDER BY profession ASC, salaire DESC;

SELECT AVG(salaire), id_departement
FROM effectif
GROUP BY id_departement;

SELECT AVG(salaire)
FROM effectif
WHERE id_departement= '2';
