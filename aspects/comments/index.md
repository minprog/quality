# Comments

Comments make code more readable, not only for others (e.g. your TA) but also for you, especially when hours, days, weeks, months, or years pass between writing and reading your own code. Code carries information too, but it is necessarily restricted by a programming language and that in turn to a machine. This means that code is great at telling you every bit of detail, because that is exactly what a programming language has you do. But, that makes code verbose and it is quite difficult to succinctly express intent in your code. Conversely a natural language, like English, can carry an amazing amount of information in just a few words, while not needing to hang on details. Playing to the strength of both tools at your disposal, we ask you to write comments next to your code, such that these comments aid you and your fellow programmers in understanding the code faster than without these comments.

## Comments in your code

Here's our advice: Add comments to your code that make programmers (including you) understand your code more easily. Use "documentation" comments to describe what a part of your code does at a high level. Use "clarification" comments when a part of your code is so complicated, that you need to explain the details of how something is done. Don't use comments to describe what is already clear from your code.

Within functions, use inline comments and keep them short (e.g., one line),
else it becomes difficult to distinguish comments from code, even with syntax
highlighting. No need to write in full sentences (including capitals and
punctuation), but do leave one space between the `//` and your comment's first
character, as in:

	// compute student's average
	average = (int) (sum / QUIZZES + 0.5);

In other words, don't do this:

	//compute student's average
	average = (int) (sum / QUIZZES + 0.5);

Or this:

	// Compute student's average.
	average = (int) (sum / QUIZZES + 0.5);

Do not place comments on the same line as actual code, as in

	average = (int) (sum / QUIZZES + 0.5); // compute student's average

## Comments atop your code

Atop your `.c` and `.h` files should be multi-line comments that summarize
what your program (or that particular file) does along with, perhaps, your
name and that of the file. Consider what I tend to do:

	/****************************************************************************
	 * hello.c
	 *
	 * Computer Science 50
	 * David J. Malan
	 *
	 * Says hello to the world.
	 *
	 * Demonstrates use of printf.
	 ***************************************************************************/

Atop each of your functions (except, perhaps, main) should be multi-line
comments that summarize what your function does along with, perhaps, its
signature. Consider what I tend to do:

	/**
	 * Sings about a number, b, of bottles.
	 */
	void chorus(int b)
	{
	    string s1 = "bottles";
	    string s2 = "bottles";

	    // use proper grammar
	    if (b == 1)
	    {
	      s1 = "bottle";
	    }

	    if (b == 2)
	    {
	      s2 = "bottle";
	    }

	    // sing verses
	    printf("%d %s of beer on the wall,\n", b, s1);
	    printf("%d %s of beer,\n", b, s1);
	    printf("Take one down, pass it around,\n");
	    printf("%d %s of beer on the wall.\n\n", b - 1, s2);
	}

## Code in comments

You might be tempted to "keep" some old code in comments. For example, if you have written a few lines of code, but you can't use them yet, you might put comment marks around those lines (often, your editor has a shortcut for this). This is called **dead code**. Be sure to clean up your code from such comments. Your job is to design a nice solution to a problem, and when you design something, you have to make choices. So as soon as you feel you're done, you will need to remove any old parts that you don't need anymore.
