# Naming

Take your time to choose clear names for your variables that state intent and make programmers (including you) understand your code more easily. Be consistent with your naming style, that way you won't spend time thinking just how you spelled that one variable days ago. It is often hard to invent a short name that intuitively describes what a variable represents, but it is worth the effort. Many very long names don't help understanding, only use longer names for the more important or longer lasting variables.

If you're summing some values, for instance, call your variable `sum`. If your variable's name
warrants two words (e.g., `is_ready`), put an underscore between them, a
convention popular in C though less so in other languages. Don't start your
variable's name with an uppercase letter.

If declaring multiple variables of the same type at once, it's fine to
declare them together, as in:

	int quarters, dimes, nickels, pennies;

Just don't initialize some but not others, as in:

	int quarters, dimes = 0, nickels = 0 , pennies;

## Loops

Whenever you need temporary variables for iteration, use `i`, then `j`, then
`k`, unless more specific names would make your code more readable:

	for (int i = 0; i < LIMIT; i++)
	{
	    for (int j = 0; j < LIMIT; j++)
	    {
	        for (int k = 0; k < LIMIT; k++)
	        {
	            // do something
	        }
	    }
	}

If you need more than three variables for iteration, it might be time to
rethink your approach.
