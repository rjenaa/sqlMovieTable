# Movie

 ## -- Create a query to find all movies in the Sci-Fi genre.
 select * FROM moviesUpdate
 Where Genre = "Sci-Fi";

## -- Create a query to find all films that scored at least a 6.5 on IMDB
 select * FROM moviesUpdate
 Where IMBDScore >= 6.5;

## -- create a query to find all of the movies rated G or PG that are less than 100 minutes long.
 select * FROM moviesUpdate
 Where (Rating = "G" OR Rating = "PG")
 And Runtime < 100;

## -- Create a query to show the average runtimes of movies scoring below a 7.5 on imdb, grouped by their respective genres.
 select Genre, AVG (Runtime)
  From moviesUpdate
 Where IMBDScore < 7.5
 GROUP BY Genre;

## -- Create a query that finds the movie by its title and changes its rating to R.
 UPDATE moviesUpdate
 SET Rating='R'
 WHERE Title='Starship Troopers';

## -- Show the ID number and rating of all of the Horror and Documentary movies in the database. Do this in only one query.
 select movieID, Rating
 From moviesUpdate
 where (Genre = "Horror" OR Genre = "Documentary");

## -- find the average, maximum, and minimum IMDB score for movies of each rating.
 select Rating, AVG(IMBDScore), min(IMBDScore), max(IMBDScore) 
 from moviesUpdate
 group by Rating;

## --  Use a HAVING COUNT(*) > 1 clause to only show ratings with multiple movies showing.
 select Rating, AVG(IMBDScore), min(IMBDScore), max(IMBDScore) 
 FROM moviesUpdate
 GROUP BY Rating
 HAVING count(*) > 1;

