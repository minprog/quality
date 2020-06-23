# Nesting

Using indentation, you make sure that the structure of your code is clear to a human reader. When *nesting* control flow structures, the indentation may eventually add up. This nesting can often (but not always) be avoided.

## Nesting conditionals

For example, in the following fragment, the comparisons are deeply nested. Note that it becomes less easy to determine which `else` block belongs to which `if` statement.

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

If you study the above example well, you may see that the discounts are provided for an increasing series of quantities. This means that the code can be written in a much nicer way:

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

## Large blocks of code in a condition

You might be tempted to check some negative condition, and if not satisfied, run the rest of your program:

    if (length < 0)
    {
        printf("Please enter a positive integer.");
        return 0;
    }
    else
    {
        // perform your algorithm on the variable 'length'
        length = length * 10;
        printf("%i\n", length);
    }

In this case, you should notice that you can *remove* the `else` block altogether, placing the algorithm below the `if` block, like below.

    if (length <= 0)
    {
        printf("Please enter a positive integer.");
        return 0;
    }

    // perform your algorithm on the variable `length`
    length = length * 10;
    printf("%i\n", length);

The reason here is that we use `return`. If the condition is met, we stop the program. So it is **impossible**, even without the `else` that the algorithm is executed with an invalid input. Rule of thumb: `return` early!
