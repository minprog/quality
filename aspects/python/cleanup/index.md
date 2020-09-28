# Cleanup

While programming you might (and you will!) stumble upon some unforeseen bugs and tricky edge cases.
In such situations, you will have to rethink your design or approach.
Chances are that you end up having some code that served a purpose once, but is no longer used or needed in your final design.
We call this "dead code".
Dead code obfuscates the final implementation of your programs and distracts the reader.
Hence, it's good practice to remove anything that isn't directly used in your final design.
Below you'll find some forms of dead code that can be cleaned up.

The first example you have seen before; it's commented-out code:

    # x = 8
    # if x > 7:
    #     print("hello!")

A bit more tricky is the condition that is never met, resulting in lines of code that will **never** be reached:

    x = 10
    if x < 10:
        print("bye!")

Or perhaps there is a function that you defined, but do not actually use:

    def why_dont_you_call_me_anymore():
        print("hello?")

Finally, atop your files you may have imported some module that you once needed, but don't anymore:

    import math

For all of these examples, the solution is clear: delete the lines!

## Learn more

Want to know more about keeping your code tidy? Have a look at this chapter (which is a combination of basic and very advanced suggestions, so beware!):

- Robert Martin, *Clean code: a handbook of agile software craftsmanship*. Chapter 17, *Smells and heuristics*. Pearson Education, 2009.
