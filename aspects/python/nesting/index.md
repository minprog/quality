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

## Learn more

Want to know more about writing simply structured code? Have a look at these chapters:

- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 17, *Unusual control structures*. Microsoft Press, 2004.
- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 19, *General control issues*. Microsoft Press, 2004.
- Ole-Johan Dahl, Edsger Dijkstra and Tony Hoare, *Structured programming*. Academic Press, 1972.
