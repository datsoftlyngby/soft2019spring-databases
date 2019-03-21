# Assignment 08 Transactions and Replication

This exercise is a bit more technical in its setup than the others we have been using. It requires you to run a droplet with a mysql server. It has to be running during the review period as well, but can be taken down by next lecture.

##  Replicated MySQL
1. You have to set up a mysql database on a droplet in singapore.
2. You have to equip that server with
	*  the classicmodels database, and 
	*  a user with the right permissions to allow a slave to serve as a backup database
3. You have to set up a database somewhere in Europe (Frankfurt or Amsterdam) which is a replication slave of the Singapore database.
4. Make an insert in one of the tables in singapore, and see how long it takes for the tables in Europe to update.
5. Make a transaction of several updates on the Singapore database, and verify that no changes happens to the European database until after the commit of the transaction.

#### Ressources for this:

* [Digital ocean has a tutorial on this](https://www.digitalocean.com/community/tutorials/how-to-set-up-master-slave-replication-in-mysql). It is a old, so expect it to be rough in the edges.
* The info to do the right things are also in [section 17 of the MySQL reference manual](https://dev.mysql.com/doc/refman/8.0/en/replication.html).  

## Handin
You need to document enough of your server for your reviewer to be able to set-up a new slave of your server. You need to make a database user which allow your reviewer to be able to make an update to your master database to verify that the slave updates correctly.

* Put password in a special file for peergrade, so it is not on github.

## Review
* Verify that you are able to set up your own slave of the database you review. 
* Verify that you can update the master database and see the changes to your database.
