1. Find the author with the name 'Kara Melton' and then select all the articles she has written.

SELECT * FROM authors WHERE name = 'Kara Melton';
 id |    name     |                                                                                                                   bio                                                                                                                   
----+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  8 | Kara Melton | Kara is a Master’s Candidate in the Department of Gender Studies at Queen’s University. She researches questions of racial progress and spends time thinking on community building, startups, tech and design, board games, and donuts.


SELECT title FROM articles WHERE author_id = 8;
                                              title                                               
--------------------------------------------------------------------------------------------------
 How Tech Business Models Come From Marginalized Communities, But Startups Are Still Mostly White
 Confronting the Assumption of Whiteness in Virtual Spaces

2. Find Ontario in the provinces table and then find all the cities in that province.
SELECT * FROM provinces  WHERE name = 'Ontario';
 id |  name   | year_founded | country_id 
----+---------+--------------+------------
 14 | Ontario |         1867 |          1
(1 row)

SELECT * FROM cities WHERE province_id = 14;
 id |  name   | year_founded | province_id 
----+---------+--------------+-------------
  8 | Toronto |         1793 |          14
 11 | Ottawa  |         1826 |          14
(2 rows)

3. Who wrote the article called 'Coding Bootcamps and Emotional Labor'?

one_to_many_assignment=# SELECT author_id FROM articles WHERE title = 'Coding Bootcamps and Emotional Labor';
 author_id 
-----------
         4
(1 row)

one_to_many_assignment=# SELECT name FROM authors WHERE id = 4; 
       name        
-------------------
 Tilde Ann Thurium
(1 row)

4. Write a series of SQL queries to find out how many provinces are in Canada.
one_to_many_assignment=# SELECT * FROM countries WHERE name = 'Canada'
one_to_many_assignment-# ;
 id |  name  | year_founded | national_animal 
----+--------+--------------+-----------------
  1 | Canada |         1867 | beaver
(1 row)

one_to_many_assignment=# SELECT COUNT(id) FROM provinces WHERE country_id=1;
 count 
-------
    14
(1 row)

5. How many people live at 4740 McDermott Street?
one_to_many_assignment=# SELECT id FROM residences  WHERE address = '4740 McDermott Street';
 id 
----
  9
(1 row)

one_to_many_assignment=# SELECT * FROM persons WHERE residence_id = 9;
 id |     name     | age | residence_id 
----+--------------+-----+--------------
 16 | Malvina King |  28 |            9
 17 | Theo Wolff   |  27 |            9
(2 rows)

6. What city is 4740 McDermott Street in?
one_to_many_assignment=# SELECT * FROM residences WHERE address='4740 McDermott Street';
 id |        address        | year_built | city_id 
----+-----------------------+------------+---------
  9 | 4740 McDermott Street |       1923 |      11
(1 row)

one_to_many_assignment=# SELECT name FROM cities WHERE id = 11;
  name  
--------
 Ottawa
(1 row)

7. What province is 4740 McDermott Street in?
one_to_many_assignment=# SELECT province_id FROM cities WHERE id = 11;
 province_id 
-------------
          14
(1 row)

one_to_many_assignment=# SELECT name FROM provinces WHERE id = 14;
  name   
---------
 Ontario
(1 row)

8. What country is 4740 McDermott Street in?

one_to_many_assignment=# SELECT name FROM countries WHERE id = 1;
  name  
--------
 Canada
(1 row)

9. Find the person named 'Destini Davis' 
and then use a series of SQL queries to find what country they live in.
one_to_many_assignment=# SELECT * FROM persons WHERE name = 'Destini Davis';
 id |     name      | age | residence_id 
----+---------------+-----+--------------
  3 | Destini Davis |  37 |            2
(1 row)

SELECT * FROM residences WHERE id = 2;
 id |      address      | year_built | city_id 
----+-------------------+------------+---------
  2 | 537 Wyman Harbors |       1975 |       8
(1 row)

SELECT *  FROM cities WHERE id = 8;
 id |  name   | year_founded | province_id 
----+---------+--------------+-------------
  8 | Toronto |         1793 |          14
(1 row)

one_to_many_assignment=# SELECT * FROM provinces WHERE id=14;
 id |  name   | year_founded | country_id 
----+---------+--------------+------------
 14 | Ontario |         1867 |          1
(1 row)

one_to_many_assignment=# SELECT * FROM countries WHERE id = 1;
 id |  name  | year_founded | national_animal 
----+--------+--------------+-----------------
  1 | Canada |         1867 | beaver
(1 row)


How many articles has Aditya Mukerjee written?
 SELECT id FROM authors WHERE name = 'Aditya Mukerjee';
 id 
----
  2
(1 row)

SELECT title FROM articles WHERE author_id = 2;
                          title                          
---------------------------------------------------------
 I Can Text You A Pile of Poo, But I Can’t Write My Name
(1 row)
