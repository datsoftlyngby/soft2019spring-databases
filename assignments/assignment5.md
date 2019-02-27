# Assignment 5

Our belowed site "stackoverflow" is part of a family of technical sites called "stackexchange.com". They run over 300 discussion fora similar to stackoverflow. The data of all those sites are awailable for download at the internet archive at: 
<https://archive.org/details/stackexchange>.

The programming stackexchange is about 40GB compressed XML - I guestimate around 100GB expanded.

We will use data from stackexchange for this assignment.

I suggest you use the two dataserts for "coffee.stackexchange.com" (small - for debugging purposes), and "askubuntu.com" which is around 700MB compressed - expands into 2GB XML. **You are free to choose which stackexchange site you want** - if you pick something else than "askubunto" you must mention so in the readme file of the handin.

The data is in several xml files, following a fixed naming scheme. There is a text file in the right side which explains briefly each field and table.

#### Loading the data
This is [a script that can *serve as the basis* loading the files into a database](https://gist.github.com/emanoelbarreiros/c164a60e98a7482cde22). 

### Exercise 1
Write a stored procedure `denormalizeComments(postID)` that moves all comments for a post (the parameter) into a json array on the post. 

### Exercise 2
Create a trigger such that new adding new comments to a post triggers an insertion of that comment in the json array from exercise 1.

### Exercise 3
Rather than using a trigger, create a stored procedure to add a comment to a post - adding it both to the comment table and the json array

### Exercise 4
Make a materialized view that has json objects with questions and its answeres, but no comments. Both the question and each of the answers must have the display name of the user, the text body, and the score.

### Exercise 5
Using the materialized view from exercise 4, create a stored procedure with one parameter `keyword`, which returns all posts where the keyword appears at least once, and where at least two comments mention the keyword as well.

## Hand-in
The hand-in must be handed in on peergrade. You are allowed to hand in in groups of 3. You review individually though.

The handin is a link to github. The readme file must explain where the textual representation of each of the solutions to the five handins are - it is easiest for the reviewer if they are inlined in the readme file.

## Review
For each of the five exercises, please consider the following elements:

* Are you able to find the solution in the submission?
* Are the descriptions in the readme file sufficient for you to replicate the solutions?
* Are the solutions clear and easy to understand, or do you find the solution to be too complex?
* If you think the solution was very clear and easy to work with, tell so.
* If you think you had a better solution, point it out (perhaps a link to yours, or inline yours).
