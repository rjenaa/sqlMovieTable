## Movie

 # -- Create a query to find all movies in the Sci-Fi genre.
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

 select Rating, AVG(IMBDScore), min(IMBDScore), max(IMBDScore) 
 from moviesUpdate
 group by Rating;

 select Rating, AVG(IMBDScore), min(IMBDScore), max(IMBDScore) 
 FROM moviesUpdate
 GROUP BY Rating
 HAVING count(*) > 1;

