# Comments

There are multiple reasons that comments make code easier to understand.
One is that time may pass before you look at your code again: hours, days, weeks, months, or even years.
If you then decide you want to reuse some parts of it, or get it going again, you will need a little bit of help understanding.
The code itself is great at telling you every tiny bit of detail, because that is exactly what a programming language has you do.
But that makes code quite verbose and harder to make sense of.
Some annotations, written in a natural language, can carry an amazing amount of information in just a few words, while not needing to hang onto details.
Playing up to the strength of both tools at your disposal, we ask you to write comments next to your code, such that these comments aid you and your fellow programmers in understanding the code better and faster than without.

## Annotations

Here's our advice: add comments to your code that make programmers (including you) understand your code more easily.
Use short annotations to **describe** what a part of your code does at a high level.
And use **clarifying** comments when a part of your code is so complicated, that you need to explain the details of how something is done.
But do not use comments to describe what should already be clear from your code: some lines may not need a comment at all!
On the other hand, if you do feel the need to write multiple sentences of comments for one line of code,
consider splitting up that line instead, or try rethinking your algorithm.

Consistency also plays a part in formatting your comments.
First of all, you should choose the language in which to write them.
It doesn't have to be the same language as your variable names,
but the comments in your programs should all be written in the same natural language.

You do not need to write full sentences including capitals and punctuation,
but you should leave one space between the `#` and your comment's first character, just like this:

    # compute one student's average
    average = sum / QUIZZES + 0.5

In other words, don't do this:

    #compute one student's average
    average = sum / QUIZZES + 0.5

Or this:

    # Compute one student's average.
    average = sum / QUIZZES + 0.5

And as a general rule, you should not place comments on the same line as actual code:

    average = sum / QUIZZES + 0.5  # compute one student's average

## Summaries

Atop your `.py` file you should have multi-line comments
that summarize what your program (or that particular file) does
along with, perhaps, your name and that of the file. There are two ways of doing this.
The first way is just simply commenting every line with a hash (#): 

    # hello.py
    #
    # Computer Science 50
    # David J. Malan
    # 
    # - Says hello to the world.
    # - Demonstrates use of printf.

Since Python will ignore string literals that are not assigned to a variable, 
you can also add a multiline string in your code by using triple-quotes, and place your comment inside it.
Note that using this method inside of functions can lead to errors!

    """
     hello.py
     
     Computer Science 50
     David J. Malan
     
     - Says hello to the world.
     - Demonstrates use of printf.
    """

Atop each of your functions (except, perhaps, main) should be multi-line comments
that summarize what your function does along with, perhaps, its signature.
Consider what David tends to do:

    def chorus(b):
        """
         Sings about a number, b, of bottles.
        """
    
        s1 = "bottles"
        s2 = "bottles"

        # use singular form if needed
        if b == 1:
            s1 = "bottle"
        if b == 2:
            s2 = "bottle"

    # sing verses
    print(f"{b} {s1} of beer on the wall,")
    print(f"{b} {s1} of beer,")
    print("Take one down, pass it around,")
    print(f"{b - 1} {s2} of beer on the wall.\n")

This example is also nice because it demonstrates splitting up a function's code into three separate parts. The second and third part get their own summarizing comment that explains, in plain English, what the code will do when run.

## Commenting out code

Apart from writing notes, you might be tempted to "keep" some old code in comments. For example, if you have written a few lines of code, but you can't use them yet, you might put comment marks around those lines (often, your editor has a shortcut for this). This is called **commented-out code**. When experimenting, this is a great system, because you can easily revert it. However, be sure to clean up your code from such comments. Your job is to design a nice solution to a problem, and when you design something, you have to make choices. So as soon as you feel you're done, you will need to remove any old parts that you don't need anymore.

## Learn more

Want to know more about writing good comments? Have a look at these chapters:

- Robert Martin, *Clean code: a handbook of agile software craftsmanship*. Chapter 4, *Comments*. Pearson Education, 2009.
- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 32, *Self-documenting code*. Microsoft Press, 2004.
