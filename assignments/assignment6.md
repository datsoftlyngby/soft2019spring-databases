# Assignment 06

## Excercise 1

In the `classicmodels` database, write a query that picks out those customers who are in the same city as office of their sales representative.

### Hand-in:
Insert into the readme file: the query and the graphical execution plan which can be obtained from the query. Explain what is the main performance problem for this query. Do not try to optimize the database for this query (yet).

### Review:
* Are you able to use the query?
* Do you have the same explanation?
* If you find the explanation good or bad - say so, and be constructive.

## Exercise 2
Change the database schema so that the query from exercise get better performance. 

### Hand-in:
Explain in the readme file what changes you did, if you changed the query or the schema. Insert a new graphical execution plan, and point out in the readme file why this new one is better.

### Review:
* Are you able to reproduce the speedup?
* Do you agree with the explanation?
* If you find the explanation good or bad - say so, and be constructive.

## Exercise 3
We want to find out how much each office has sold and the max single payment for each office. Write two queries which give this information

a) using grouping<br>
b) using windowing

For each of the two solutions, check its graphical execution plan.

### Hand-in:
The two queries and the graphical execution plans. Explain any differences and try to explain why there is or is not any difference.

### Review:
* Are you able to reproduce the difference?
* Do you agree with the explanation?
* If you find the explanation good or bad - say so, and be constructive.

## Exercise 4
In the stackexchange forum for coffee (coffee.stackexchange.com), write a query which return the displayName and title of all posts which with the word `grounds`in the title.

> If you want to challenge yourself a bit, use the ubuntu stackexchange instead, and search for `grep` rather than `grounds` in this and exercise 5.

### Hand-in:
* Hand in the query. Show the execution plan for the query (if you cannot get the graphical, show the tabular).
* Document that there is no real cost to the join to get the display name instead of just the userid. You can do that by running an other query with no join and then show that there is no major difference.

### Review:
* Are you able to verify there is no major difference?
* Do you agree with the explanation?
* If you find the explanation good or bad - say so, and be constructive.

## Exercise 5
Add a full text index to the `posts` table and change the query from exercise 4 so it no longer scans the entire `posts` table. 

### Hand-in:
* the revised query
* the sql needed to add your index
	* in particular your choice between a "natural language" full-text search and a "boolean" full-text search.
* documentation of efficiency in the form of an execution plan

### Review:
* Are you able to reproduce the difference?
* Do you belive this is the optimal query?
* If you belive you have a better solution, say so - and be constructive.
