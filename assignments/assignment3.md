# Assignment 3
Hand in on peergrade Sunday the 17th at 16:00. Reviews by Tuesday at 23:00.

**Worth** 10 studypoints

### Handin
A link to a github repository (or gist) with a README file with the two exercises below.

## 1. Twitter data
If you did not solve the twitter exercises, do it for this time. Your README.md file must contain the (aggregation) queries for the 5 exercises and the output of them. 

**Hint**: when you work with developing the queries you can use the small twitter set

If you solved the exercise already - please hand-in the queries and output - not the whole program and setup.

### Review criteria
For each af the 5 queries:

* Does it solve the problem, and if not, explain why
* If you were able to get the queries to work in your setup (using a different programming language), and if not, what was the problem.
* Any suggestion from your own solution you would like to point out for inspiration
* If there was something in this solution which you envy

## 2. Modeling
The mongo online manual has a [section on modeling] (https://docs.mongodb.com/manual/applications/data-models-tree-structures/). Consider three of the solutions:

  * Arrays of Ancestors, see https://docs.mongodb.com/manual/tutorial/model-tree-structures-with-ancestors-array/
  * Materialized paths, see https://docs.mongodb.com/manual/tutorial/model-tree-structures-with-materialized-paths/
  * Nested sets, https://docs.mongodb.com/manual/tutorial/model-tree-structures-with-nested-sets/

The mongo online manual also have a section on [Operational Factors and Data Models](https://docs.mongodb.com/manual/core/data-model-operations/) that mention a number of criteria to consider when modeling. 

For your analysis you need to consider only the first five factors:

* Atomicity
* Sharding
* Indexes
* Large Number of Collections
* Collection Contains Large Number of Small Documents

For each of the three models above, figure out which of the factors it the solution works well for, and where the model has problems.

The hand-in should in the readme file have a table like this:

Model | Atomicity | Sharding |Indexes |Large Number of Collections | Collection Contains Large Number of Small Documents
----|:----:|:----:|:----:|:----:|:----:
Arrays of Ancestors	|x| |x|x| |
Materialized paths  | |x ||x|x|
Nested sets			|x|x|x|| |

Your hand-in **must at least** consider the models and factors marked with "x", and for each of them give a brief argument for your conclusion.

### Review criteria
In your review, please consider the following aspects:

* Correctness of the conclusions. 
	* If you believe a specific conclusion is wrong, refer to your own argument (or paste it).
	* If you believe you were wrong, say thanks :-)
 
