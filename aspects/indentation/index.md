# Indentation

## Indentation

Indent your code four spaces at a time to make clear which blocks of code are
inside of others. If you use your keyboard's Tab key to do so, be sure that
your text editor's configured to convert tabs (`\t`) to four spaces, else
your code may not print or display properly on someone else's computer, since
`\t` renders differently in different editors. Here's some nicely indented
code:

    // print arguments
    printf("\n");
    for (int i = 0; i < argc; i++)
    {
        for (int j = 0, n = strlen(argv[i]); j < n; j++)
        {
           printf("%c\n", argv[i][j]);
        }
        printf("\n");
    }

Do note that you can check that your code is indented correctly through a tool called `style50`. You'll find instructions on how to use `style50` alongside the problem specifications.
