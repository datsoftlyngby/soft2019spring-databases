# Assignment 07

Consider this select statement from classic models:

```sql
select customerNumber,
       customerName,
       concat(contactFirstName,' ', contactLastName) as contactName,
       customers.phone as contactPhone,
       customers.city as custCity,
       customers.postalCode as custZip,
       customers.country as custCountry,
       concat(firstName,' ',lastName) as repName,
       employees.email as repEmail,
       offices.phone as repPhone,
       offices.postalCode as repZip,
       offices.city as repCity,
       concat(offices.addressLine1, '\n', offices.addressLine2) as repAddress,
       offices.country as repCountry
from employees 
inner join customers on employees.employeeNumber = customers.salesRepEmployeeNumber
inner join offices on employees.officeCode = offices.officeCode
```

Assume it to be materialized into a table `CustomerOverview`.

## Exercise 1
Mention which violation there are to:

* First normal form (if any)
* Second normal form (if any)
* Third normal form (if any)

### Handin
Handin must mention which aspect of the normal form is violated. If it is an issue with a functional dependency, the hand-in should mention which collumn is dependent on what other column, and why that is an issue.

## Exercise 2
Assume we did not include the customerNumber in the table. What could be a key, and do we get the same violations of the normal forms?

### Handin
The handin must mention which column(s) you suggest to use as key, and argue why they functionally determines the entire row. Also, mention if there are any new issues with normal forms.

## Exercise 3
Assume the same table as in exercise 2. 

1. Write a safe update statement that change the `repPhone` column from `oldNumber` (say 12345678) to `newNumber` (say 87654321).
2. Write an update of `repEmail` which do not update properly (do not update it everywhere it should)

### Handin
The two statements, and explanation (or extract from real data before and after) to demonstrate why they work as they do.

## Exercise 4
In this exercise we will assume we have materialized this query into a table `tblEx4Sydney`.

```sql
with my_cust as
   (select customerNumber,
       customerName,
       customers.country as custCountry,
       offices.city      as repCity
    from employees
       inner join customers on employees.employeeNumber = customers.salesRepEmployeeNumber
       inner join offices on employees.officeCode = offices.officeCode)
select *
from my_cust
where repCity = 'Sydney'
```

Assume we have an index on customerName, and assume a fan-out in the B+ tree of 4. 

**Draw** a representation of of the B+ tree with index and leaf nodes, as well as the actual table data. The drawing must be a combination of Figure 1.1 and 1.2 from [Anatomy of an SQL index](https://use-the-index-luke.com/sql/anatomy).

### Handin
* You need to draw the tree on paper - perhaps by printing the actual table data and then handdraw the indexes (both leafnodes and B-tree) on top of it.
You can take a (clear) photo of the drawing to include in the handin.
* Explain how the index is used to find "Handji Gifts& Co" - that is, the path through the tree to get to the right row.
