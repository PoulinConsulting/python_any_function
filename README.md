# The `any(iterable)` function
This function returns True if at least one of the iterable's values is True. It is equivalent to
```
def any(iterable):
    for element in iterable:
        if element:
            return True
    return False
```

## ***When to use***
* when you need to search for a True value, and you don't know the number of values ahead of time

## ***Examples***
### Who owes me money?
Imagine I own a business and I want to know which customers owe me money.

### Algorithm
1. iterate over all customers
2. iterate over invoices for each customer
3. check each invoice for a balance due

### Implementation

Assume I have these classes and methods
```
class Customer:
    def invoices(self):
        ''' get all a customer's invoices '''

class Invoice:
    def balance_due(self):
        ''' get the unpaid balance '''
```
I can code
```
customers_owing_money = [
    customer 
    for customer in customers
    if any(
        invoice.balance_due() > 0 
        for invoice in customer.invoices()
    )
]

```

I now have a list of customers with unpaid balances.


However, couldn't I write this instead?
```
customers_owing_money = [
    customer 
    for customer in customers
        for invoice in customer.invoices()
            if invoice.balance_due() > 0
]
```
No, because this might produce duplicate customers in the final output. I must consider the customer's invoices as a group, not individually.

## Additional information
See [Stack Overflow: How exactly does the python any() function work?
](https://stackoverflow.com/questions/16505456/how-exactly-does-the-python-any-function-work)
