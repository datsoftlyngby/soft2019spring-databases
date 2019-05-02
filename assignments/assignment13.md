# Assignment 13 Database comparison

For this exercise you are going to set up an MySQL and a Neo4j database. You will initialize the databases with data of an artificial social network. That network consists of persons, i.e., users of a platform such as LinkedIn, and endorsements, i.e., the acknowledgment of another person. 

The data is given to you in CSV files. You can see small examples here, where one CSV file contains the data for the graph nodes and the other CSV file contains the data for the edges:

  * https://github.com/datsoftlyngby/soft2019spring-databases/blob/master/data/social_network_nodes_small.csv
  * https://github.com/datsoftlyngby/soft2019spring-databases/blob/master/data/social_network_edges_small.csv

**OBS:** The two files above are only small examples to understand how the data is structured. For your exercise you will use the **complete** dataset containing 500.000 nodes and some millions of edges:

https://github.com/datsoftlyngby/soft2019spring-databases/raw/master/data/archive_graph.tar.gz.

## Task

The purpose of this exercise is, that you execute a small experiment in which you compare runtimes of various queries on the two databases and report the measured results as well as a possible explanation and conclusions for the observations.


Precisely, your task is:

  1. Setup an SQL and a Neo4j database respectively.
  2. Import the data from the social network (endorsement graph https://github.com/datsoftlyngby/soft2018spring-databases-teaching-material/raw/master/data/archive_graph.tar.gz) into a Neo4j database and into an SQL database respectively.
  3. Construct queries in SQL and in Cypher, which find

     1. all persons that a person endorses, i.e., endorsements of depth one.
     2. all persons that are endorsed by endorsed persons of a person, i.e., endorsements of depth two.
     3. endorsements of depth three.
     4. endorsements of depth four.
     5. endorsements of depth five.

  4. Write a program in a programming language of your choice, such as Java, C\#, etc., where the program executes the above queries for **twenty** random nodes against the two respective databases. That is, you run each query on the same twenty random nodes.
  5. Extend your program, so that it measures the average and median execution times of each query. That is, you run a benchmark for the two databases.
  6. You collect your measurement results and present them with an evaluation of your experiment in a Markdown file in a repository on Github. That is, you hand in this assignment via Github.
    * Describe the setup of your experiment. That is, what does someone has to do/install/setup to reproduce your experiment?
    * Present the execution time of each query each of the 20 random nodes/persons per database.
    * Present the average and the median runtime of each of the queries per database.
    * Give an explanation of the differences in your time measurements. 
    * Conclude which database is better suited for this kind of queries and explain why.
  7. Push your solution, source, code, and presentation of the results to a Github repository *and* hand-in a link to that repository on peergrade.
  

## Hints:

You likely want to give Neo4j access to more memory. 

  **OBS** The Neo4j standard configuration is low on RAM. To receive meaningful results that do not measure RAM swapping times you have to increase RAM in the Neo4j configuration.

  Follow the _Memory Configuration guidelines_ on https://neo4j.com/developer/guide-performance-tuning/
and the _Memory configuration_ on https://neo4j.com/docs/operations-manual/current/performance/memory-configuration/#heap-sizing

    
### Docker env variables
You can set the configuration variables 

* `dbms.memory.heap.initial_size`, 
* `dbms.memory.heap.max_size`, and 
* `dbms.memory.pagecache.size`) 
	
via the following environment variables when starting the container 

* `--env=NEO4J_dbms_memory_pagecache_size=xG`, 
* `--env=NEO4J_dbms_memory_heap_initial__size=xG`, 
* `--env=NEO4J_dbms_memory_heap_max__size=xG`,
	
where `x` is an integer indicating gigabytes.

Present your measurement results in an understandable way. For example in a table similar to the following:
  
```
                     MySQL              Neo4j       
                average   median   average  median
Depth one:         0.5       0.4      2.1     1.4
Depth two:         1.8      17.0      2.5     2.1
Depth three:      57.5      17.0     11.5     7.3
Depth four:     1716.1     517.9    208.9    80.5
Depth five:   204874.4   70712.5   4647.8  1549.0
```


## References

This exercise is inspired and similar to chapter 1 "A case for a Neo4J database" of the book "Neo4J in Action" https://www.manning.com/books/neo4j-in-action). It is recommended that you read the first chapter. It is accessible online as PDF: https://manning-content.s3.amazonaws.com/download/5/392c9aa-4c64-4c6d-a072-fcf6b73d4ef1/Neo4jinAction_CH01.pdf

