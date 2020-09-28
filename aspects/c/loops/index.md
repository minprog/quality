# Loops

Now that you have seen a number of algorithms using loops, this is the time wonder how to choose what kind of loop you might use for a given problem. The reason that this is a more complicated question than you might have thought is that all kinds of loops can be made equivalent. Consider these three loops, all of which count from 0 to 9:

    // version 1
    for(int i = 0; i < 10; i++)
    {
        printf("%d\n", i);
    }

    // version 2
    int i = 0;
    while(i < 10)
    {
        printf("%d\n", i);
        i++;
    }

    // version 3
    int i = 0;
    do
    {
        printf("%d\n", i);
        i++;
    }
    while (i < 10);

Choosing the right type at the right time will make your code easier to understand. Below are some guidelines for choosing loops. In general we suggest these guidelines but use your best judgement in any given situation.

## For

Prefer a `for`-loop to a `while`-loop when there is an obvious loop variable, or if you know in advance just how many times you want the loop to iterate. In the examples above, the `for`-loop is easiest to understand, because the starting point, ending point, and step are written next to each other on a single line. By the way, do not change the loop variable inside such a loop! Only then can one easily see how many times the `for`-loop iterates by just looking at its first line.

## While

Prefer a `while`-loop to a `for`-loop when there is no obvious loop variable. You might want to run a loop until some condition becomes false: perfect for a `while`-loop. The following example uses a **flag variable** to control an input loop. Because it relies on user input, we can't predict how often the loop will run before it should be terminated.

    bool running = true;
    while(running)
    {
        printf("Enter 999 to stop: ");
        int command = get_int();
        
        if(command == 999)
        {
            running = false;
        }
    }

> A `do-while`-loop is a bit harder to understand because the condition is on the last line of the loop. You can even terminate a loop right in the middle by using the `break` statement in the loop block. Because this makes it ever harder to determine the terminating condition, we recommend to avoid it.

## Learn more

Want to know more about writing loops? Have a look at this chapter:

- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 16, *Controlling loops*. Microsoft Press, 2004.
