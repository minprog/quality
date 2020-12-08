# Nesting

Using indentation, you make sure that the structure of your code is clear to a human reader. When *nesting* control flow structures, the indentation may eventually add up. This nesting can often, not always, be avoided. Earlier, we have pointed out that "deep" nesting with loops is something to try to avoid. Here, we take a look at avoiding nesting with conditionals.

## Conditionals

In the following fragment, comparisons are deeply nested. Note that it becomes pretty hard to determine which `else` block belongs to which `if` statement.

    if quantity > 10:
        if quantity > 100:
            if quantity > 1000:
                discount = 0.10
            else:
                discount = 0.05
        else:
            discount = 0.025
    else:
        discount = 0.0

If you study the above example well, you may figure out that higher discounts are associated with purchasing increasing quantities. This means that the code can be written in a much nicer way:

    if quantity > 1000:
        discount = 0.10
    elif quantity > 100:
        discount = 0.05
    elif (quantity > 10):
        discount = 0.025
    else:
        discount = 0

## Early exit

You might need to check some condition, and if not satisfied, run the rest of your program:

    import sys

    if length <= 0:
        print("Please enter a positive integer.")
        sys.exit()
    else:
        length = length * 10
        print(length)

In this case, notice that you can *remove* the `else` block altogether, placing the algorithm below the `if` block, like below.

    import sys 

    if length <= 0:
        print("Please enter a positive integer.")
        sys.exit()

    length = length * 10
    printf(length)

The reason here is that we use `sys.exit()`. If the condition is met, we stop the program. So it is **impossible**, even without the `else` that the algorithm is executed with an invalid input. Rule of thumb: `exit` early!

## Boolean expressions

Especially in object oriented programming, you may sometimes want to write some function which returns whether or not a certain condition is true:

    def letter_in_word(self, letter):
        if letter in self.word:
            return True
        else:
            return False
            
This function can be simplified quite a bit. Notice you can immeditately return the result of a boolean expression, without using `if`-statements at all:

    def letter_in_word(self, letter):
        return letter in self.word
        
## Conditional return

You may also need to write a function which, instead of a boolean, needs to return a certain text based on a condition:

    def too_many_items(self):
        result = ""
        
        if len(self.items) > 1000:
            result = "There are too many items!"
        else:
            result = "You're fine, there's room for more items!"
        
        return result
        
Within a larger block of code, this way of setting a string would be completely reasonable. However, a function can `return`, which can make our implementation a bit more compact:

    def too_many_items(self):
        if len(self.items) > 1000:
            return "There are too many items!"
        return "You're fine, there's plenty of room for more items!"
        
Also note that, similarly to above under 'early exit', you don't even need an `else` block. A `return` immediately terminates the function, so getting to the second `return` if there are fewer than 1000 items is already impossible.

If your text and condition are short enough, you can even use Python's equivalent of a ternary operator:

    def awesome_text(self):
        return "Awesome!" if self.awesome else "Not awesome :-("
        
In general, try to return as quickly as you can in a function. This will keep your code more compact and improves readability.

## Learn more

Want to know more about writing simply structured code? Have a look at these chapters:

- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 17, *Unusual control structures*. Microsoft Press, 2004.
- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 19, *General control issues*. Microsoft Press, 2004.
- Ole-Johan Dahl, Edsger Dijkstra and Tony Hoare, *Structured programming*. Academic Press, 1972.
