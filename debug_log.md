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

- When we run the code it throws an internal server error. It traces to line 52 in `app.py`.
-  `KeyError: 'name'. result_json` returns an api error which could possibly be becasue of bad params which is `None`
- I fixed the argument type issues but I still get an API error.
- I changed `place` to `q` in the params.
- There's a typo in JSON key for `temperature`, it should be `temp`

## Exercise 3
- `merge_sort` seems to throw an `IndexError` for an out of range in line 37.
- After looking through the code I noticed that `i` and `j` should be replaced.
- Then another bug in `binary_search` function. The division is not rounded to the closest integer but left as a float. Fixed that too.

