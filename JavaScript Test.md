# JavaScript Test



1. What are the final values of all variables `a`, `b`, `c` and `d` after the code below?

   ```javascript
   let a = 1, b = 1;
   
   let c = ++a; // ?
   let d = b++; // ?
   ```

   

2. What are results of these expressions?

   ```javascript
   1. "" + 1 + 0
   2. "" - 1 + 0
   3. true + false
   4. 6 / "3"
   5.  "2" * "3"
   6. 4 + 5 + "px"
   7. "$" + 4 + 5
   8. "4" - 2
   9. "4px" - 2
   10.  7 / 0
   11.  "  -9  " + 5
   12. "  -9  " - 5
   13. null+1
   14. undefined+1
   15. " \t \n" - 2
   ```

   

3. What will be the result for these expressions?

   ```javascript
   5 > 4
   "apple" > "pineapple"
   "2" > "12"
   undefined == null
   undefined === null
   null == "\n0\n"
   null === +"\n0\n"
   ```

   

4. Write a function which take two parameters visitor, password

   if the visitor is "Admin" then check the password if the visitor is an empty string alert "Canceled". if it’s another string – then show “I don’t know you”.

   The password is checked as follows:

   - If it equals “TheMaster”, then show “Welcome!”,

   - Another string – show “Wrong password”,

     

5. Write an `if` condition to check that `age` is between `14` and `90` inclusively.

   “Inclusively” means that `age` can reach the edges `14` or `90`.

6. Write the code which outputs prime numbers in the interval from 2 to n.

   For n = 10 the result will be 2,3,5,7.

   P.S. The code should work for any n, not be hard-tuned for any fixed value.

7. Write a function `sumTo(n)` that calculates the sum of numbers `1 + 2 + ... + n`.

8. Which value it will show “Pete” or “John”  and Why ?

   ```javascript
   function makeWorker() {
     let name = "Pete";
   
     return function() {
       alert(name);
     };
   }
   
   let name = "John";
   
   let work = makeWorker();
   
   work();
   ```

9. Write function sum that works like this sum(a)(b) = a+b.

   ```javascript
   sum(1)(2) = 3
   sum(5)(-1) = 4
   ```

10. What will be the result of this code?

    ```javascript
    let x = 1;
    
    function func() {
      console.log(x); // ?
    
      let x = 2;
    }
    
    func();
    ```

11. We have an object storing salaries of our team:

    ```javascript
    
    let salaries = {
      John: 100,
      Ann: 160,
      Pete: 130
    }
    ```

    Write the code to sum all salaries and store in the variable `sum`. Should be `390` in the example above.

    If `salaries` is empty, then the result must be `0`.

12. Here the function `makeUser` returns an object.

    What is the result of accessing its `ref`? Why?

    ```javascript
    
    function makeUser() {
      return {
        name: "John",
        ref: this
      };
    }
    
    let user = makeUser();
    
    alert( user.ref.name ); // What's the result?
    ```

13. Write a function `getWeekDay(date)` to show the weekday in short format: ‘MO’, ‘TU’, ‘WE’, ‘TH’, ‘FR’, ‘SA’, ‘SU’.

    For instance:

    ```javascript
    let date = new Date(2012, 0, 3);  // 3 Jan 2012
    alert( getWeekDay(date) );        // should output "TU"
    ```

14 . Write the function `sumInput()` that:

- Asks the user for values using `prompt` and stores the values in the array.
- Finishes asking when the user enters a non-numeric value, an empty string, or presses “Cancel”.
- Calculates and returns the sum of array items.

P.S. A zero `0` is a valid number, please don’t stop the input on zero.

15. Create a function `truncate(str, maxlength)` that checks the length of the `str` and, if it exceeds `maxlength` – replaces the end of `str` with the ellipsis character `"…"`, to make its length equal to `maxlength`.

    The result of the function should be the truncated (if needed) string.

    For instance:

    ```javascript
    
    truncate("What I'd like to tell on this topic is:", 20) = "What I'd like to te…"
    
    truncate("Hi everyone!", 20) = "Hi everyone!"
    ```

