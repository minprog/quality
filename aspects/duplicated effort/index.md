# Duplicated effort

Do something once, why do it again? Try to reuse results of a computation when feasible. For instance, there's no need to compute the length of a string over and over again if the length does not change:

    string text = "hello";
    for (int i = 0; i < strlen(text); i++)
    {
        printf("%c", toupper(text));
    }

Instead we can compute the length once, store it, and then reuse the result:

    string text = "hello";
    for (int i = 0, length = strlen(text); i < length; i++)
    {
        printf("%c", toupper(text));
    }
