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

- When running the code I can make an order however when continuing there were various errors that needed to be resolved. Looking at the lines I needed to *trace backwards* to look line by line if I can spot the first error.
    - On line #78 I see there is a toppings relation with Pizzatoppings inside the pizza class however the route wasn't relating to the topping class. topping_type needs to take the value for the topping str to correctly ensure the instances of the PizzaTopping.
- Here I decided to continue to *trace backward* since I knew the class instances needed to be all settled before continuing from here on. After further comtemplation I believed the error had to be in the routes and there's where I found the problem.
    - order_name request form get needed to have 'order_name' instead of just name.
    - `pizza_size_str` needed to have `pizza_size` instead of `pizza` alone.
    - `toppins_list` need to have method to get all the list so method .getlist() is needed.
- From here on I got an error `werkzeug.routing.exceptions.BuildError: Could not build url for endpoint '/'. Did you mean 'static' instead?`
    - Here I recognized `return redirect(url_for('/'))` was wrong and the `'/'` should of been `'home'` instead.
- Now since the backend is working I worked on the frontend and edited the jinja syntax.
    - On the home.html I needed to make sure the if, for loop and endloop is correctly on the correct line inorder to be executed. 
- Here I thought everything was supposed to be all settled but I kept on getting an error. Using Divide and conquer I kept on refering back to the errors and my code.
    I then realized I needed to connect the database session after the pizza was added despite it has been documented to the database successfully. After butting db.session.commit() the pizza is now being displayed.

## Exercise 2

[[Your answer goes here!]]

## Exercise 3

[[Your answer goes here!]]
