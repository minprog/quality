# Nesting

Using indentation, you make sure that the structure of your code is clear to a human reader. When *nesting* control flow structures, the indentation may eventually add up. This nesting can often, not always, be avoided. Earlier, we have pointed out that "deep" nesting with loops is something to try to avoid. Here, we take a look at avoiding nesting with conditionals.

## Conditionals

In the following fragment, comparisons are deeply nested. Note that it becomes pretty hard to determine which `else` block belongs to which `if` statement.

    if (quantity > 10)
    {
        if (quantity > 100)
        {
            if (quantity > 1000)
            {
                discount = 0.10;
            }
            else
            {
                discount = 0.05;
            }
        }
        else
        {
            discount = 0.025;
        }
    }
    else
    {
        discount = 0.0;
    }

(Example derived from the book "Code Complete" by Steve McConnell.)

If you study the above example well, you may figure out that higher discounts are associated with purchasing increasing quantities. This means that the code can be written in a much nicer way:

    if (quantity > 1000)
    {
        discount = 0.10;
    }
    else if (quantity > 100)
    {
        discount = 0.05;
    }
    else if (quantity > 10)
    {
        discount = 0.025;
    }
    else
    {
        discount = 0;
    }

To come up with such an improvement requires a deep understanding of the problem that the program solves, as well as some fluency with using control structures such as `if`-`else if`-`else`.

## Early exit

You might need to check some condition, and if not satisfied, run the rest of your program:

    if (length <= 0)
    {
        printf("Please enter a positive integer.");
        return 0;
    }
    else
    {
        length = length * 10;
        printf("%i\n", length);
    }

In this case, notice that you can *remove* the `else` block altogether, placing the algorithm below the `if` block, like below.

    if (length <= 0)
    {
        printf("Please enter a positive integer.");
        return 0;
    }

    length = length * 10;
    printf("%i\n", length);

The reason here is that we use `return`. If the condition is met, we stop the program. So it is **impossible**, even without the `else`, that the algorithm is executed with an invalid input. Rule of thumb: `return` early!

## Factoring out a function

A final way to remove nesting is to create a function that performs one part of the task at hand. However, try to simplify your code before doing that. It might not even be needed.

## Learn more

Want to know more about writing simply structured code? Have a look at these chapters:

- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 17, *Unusual control structures*. Microsoft Press, 2004.
- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 19, *General control issues*. Microsoft Press, 2004.
- Ole-Johan Dahl, Edsger Dijkstra and Tony Hoare, *Structured programming*. Academic Press, 1972.
