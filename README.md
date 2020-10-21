# Movie

CREATE DATABASE movieDatabase;

use movieDatabase;

CREATE TABLE IF NOT EXISTS movies (
Title VARCHAR(40) NOT NULL DEFAULT ' ',
Runtime INT UNSIGNED NOT NULL DEFAULT 0,
Genre VARCHAR(30) NOT NULL DEFAULT ' ',
IMBDScore DECIMAL(2,1) NOT NULL DEFAULT 0,
Rating VARCHAR(4) NOT NULL DEFAULT ' ',
PRIMARY KEY (Title)
);


INSERT INTO movies VALUES  ('Howard the Duck',
	110,	'Sci-Fi',	4.6,	'PG');
INSERT INTO movies VALUES  ('Lavalantula',
	83,	'Horror',	4.7,	'TV-14');
INSERT INTO movies VALUES  ('Starship Troopers',
	129,	'Sci-Fi'	,7.2	,'PG-13');
INSERT INTO movies VALUES  ('Waltz With Bashir',
	90,	'Documentary',	8.0,	'R');
INSERT INTO movies VALUES  ('Spaceballs',
	96,	'Comedy	',7.1	,'PG');
INSERT INTO movies VALUES  ('Monsters Inc.	',
92,	'Animation',	8.1	,'G');
INSERT INTO movies VALUES  ('The Shawshank Redemption',
142,	'Drama',	9.3,	'R');
INSERT INTO movies VALUES  ('The Godfather',
175,	'Crime',	9.2,	'R');
INSERT INTO movies VALUES  ('Pulp Fiction',
154,	'Crime',	8.9,	'R');

select * FROM movies
Where Genre = "Sci-Fi";

select * FROM movies
Where IMBDScore >= 6.5;

select * FROM movies
Where (Rating = "G" OR Rating = "PG")
And Runtime < 100;


select Genre, AVG (Runtime)
 From movies
Where IMBDScore < 7.5
GROUP BY Genre;

UPDATE movies
SET Rating='R'
WHERE Title='Starship Troopers';



select Title, Rating
From movies
where (Genre = "Horror" OR Genre = "Documentary");

select AVG(IMBDScore), min(IMBDScore), max(IMBDScore) 
from movies
group by Rating;

select Rating, AVG(IMBDScore), min(IMBDScore), max(IMBDScore) 
FROM movies
GROUP BY Rating
HAVING count(*) > 1;
