# Assignment 12, Neo4J

This assignment is about the analysis of twitter data from the British Islands. 

The data are orginally taken from: http://followthehashtag.com/datasets/170000-uk-geolocated-tweets-free-twitter-dataset/

This time getting the data into the right format is not part of the exercise, and the data is available at: https://github.com/datsoftlyngby/soft2019spring-databases/blob/master/data/some2016UKgeotweets.csv.zip

## Exercise 1
If you give your neo4j docker container this flag '-v $(pwd):/var/lib/neo4j/import', you should be able to load the data using this query:

```cypher
LOAD CSV WITH HEADERS FROM "file:///some2016UKgeotweets.csv" AS row 
    FIELDTERMINATOR ";"
return row
LIMIT 1
```

The exercises in this assignment will work with only some of the columns in the csv file:
"User Name", "Nickname","Place (as appears on Bio)", "Latitude", "Longitude" and "Tweet content"

Ofcause we do have to extract `mentions` from the data.

Unlike the other databases we have worked with, neo4J has a rather complete programming language. This example shows how to extract a list of mentions from a tweet text:

```cypher
with "Talking to some great journos this morning all about @Hirsty148!  🐑 😴 @Metropolitan by COMO,…" as tweetSample
return extract( m in 
                filter(m in split(tweetSample," ") where m starts with "@" and size(m) > 1) 
                | right(m,size(m)-1))
                as mentions
```

which returns a list of ['Hirsty148!', 'Metropolitan'].

Finally we can state the exercise

* Write a cypher command that loads the tweets, creates a number of objects labeled "Tweet" with the columns "User Name", "Nickname","Place (as appears on Bio)", "Latitude", "Longitude" and "Tweet content" renamed as something nice (single lowercase name), and which adds a list of mentions to each Tweet.

## Exercise 2
* Use the mentions list of each tweet to create a new set of nodes labeled "Tweeters", whith a "Mentions" relation.
* Create a relation "Tweeted" between Tweeters and Tweet.

## Exercise 3
* Find the top 10 list of tweeters whose tweets are the furtherst apart.

## Handins
Link to cypher queries and the results obtained from each query

