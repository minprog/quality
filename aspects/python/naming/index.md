# Naming

Choosing good names for your variables is an art more than a science.
Please take your time to choose clear names for your variables that describe the idea behind it and that help programmers (including you) understand your code more easily.
While we can't give a general rule for finding good names, we can help you narrow your choices down by noting some constraints.


## Name length

It is often hard to find a short name that intuitively describes what a variable represents, but it is worth the effort.
Some oft-used short names that have a clear meaning are:

- `sum`
- `average`
- `age`
- `name`
- `total`

You should understand that the meanings of those words are not clear by themselves, but dependent on the **context**.
Each of the names in your code tell one part of the full story.
So when choosing the variable name `sum`, make sure that somewhere close it becomes clear what exactly is being summed (like the total number of tonic waters ordered in a restaurant).

Some names are a bit more specific than the examples above and contain words that differentiate them from other variables.
Here are some examples of variable names having two words:

- `current_user` (from a list of users)
- `starting_position` (within a string)
- `old_name` (as opposed to a changed name)

For variables, there is often a preference to use single-word names. Long names often don't help understanding because they themselves take longer to understand. But there are many options, so it's good to experiment.


## Consistency

Consistency is a part of choosing names, too.
This mostly concerns how one formats names.
There are several ways to write names, and we will follow the specification which asks to write all names in **lowercase**, and to separate different words in names using an **underscore** (`_`).
Above, you have seen several examples of variable names that are formatted consistently with this specification. Like before, this is just a convention, and writing names differently will not result in a compiler error. However, being consistent does allow one to more easily make sense of a given program.


## Constants

In Python, constants are usually declared and assigned in a module. Here, the module is a new file containing variables, functions, etc which is imported to the main file. Inside the module, constants are written in **all-caps** with underscores separating the words.

We have two files: **constant.py** and **main.py**

In **constant.py**

    PI = 3.14
    GRAVITY = 9.8

In **main.py**

    import constant

    print(constant.PI)
    print(constant.GRAVITY)

It might be tempting to just write the literal value in your code somewhere and not use a constant name. This is commonly called a **magic number**, because without diving deep into the code it would often be very hard to understand what that number means. That’s why we expect (almost) every magic number to be defined as a constant.

## Loops

Loops are a special case. Sometimes it's clear from a comment what the loop is supposed to do, but it's hard to think of a name for the **loop counter**. In that case, it is conventional to use the name `i`, then `j`, then `k`.

    for i in range(LIMIT):
        for j in range(LIMIT):
            for k in range(LIMIT):
                # do something

However, it is quite uncommon that no valid names can be found for the loop counters.
In all cases, make sure that from the combination of names and comments it is very clear what the purpose of the loop is and what the role of each variable is.
Also, if you need more than two or three nested loops, it might be time to rethink your approach.


## Python specifics

When assigning values to multiple variables at once, it's fine to declare them together, as in:

    a, b = 100, 100

You can also assign them different variables. Moreover, it is also possible to assign to different types:

    a, b, c = 0.1, 100, 'string'


## Learn more

Want to know more about choosing good names? Have a look at these chapters:

- Robert Martin, *Clean code: a handbook of agile software craftsmanship*. Chapter 2, *Meaningful names*. Pearson Education, 2009.
- Steve McConnell, *Code complete: a practical handbook of software construction*. Chapter 11, *The power of variable names*. Microsoft Press, 2004.
