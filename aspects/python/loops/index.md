# Loops

Now that you have seen a number of algorithms using loops, this is the time wonder how to choose what kind of loop you might use for a given problem. The reason that this is a more complicated question than you might have thought is that the different kinds of loops can be made equivalent. Consider these two loops, both couting from 0 to 9:

    # version 1
    for i in range(10):
        print(i)

    # version 2
    i = 0
    while i < 10:
        print(i)
        i += 1

Choosing the right type at the right time will make your code easier to understand. Below are some guidelines for choosing loops. In general we suggest these guidelines but use your best judgement in any given situation.

## For

Prefer a `for`-loop to a `while`-loop when there is an obvious loop variable, or if you know in advance just how many times you want the loop to iterate. In the examples above, the `for`-loop is easiest to understand, because there is specified exactly how many times the loop will run.

## While

Prefer a `while`-loop to a `for`-loop when there is no obvious loop variable. You might want to run a loop until some condition becomes false: perfect for a `while`-loop. The following example uses a **flag variable** to control an input loop. Because it relies on user input, we can't predict how often the loop will run before it should be terminated.

    running = True
    
    while running:
        command = input("Enter 999 to stop: ")
    
        if command == "999":
            running = False

## Learn more

Want to know more about writing loops? Have a look at this chapter:

- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 16, *Controlling loops*. Microsoft Press, 2004.
