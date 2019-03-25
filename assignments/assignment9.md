# Assignment 09 Relational algebra

# Your turn / Assignment
Consider this query from the classic models:

```sql
select customers.customerName, offices.city as office_city
from customers, employees, offices
where 
	customers.salesRepEmployeeNumber = employees.employeeNumber and 
	employees.officeCode = offices.officeCode and
    customers.city = offices.city;
```

1. Rewrite it as an expression in relational algebra
2. Add row counts to the subexpressions
3. Rewrite to a better expression

#### Red only extra exercise
In the in-class exercises we saw a result of adding an index on city. Can you explain that as it is, or do you actually need a new operator of some kind. <br>
*Hint: you need a variation on the select operator.*

## Handin
A link to github with the answer to the exercise above. It is part of the exercise to be able to format the relational algebra expression correctly. (You are allowed to "cheat" and make a pdf file with the formulas using some non-latex tool).

## Review
* Verify that the 1) algebraic expression is correct. 
* Verify that the row-count of the subexpressions are as you expect them, and explain why you have a different number if you do (or say thanks for the other convincing you that you was mistaken).
* Verify at the rewritten expression is indeed better. If you have a better rewrite, say so, or explain why you have a better (or just the same).

#### Red exercise
Give constructive feedback regarding the difference between your solution and the one you review.


