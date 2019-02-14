# Assignment 2 - Analysis of Twitter Data

Your task is to implement a small database application, which imports a dataset of Twitter tweets from the CSV file into database.

Your application has to be able to answer queries corresponding to the following questions:

  1. How many Twitter users are in the database?
  * Who are the most active Twitter users (top ten)?
  * Who are the 
	  * five most grumpy (most negative tweets) and 
	  * the most happy (most positive tweets)? 
  * Which Twitter users link the most to other Twitter users? (Provide the top ten.)
  * Who is are the most mentioned Twitter users? (Provide the top five.)
  
Your application can be written in the language of your choice. It must have a structured form of acceess, but it is not important if it is an API, a CLI UI, a GUI, or a Web-based UI.

You present your system's answers to the questions above in a Markdown file on your Github account. That is, you hand in this assignment via Github. Push your solution, source, code, and presentation of the results to a Github repository, and a link to your solution in the  hand-in area.


## Hints

You can download and uncompress a dataset of Twitter tweets from http://help.sentiment140.com/for-students/.


Connect to your Docker container running the MongoDB DBMS.

```bash
$ docker run --rm -v $(pwd)/data:/data/db --publish=27017:27017 --name dbms -d mongo
88385afac5fe88a5ba47cd60c084bc1855cae6089a7e7d95ba24f0ba6fea1404
$ docker exec -it dbms bash
```

On that container install `wget` and `unzip`. **Note**: everything from here on, is a generic description for how to work on a Linux with the `apt` package manager, such as Ubuntu, Debian, etc.

```bash
root@88385afac5fe:/$ apt-get update
root@88385afac5fe:/$ apt-get install -y wget, unzip
```

Continue with downloading the data

```bash
root@88385afac5fe:/$ wget http://cs.stanford.edu/people/alecmgo/trainingandtestdata.zip
```

In your VM the unzip package is not installed by default. 

Now you can uncompress the Twitter dataset to your current directory with:

```bash
root@88385afac5fe:/$ unzip trainingandtestdata.zip
```

After uncompression you will have a folder with two files. For your exercise you will use the bigger one training.1600000.processed.noemoticon.csv. However, both files are CSV files, which do not contain a header row. The documentation on http://help.sentiment140.com/for-students/ says that the columns contain the following.

  > The data is a CSV with emoticons removed. Data file format has 6 fields:
  > 0 - the polarity of the tweet (0 = negative, 2 = neutral, 4 = positive)
  > 1 - the id of the tweet (2087)
  > 2 - the date of the tweet (Sat May 16 23:58:44 UTC 2009)
  > 3 - the query (lyx). If there is no query, then this value is NO_QUERY.
  > 4 - the user that tweeted (robotickilldozr)
  > 5 - the text of the tweet (Lyx is cool)

To make use of the `--headerline` switch when importing the data with mongoimport, we add a headerline accordingly:

```bash
root@88385afac5fe:/# sed -i '1s;^;polarity,id,date,query,user,text\n;' training.1600000.processed.noemoticon.csv
```

That leads to that the fields of our documents are named according to the given headerfields.
After importing the dataset, the dates are represented as strings instead of proper date objects. You might want to convert them with the following code:

```javascript
db.tweets.find().forEach(function(doc){
    if (doc.date instanceof Date !== true) {
        doc.date = new Date(doc.date);
        db.tweets.save(doc);
    }
});
```

For some of the questions, you might want to have a look into MongoDB's aggregation framework and queries using regular expressions. For example, the following query finds all tweets mentioning another Twitter user.

```
db.tweets.aggregate(
    {$match:{text:/@\w+\/}},
    {$group:{_id:null,text:{$push:"$text"}}
})
```


## Hand-in procedure

  * Provide all code and documentation for this assignment in a repository on Github.
  * Create a Markdown (.md) file called README.md in the root of your project.
  * That README.md describes what this project does and how to make it work. That is, you reviewer has to be able to clone your project, build it -you have to define steps for how to do that and what dependencies are required-, and use it.
  * A presentation of your system's reply to the **five** queries above.
  * Hand-in a link to your repository on www.peergrade.io.
  * Hand-in at latest on 10. Feb. 16:00.
  
## Review procedure

  * Log onto www.peergrade.io with your school email addresss.
  * Finish your review on www.peergrade.io at latest on 12. Feb. 23:00
  * Make use of the review criteria in peergrade giving feedback.


