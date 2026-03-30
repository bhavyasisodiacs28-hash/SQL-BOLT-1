Exercise-06 - Multi-table queries with JOINs

1. Find the domestic and international sales for each movie
    
SELECT Title, International_sales, Domestic_sales
FROM Movies JOIN Boxoffice
ON Id=Movie_id;

2. Show the sales numbers for each movie that did better internationally rather than domestically
    
SELECT Title, International_sales, Domestic_sales
FROM Movies JOIN Boxoffice
ON Id=Movie_id
WHERE International_sales > Domestic_sales;

3. List all the movies by their ratings in descending order

SELECT Title, Rating
FROM Movies JOIN Boxoffice
ON Id=Movie_id
ORDER BY Rating DESC;

Exercise-07 - OUTER JOIN
    
1. Find the list of all buildings that have employees
    
SELECT DISTINCT Building
FROM Employees
LEFT JOIN Buildings ON Building=Building_name
WHERE Years_employed NOT NULL;

2. Find the list of all buildings and their capacity
    
SELECT *
FROM Buildings;

3. List all buildings and the distinct employee roles in each building (including empty buildings)
    
SELECT DISTINCT Building_name, Role 
FROM Buildings 
LEFT JOIN employees ON building_name = building;

Exercise-08 - A short note on NULLs

1. Find the name and role of all employees who have not been assigned to a building
    
SELECT *
FROM Employees
LEFT JOIN Buildings
ON Building_name = Building
WHERE Building IS NULL;

2. Find the names of the buildings that hold no employees
    
SELECT *
FROM Buildings
LEFT JOIN Employees
ON Building_name = Building
WHERE Building IS NULL;

Exercise-09 - Queries with expressions

1. List all movies and their combined sales in millions of dollars
    
SELECT Title, (Domestic_sales + International_sales)/1000000 AS Total_Sales_Millions
FROM Movies
LEFT JOIN Boxoffice ON Id=Movie_Id;

2. List all movies and their ratings in percent
    
SELECT Title, Rating*10 as Percent
FROM Movies
LEFT JOIN Boxoffice ON Id=Movie_Id;

3. List all movies that were released on even number years
    
SELECT Title, Year
FROM Movies
LEFT JOIN Boxoffice ON Id=Movie_Id
WHERE Year % 2 = 0;

Exercise-10 - Queries with aggregates (Pt01)

1. Find the longest time that an employee has been at the studio
    
SELECT MAX(Years_employed)
FROM Employees;

2. For each role, find the average number of years employed by employees in that role
    
SELECT Role, AVG(Years_Employed) 
FROM Employees
GROUP BY Role;

3. Find the total number of employee years worked in each building
    
SELECT Building, SUM(Years_Employed) 
FROM Employees
GROUP BY Building;

Exercise-11 - Queries with aggregates (Pt02)

1. Find the number of Artists in the studio (without a HAVING clause)
    
SELECT Role, COUNT(*) AS Number_of_Artists
FROM Employees
WHERE Role = "Artist";

2. Find the number of Employees of each role in the studio
    
SELECT Role, COUNT(*)
FROM Employees
GROUP BY Role;

3. Find the total number of years employed by all Engineers
    
SELECT Role, SUM(Years_Employed)
FROM Employees
GROUP BY Role
HAVING Role = "Engineer";

Exercise-12 - Order of execution of a Query

1. Find the number of movies each director has directed
    
SELECT *, COUNT(Title)
FROM Movies
GROUP BY Director;

2. Find the total domestic and international sales that can be attributed to each director
    
SELECT Director, sum(Domestic_sales + International_Sales) as Total_Sales
FROM Movies
LEFT JOIN Boxoffice ON Id = Movie_ID
GROUP BY Director;

Exercise-13 - Inserting rows

1. Add the studio's new production, Toy Story 4 to the list of movies (you can use any director)
    
INSERT INTO Movies,
VALUES (4, "Toy Story 4", "John Lasseter", 2017, 123);

2. Toy Story 4 has been released to critical acclaim! It had a rating of 8.7, and made 340 million domestically and 270 million internationally. Add the record to the  BoxOffice table.
    
INSERT INTO Boxoffice
VALUES (4, 8.7, 340000000, 270000000);

Exercise-14 - Updating rows

1. The director for A Bug's Life is incorrect, it was actually directed by John Lasseter
    
UPDATE Movies
SET Director = "John Lasseter"
WHERE Id = 2;

2. The year that Toy Story 2 was released is incorrect, it was actually released in 1999
    
UPDATE Movies
SET Year = "1999"
WHERE Id = 3;

3. Both the title and directory for Toy Story 8 is incorrect! The title should be "Toy Story 3" and it was directed by Lee Unkrich
    
UPDATE Movies
SET Title = "Toy Story 3", Director = "Lee Unkrich"
WHERE Id = 11;

Exercise-15 - Deleting rows

1. This database is getting too big, lets remove all movies that were released before 2005.
    
DELETE FROM Movies
WHERE Year < 2005;

2. Andrew Stanton has also left the studio, so please remove all movies directed by him.
    
DELETE FROM Movies
WHERE Director = "Andrew Stanton";

Exercise-16 - Creating Tables
    
CREATE TABLE Database (
    Name TEXT,
    Version FLOAT,
    Download_Count INTEGER);
    
Exercise-17 - Altering Tables

1. Add a column named Aspect_ratio with a FLOAT data type to store the aspect-ratio each movie was released in.
    
ALTER TABLE Movies
  ADD COLUMN Aspect_ratio FLOAT DEFAULT 3;
  
2. Add another column named Language with a TEXT data type to store the language that the movie was released in. Ensure that the default for this language is English.
    
ALTER TABLE Movies
  ADD COLUMN Language TEXT DEFAULT "English";

Exercise-18 - Dropping Tables

DROP TABLE Movies;

DROP TABLE BoxOffice;
