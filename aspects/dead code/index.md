# Dead Code

While programming you might stumble upon some unforeseen bugs and tricky edgecases, that could very well have you rethink your design and/or approach along the way. Chances are you'll end up writing code that served a purpose once, but is no longer used or needed in your final design. We call this dead code. Dead code obfuscates the actual implementation and distracts the reader. Do try to remove anything that isn't directly used in your final design.

That could be blocks of commented code, that you kept around:

    // if (x > 7)
    // {
    //     printf("hello!");
    // }

Or maybe it's a condition that's never met:

    int x = 10;
    if (x < 10)
    {
        printf("bye!");
    }

Perhaps a function that you defined, but never called:

    void why_dont_you_call_me_anymore()
    {
        printf("hello?");
    }

Or that one library that you once needed:

    #include <ctype.h>
