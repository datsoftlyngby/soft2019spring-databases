# Gutenberg Project

The task for the semester project in the database course is to build a small application that allows to figure out which cities are mentioned in which English books from Project Gutenberg, given a city which books mentioned it, and given a location, which books mention citis in vicinity.


## Build an Application with Various Databases

In the class, we covered four database paradigms. Key-value stores, document-oriented, relational, and graph databases. You build your application with at least **two** databases from two different paradigms, for example, MySQL and Neo4j, MySQL and MongoDB, Neo4j and MongoDB, etc. Of course, you are free to use any other database system from the given database paradigms.

You must build the an application in such a way that the same front-end will work for both databases.

## Types of End-user Queries

In essence, your application will support the following basic end-user queries:

  1. Given a city name your application returns all book titles with corresponding authors that mention this city.
  2. Given a book title, your application plots all cities mentioned in this book onto a map.
  3. Given an author name your application lists all books written by that author and plots all cities mentioned in any of the books onto a map.
  4. Given a geolocation, your application lists all books mentioning a city in vicinity of the given geolocation.

Consequently, your databases store author names, book titles, names of cities, their geolocations and their occurences in texts, and any other information that you deem important.


## Measure Application Behavior

Subsequently, you define a set of end-user test queries with at least five queries per type, see section above. That is, in total your end-user query test set contains at least 20 queries.

Now, you meassure the reponsiveness of your application with respect to the end-user queries.


## Report Results

Your final report has to provide information on the following:

  1. Which databases are used.
  * How data is modeled in the database.
  * How data is modeled in your application.
  * How the data is imported.
  * Behavior of query test set. Including a discussion on how much of the query runtime is influenced by the DB and what is influenced by the application frontend.
  * Your recommendation, for which database to use in such a project for production.
 
**OBS** Remember to use the approprite diagram notations for documentation.

# Hand-in Procedure

  * Create a repository on Github, which includes everything, the  code of your project, all related artifacts, as well as the report.
  * Create a Markdown (.md) file called README.md in the root of your project.
    - That README.md describes what this project does, and contains the project report as specified above.
  * Hand-in a link to this repository on Moodle. Latest hand-in is on 30. May 07:00 (morning). After handin deadline it is considered cheating to change the *master branch* in the repository.


# Hints:

 * A description on how to automatically download these books is available here: https://github.com/datsoftlyngby/soft2018spring-databases-teaching-material/tree/master/book_download
 * Per book you need the author(s) and the title(s). To get them you have essentially two possibilities:
   - You parse this information out of each book's text file.
   - You parse this information out of the XML/RDF files from the offline catalogue, see https://www.gutenberg.org/wiki/Gutenberg:Feeds
 * Per book you need a list of cities it mentions. Of course you write a program solving this task, where you can choose one of many strategies for your implementation. Be aware that some generate more noise than others.
    - Apply the heuristics that says: In English potential cities in a text are capitalized words
    - Apply the above heuristiscs to find sentences potentially mentioning cities and subsequently apply natural language recognition (named entity recognition) on those sentences to find proper city names, see for example:  https://nlp.stanford.edu/software/CRF-NER.html
  * CSV files with many cities and their geolocations is avalable from www.geonames.org, see http://download.geonames.org/export/dump/. For your project, you use either http://download.geonames.org/export/dump/cities15000.zip or http://download.geonames.org/export/dump/cities5000.zip
    - You choose wheather you recognise ASCII names or unicode names from `cities*.txt` depending on a book's file type. That is, you use the city names in either column `name` or `asciiname`.
    - You can neglect the city names given in column `alternatenames`.
* Remember that this project forms the basis of your exam _"The exam starts with a ten minutes group presentation about the Gutenberg Books Project."
* The frontend of your application does not matter too much. That is, a CLI application is as good as a web-application.



notes
