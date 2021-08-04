# Formatting

There are several rules of thumb that you can apply to make your code easier to read and understand.
Several of those rules concern the formatting of individual lines of code, or the formatting of several related lines of code.
Other rules concern details that, however small, occur very often in code.

One important idea that you will encounter is that of **consistency**: choosing a rule and applying it the same everywhere.
The reason that consistency pops up is that there are often several equally valid options to choose from when formatting your code.
Hence, choosing rules, agreeing upon those with others, and applying them consistently is a common practice in programming.

## Indentation

Indentation is putting one or more spaces before each line of code.
The number of spaces is dependent on the **structure** of the code itself.
By following the structure, indentation enhances your code **visually**, making it easier to recognize common patterns and to understand what the program is doing.
To achieve this, code **within** a pair of brackets is indented once.
We recommend that you indent code using four spaces at a time.
In Python it is quite easy to know *when* you should indent a line. After a
line that ends in a `:` (colon), all dependent lines should be indented.

    list_of_numbers = [2, 3, 5, 6]

    # print arguments
    for i in range(10):
        if i in list_of_numbers:
            print("Number " + i + " is in the list!")
        number_count += 1

It is important to distinguish between **spaces and tabs** in this case. A tab is a single character that is displayed as multiple spaces (in most editors).
Sometimes, your editor may even insert spaces instead of the tab character as you type it.
The reason to make a clear distinction is that each editor may interpret a tab as being a different number of spaces.
So when you save your code with tab characters in it, it may actually look different in another editor.
You should be aware of this, and especially avoid **mixing** tabs and spaces (why?).
To make it easier for yourself, we recommend that you check that your editor is set to indent using **four spaces**, even if you type a tab character.

> You can check that your code is indented correctly using `style50`.
> You can find instructions on using `style50` alongside the problem specifications.

## Spaces

Consistent use of spaces makes expressions and statements easier to read.
To get started, we ask that you use the following rules consistently:

- Use a space around every binary operator.

        -3 + 5 - 4 * -2 < 10

- Do not use a space between the name of a function and its opening `(`.

        print("foo")
        answer = str(42)

## Grouping

Using empty lines between blocks of code makes your program easier to read.
As before, this enhances the visual structure of your program so another person can more easily recognize the patterns and make sense of the algorithms.
As you write longer code, you will encounter many options for grouping parts of it.
For now, you should at least use blank lines to **separate** `for`, `while`, `if` and other statements that contain blocks of code.
On the other hand, you can omit the blank line to keep an `if` and its related `elif` and `else` statements together.

So don't do this:

    x = 5
    for i in range(4):
        x += 3
    if (x > 10):
        x /= 2

And don't do this:

    x = 5

    y = 7

    if x > 10:
        x /= 2

    else
        y *= 2

But do this, i.e. grouping related statements:

    x = 5
    y = 7

    for i in range(4):
        x += 3
        y *= 6

    if x > 10:
        x /= 2
    else:
        x *= 2

    if y == 7:
        y = 0

## Line length

Placing spaces around each operator and using good variable names may result in lines of code that have become pretty long. Generally speaking, we'd like to keep lines of code under 100 characters. It's pretty easy to split long comments into multiple lines, but for long expressions it's a bit harder. Consider this long expression:

    average_temperature = (sum_of_minima + sum_of_maxima) / num_measurements / 2

This is not extremely long but you can see where this is going. Now, how do you break up such an expression? The first way is to split it up after the assignment operator:

    average_temperature =
        (sum_of_minima + sum_of_maxima) / num_measurements / 2

For this expression it suffices. Note the additional indentation of the second line, which helps the reader to immediately identify the line as being a continuation.

Alternatively, you could do something like this:

    average_temperature = (sum_of_minima + sum_of_maxima) /
                              num_measurements / 2

In many cases it doesn't quite matter where you break the line, because Python can infer that the lines belong together. Do remember that you're doing this to make your code more readable! So try to find a way that focuses the code reader's eye and makes your code easy to read.

## Learn more

Want to know more about writing neatly formatted code? Have a look at these chapters:

- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 31, *Layout and style*. Microsoft Press, 2004.
- Robert Martin, *Clean code: a handbook of agile software craftsmanship*. Chapter 5, *Formatting*. Pearson Education, 2009.
