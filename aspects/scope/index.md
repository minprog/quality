# Scope

From earlier, you know that you can declare, initialize and assign variables at various points in your programs.
At some point in the development of programming languages, it was needed to at least declare all variables at the top of a file or function.
With current compilers, this is not needed at all.
Instead, it is now common to declare and initialize variables as **late** as possible.
For example, you have seen `for`-loops where the loop variable is declared inside the loop:

    for (int i = 0; i < 10; i++)
    {
        ...
    }

Doing it like that even helps you prevent programming errors.
For example, if we try to print the variable `i` after the loop terminates, we get an error *while compiling*.
This error helps us understand that our idea for a solution might not be quite correct, yet.

    printf("%d\n", i);   // use of undeclared identifier

Say we are using a loop to calculate a sum and we want to print that.
We then need to declare the variable **outside** the loop, lest we get the same error as above.
So, we decide that we *need* to access that variable later and we make an intentional decision about the scope of that variable.

    int sum = 0;
    for (int i = 0; i < 10; i++)
    {
        sum += array[i];
    }
    printf("%d\n", sum);

## Late declaration

The above is about `for`-loops but declaring late is something you should always consider. Not only does this make your code easier to read, it also makes it much easier to spot which pieces of code are **independent** of each other.

So don't do this:

    int main(void)
    {
        int count = 0;
        // code
        // ...
        // some more code
        count += 1;
    }

But do this:

    int main(void)
    {
        // code
        // some more code
        
        // count has nothing to do with the code above!
        int count = 0;
        count += 1;
    }


## Global variables

The ultimate early declaration is having a variable that is declared outside of any function, including `main`. Such variables are called **global**, in that they can be accessed from any function. Global variables are rarely needed. Sometimes, a set of functions can share a single global variable that contains the main data of the program, like in a game. In other cases, it might be better to avoid globals and pass some of the data to other functions as **parameters**.

## Learn more

Want to know more about declaring variables? Have a look at this chapter:

- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 10, *General issues in using variables*. Microsoft Press, 2004.
