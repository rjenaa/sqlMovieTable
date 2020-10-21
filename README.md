#Movie


CREATE database movieDataBaseUpdate;
 use movieDataBase;

 CREATE TABLE IF NOT EXISTS moviesUpdate (
 movieID INT UNSIGNED NOT NULL AUTO_INCREMENT,
 Title VARCHAR(40) NOT NULL DEFAULT ' ',
 Runtime INT UNSIGNED NOT NULL DEFAULT 0,
 Genre VARCHAR(30) NOT NULL DEFAULT ' ',
 IMBDScore DECIMAL(2,1) NOT NULL DEFAULT 0,
 Rating VARCHAR(5) NOT NULL DEFAULT ' ',
 PRIMARY KEY (movieID)
 );


 INSERT INTO moviesUpdate VALUES  (1, 'Howard the Duck',
 	110,	'Sci-Fi',	4.6,	'PG');
 INSERT INTO moviesUpdate VALUES  (2, 'Lavalantula',
 	83,	'Horror',	4.7,	'TV-14');
 INSERT INTO moviesUpdate VALUES  (3,'Starship Troopers',
 	129,	'Sci-Fi'	,7.2	,'PG-13');
 INSERT INTO moviesUpdate VALUES  (4,'Waltz With Bashir',
 	90,	'Documentary',	8.0,	'R');
 INSERT INTO moviesUpdate VALUES  (5,'Spaceballs',
 	96,	'Comedy	',7.1	,'PG');
 INSERT INTO moviesUpdate VALUES  (6,'Monsters Inc.	',
 92,	'Animation',	8.1	,'G');
 INSERT INTO moviesUpdate VALUES  (7,'The Shawshank Redemption',
 142,	'Drama',	9.3,	'R');
 INSERT INTO moviesUpdate VALUES  (8,'The Godfather',
 175,	'Crime',	9.2,	'R');
 INSERT INTO moviesUpdate VALUES  (9,'Pulp Fiction',
 154,	'Crime',	8.9,	'R');


 select * FROM moviesUpdate
 Where Genre = "Sci-Fi";

 select * FROM moviesUpdate
 Where IMBDScore >= 6.5;

 select * FROM moviesUpdate
 Where (Rating = "G" OR Rating = "PG")
 And Runtime < 100;


 select Genre, AVG (Runtime)
  From moviesUpdate
 Where IMBDScore < 7.5
 GROUP BY Genre;

 UPDATE moviesUpdate
 SET Rating='R'
 WHERE Title='Starship Troopers';



 select movieID, Rating
 From moviesUpdate
 where (Genre = "Horror" OR Genre = "Documentary");

 select AVG(IMBDScore), min(IMBDScore), max(IMBDScore) 
 from moviesUpdate
 group by Rating;

 select Rating, AVG(IMBDScore), min(IMBDScore), max(IMBDScore) 
 FROM moviesUpdate
 GROUP BY Rating
 HAVING count(*) > 1;

