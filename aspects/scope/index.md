# Scope

Try to restrict the scope, the lifespan, of a variable as much as possible. That way you let go of unused memory as fast as possible, but more importantly you do not clutter the namespace with unused variables. That makes it just a little easier to find names for new variables, without resorting to names like `new_count` and `user2`.

For instance, take this for-loop:

    int i;
    for (i = 0; i < 10; i++) {
        printf("hello");
    }

Here the variable `i` continues to exist beyond the body of the for-loop, even though it probably won't see any use. So do this instead of the above:

    for (int i = 0; i < 10; i++) {
        printf("hello");
    }


## Late declaration

Try to declare your variables as late as possible by moving your variables as close as possible to the code where it's actually used. Not only does this make your code easier to read, it also makes it much easier to spot which pieces of code are independent of each other.

So don't do this:

    void my_function()
    {
        int count = 0;
        // code
        // some more code
        count += 1;
    }

But do this:

    void my_function()
    {
        // code
        // some more code
        int count = 0;
        count += 1;
    }


## Global variables

Global variables, variables that are kept around for the entirety of your program, can make your code a nightmare to debug and understand. Especially so if the value in that global variable changes! Take this program:

    int answer = 42;

    void foo()
    {
        answer += 1;
    }

    void bar()
    {
        answer *= 2;
    }

    int main()
    {
        foo();
        bar();
        printf("%d\n", answer); // prints 86
    }

Now if we swap the two function calls...

int main()
{
    bar();
    foo();
    printf("%d\n", answer); // prints 85
}

We end up with a different output! Now this program is small and manageable, but do just imagine trying to trace this outcome in a couple 1000 lines of code and you can see why the use of global variables is generally frowned upon. So instead, lets remove the global variable and parameterize the functions:

    int foo(int answer)
    {
        return answer + 1;
    }

    int bar(int answer)
    {
        return answer * 2;
    }

    int main()
    {
        int answer = foo(42);
        answer = bar(answer);
        printf("%d\n", answer); // prints 86
    }

Globals, guilty until proven innocent. There are often better ways to restructure your program to avoid the use of global variables. But, nothing is ever binary in software design. You might need access to a bit of static data in nearly every part of your code. In that case, a global constant variable might just be what you're looking for. Or say that your entire program revolves around some global variable keeping state? Well, you could opt to pass that global as a parameter to every function you write, but does that truly make your code that much easier to understand over just having one global around?
