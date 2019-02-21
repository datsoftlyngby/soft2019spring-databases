# Assignment 4
This week is about security in databases. As always with IT security we have three main areas to worry about:

* Preventing unauthorized access
* Discovering unauthorzed access
* Recovering from unauthorized access

The exercises will utilize the MySQL database - version 8. In the slides it is shown how to set it up using docker.

We will be using the "classic models" sample database.<br>
(http://www.mysqltutorial.org/mysql-sample-database.aspx)

An overview of the tables are in this figure:

<img src="images/ClassicModelsER.png" width="75%">

### Handin
You hand-in on peergrade Monday 25th at 06:00.  Your hand-in is a link to a github repository.


## Excercise 1 - user privileges
Lets assume are several systems which use this database:

* Inventory - which is used to maintain the two tables `products`and productlines`. 
* Bookkeeping which make sure that all orders are payed.
* Human resources which takes care of employees and their offices
* Sales - who creates the orders for the customers 
* IT - who maintains this database

Create a database user for each of the four roles, and be restrictive in what the each user can do in the database.

In the readme file, argue why the permissions are as they are.

#### Hand-in
Hand in for this is a sql script which creates and sets the permissions for the users. 

#### Review
Check that:

* You are able to run the sql script on your own database set-up.
* If you belive the permission choice in the readme file is not safe, explain what would have been a better choice.
* If you believe the user has the wrong permissions compared to what is in the readme file, try to exemplify with a sql statement which you are not allowed to run, but you think you should be able to run.

## Exercise 2 - logging
Make a number of operations on the database:

* Insert 2 new employees 
* Insert 1 new product
* Create 1 new order

**Non-mandatory extra**: Set up a mysql database on digital ocean with standard port (3306), and check the log some days later for log-in attempts.

#### Hand-in
Upload as part of the hand-in the database log which shows:

* The users and their privileges being added (the part of the log from exercise 1)
* The three changes to the database from above
* One attempt to make a change by a user with the wrong privileges

#### Review
Check that:

* The log contains the elements required


## Exercise 3 - backup and recovery
Create a backup file of the database after the changes in the two previous exercises.

#### Handin
Include the backup file in your git-repository.

As there are several ways of taking a backup of a database, you must explain in the readme file which technique you have used.

#### Review
Verify that you are able to install the backup based on the file on github.

