# Magic numbers

The meaning of life may very well be [42](https://www.youtube.com/watch?v=aboZctrHfK8), but what was the question? You might find that there is such a magic number, like 67, that just makes your code work. When writing code you'll probably know why, maybe because 67 just so happens to translate to the letter `C` in the ASCII table? But shortly after you will undoubtedly forget. Needless to say, throwing magic numbers around in your code will absolutely confuse your peers. That's why you should document these numbers in comments, and whenever possible give them a clear and descriptive name. For instance, change:

    if (strlen(name) < 20)
    {
        // do something
    }

to

    // 20 is the maximum number of chars length that the database supports
    if (strlen(name) < 20)
    {
        // do something
    }

Alternatively, and perhaps better in case we find our magic number `20` scattered throughout our code, is to use a constant variable like so:

    const int MAX_NAME_LENGTH = 20;

    if (strlen(name) < MAX_NAME_LENGTH)
    {
        // do something
    }

Here we introduced a constant (denoted by the `const` modifier) variable called `MAX_NAME_LENGTH`. The `const` modifier makes it so that you cannot change the value of the variable, it's constant after all! By convention, especially in C, you'll typically find `ALL_CAPS_NAMES` for constant variables. Besides making your code easier to understand, this approach also makes your code easier to change. Because now if we'd ever want to increase the maximum number of characters for a name, all we'd need to do is change the value of `MAX_NAME_LENGTH`. That's just one line of code. In the other scenario, without the constant variable, we would have to change every single line of code containing the number 20. What would happen if you miss one?

![embed](https://www.youtube.com/embed/vK_naJkrtjc?rel=0)
