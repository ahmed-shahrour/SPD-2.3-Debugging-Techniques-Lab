# Debug Log

**Explain how you used the the techniques covered (Trace Forward, Trace Backward, Divide & Conquer) to uncover the bugs in each exercise. Be specific!**

In your explanations, you may want to answer:

- What is the expected vs. actual output?
- If there is a stack trace, what useful information does it contain?
- Which technique did you use, on which line numbers?
- What assumptions did you have about each line of code, and which ones were proven to be wrong?

_Example: I noticed that the program should show pizza orders once a new order is made, and that it wasn't showing any. So, I used the trace forward technique starting on line 13. I discovered the bug on line 27 was caused by a typo of 'pzza' instead of 'pizza'._

_Then I noticed another bug ..._

## Exercise 1

- When I submit the form for a New Order, the page throws a 
```
TypeError: 'topping' is an invalid keyword argument for PizzaTopping
```
Once I looked through the error stack, it says the source of the error is at line 79 in `app.py`.  The POST request is received via the backend server logs. So I think the error tail is when we submit a POST request for a New Order.

- The error leads us to the misuse of class `PizzaTopping`. There isn't an argument called `topping`. It should be `topping_type`. So I fixed that but another error pops up

- `pizza_size_str` variable is `None`. The HTML form input is also not matching so I renamed it

- The same issue occurrs for `order_name`.

- After all that, the db is committed appropriately so I fixed that too.

- Fixed the `PizzaTopping` array being created.

- then I fixed the `redirect(url_for('/'))` to `redirect(url_for('home'))`.
## Exercise 2

[[Your answer goes here!]]

## Exercise 3

[[Your answer goes here!]]
