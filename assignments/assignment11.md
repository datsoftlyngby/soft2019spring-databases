# Assignment 11 - Object Relational Mapping
This hand-in is a bit different as it is not so much database as it is general programming skills.

We will make a tiny little ORM of our own.

An ORM has can be viewed as either:

* A convenience layer to access tables from a database
* A storage layer for entity objects

Our focus will be the last. We will make several parts of an ORM, with the focus of getting the whole working together rather than streamlining any part in particular.

The exercises below will be used to implement the following aspects:

* A specification of entities. Based on this specification you generate both a database scema, and the classes of the entities.
* A very simple query language which is expressed in terms of entities, and translates into SQL.
* We will skip the part of the ORM which allow us to store data.



# Exercise 1
There are many ways to specify the relationship between entities and database tables. We will use a simple json like format:

```json
{"schemaName": "MicroShop",
  "entities": [
  	{"Customer": {
  		"name": "String",
  		"orders" :"*Order"}},
  	{"Order" :{
  		"date": "String",
  		"total": "Number",
  		"customer": "Customer",
  		"lines": "*OrderLine" }},
  	{"OrderLine" : {
  		"order": "Order",
  		"product": "Product",
  		"count": "Number",
  		"total": "Number" }},
  	{"Product" : {
  		"name": "String",
  		"price" :"Number"}}
  ]
}
```

Write a program which take a specification like this and write two files:

* A file which defines the necessary MySQL schema with tables. 
* A source file with class definitions (pick C#, Java, or Python).

You need to define how to translate 'String' and 'Number'. 

Besides these two types, the type can be one of the other entities. The '*' in front of some of the entity types means that there is a list of entities. For example a Customer has a list of Order.

# Handin
The code should be handed in. Also, the resulting sql and source file for the above specification should be in the handin.

## Exercise 2
No ORM without a query language. We will make a very simple one with the following syntax:

* `Customer` return a collection of all Customers
* `Customer.name` return a collection of all names of Customers
* `(Customer|name='Joe')` return a collection of all Customers named Joe.
* `(Customer|name='Joe').Orders` return a collection of all Joe's orders
* `(Customer|name='Joe').Orders.OrderLine.Product` return a collection of all products in all of Joe's orders
* `(Orders|total > 200).Customer.name` return a list of all Customers with an order above 200.

I suggest you get the queries to work in the order specified above. Getting the first two to work is necessary.

The condition in `(Customer|name='Joe')` can be really hard to do if you want to do it 100% right. I therefore suggest to merely assume that the part from `|` to the matching `)` is copied into a sql where clause directly.

Examples of how the query language could be used in Python could be:

```python
names = myQuery("Product.name")
for name in names:
	print(name)
```
or

```python
joesOrders = myQuery("(Customer|name='Joe').Orders")
for order in joesOrders:
	print( order.date )
```
