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

- Similar to Exercise 1 after I ran the code and the server was running successfully. However after that I got a list of errors. Looking at the app.py I decided to *trace forward* because I wasn't sure which line was causing the error. Going over the first route I found an error in the `/results` route
    - The request arguments are getting `users_city` and `requested_units` but should of been just `city` and `units`.
- After that continuing to the paramas and seeing if it correct relates back to the result json file. There is where I had an ah ha moment
    - Even though the params are correct the result json needs to be called.
- Lastly I went to to the context dictonary and found that the temp value needs to have the same result. Therefore it can't be `temperature` but `temp`.
- Here I thought I was done but unfortunately I kept on getting `KeyError: 'name'` in results `'city': result_json['name']`
    - I then figured out the paramenter key value was `place`. I changed the `place` to `q` inorder to have the correct API place value. After that it began to show. Once I thought I noticed an html typo in the home.html page. I changed the end h1 to h2.
- Finally everything was working

## Exercise 3

- When running main.py I'm getting an IndexError: list idex out of range. Heading into the main.py file I see the majority of the code is in utils.py where I headed there.
- I used *trace backward* since I knew there would be a slight error in the merge_sort function. Seeing that the initial values were being declared proved to me that the code after that needed more indepth checking. The first error I found was in the while loop.
    - Since the while loop copies the data to the temporary left and right arrays, I noticed since the while loop is comparing if `i` is less than the length of the left side and the same goes to `j`, the temporary arrays of `i` and `j` need to  be less than inorder to not be off bounds.
    - Continuing down to see if any element was left, both while loops of `i` and `k` need to be increased by 1 inorder to check the array values of both left and right sides.
- On the last function I knew I still continued to use *trace backwards* since this was the last function I didn't check.
    - When the low and high variables were declared and eventaully seeing the mid has a value of 0, I knew it had to be removed.
    - Since we're searching for the binray search with the parameters of the arry and element, the while loop needs to be iterating when the low value is less than and equal to high because it needs to return the index. If it's not less than or equal to we would be looking for a different value. Lastly since we're getting the mid values we need to get the average floor division of the high and low in order to be specific as much as possible. Other than that I recieved no errors and didn't need to use *Divide and Conquer* to check for multiple errors.