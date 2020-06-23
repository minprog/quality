# Whitespace

Consistent use of whitespace makes expressions and statements more readable. Now there is no golden standard on just how you format your code. It is important however to format your code consistently and to be able to adhere to a set of rules set by for instance your company or the team you work in. In this course we ask that you:

- Use a space around every binary operator:

    -3 + 5 - 4 * -2 < 10

- Add a space after keywords like `while`, `for` and `if`:

    while (count < 0)
    {
        if (count > 5)
        {
            printf("foo");
        }
    }

- Do not use a space between the name of a function and its opening `(`:

    printf("foo");
    int answer = atoi("42");


## Vertical spacing

Using empty lines between blocks of code makes your program easier to read. Keep blocks of `if` and `else` statements together, but place an empty line between blocks of code that do not belong together.

So don't do this:

    int x = 5;
    for (int i = 0; i < 4; i++)
    {
        x += 3;
    }
    if (x > 10)
    {
        x /= 2;
    }

And don't do this:

    int x = 5;

    int y = 7;

    if (x > 10)
    {
        x /= 2;

    }

    else
    {
        y *= 2;
    }

But do this, i.e. grouping related statements:

    int x = 5;
    int y = 7;

    for (int i = 0; i < 4; i++)
    {
        x += 3;
        y *= 6;
    }

    if (x > 10)
    {
        x /= 2;
    }
    else
    {
        x *= 2;
    }

    if (y == 7)
    {
        y = 0;
    }
