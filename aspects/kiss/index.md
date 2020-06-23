# KISS

Keep It Simple, Stupid. Try not to overcomplicate things in your design, and where possible break your program apart in small simple units. Take this program:

    def plot_running_average(filename):
        # Read numbers
        numbers = []
        with open(filename) as f:
            for line in f:
                # If line is not empty
                if line:
                    # Convert line to an int and add
                    numbers.append(int(line))

        # Compute running average
        running_average = [numbers[0]]
        for i in range(1, len(numbers)):
            running_average.append((running_average[-1] * i + numbers[i]) / (i + 1))

        # Plot
        plt.ylabel("Running average")
        plt.title("A beautiful graph")
        plt.plot(running_average)


Got it? No, well me neither. There's a lot going on in this function and odds are there's a little bug hiding somewhere in the corner, something like an `IndexError` on an empty file perhaps? Point is, it's gotten so complex that it isn't very clear to what it's doing and supposed to do.

So how can we improve? There seem to be three distinct things happening in this program that all do something completely unrelated from each other. First there's a reading part, then something computing a running average, and finally a little bit of code that plots a graph. Lets start by breaking this big function into three smaller functions:


    def read_numbers(filename):
        numbers = []
        with open(filename) as f:
            for line in f:
                # If line is not empty
                if line:
                    # Convert line to an int and add
                    numbers.append(int(line))

        return numbers

    def running_average_of(numbers):
        running_average = [numbers[0]]
        for i in range(1, len(numbers)):
            running_average.append((running_average[-1] * i + numbers[i]) / (i + 1))
        return running_average

    def plot(numbers):
        plt.ylabel("Running average")
        plt.title("A beautiful graph")
        plt.plot(numbers)

    def plot_running_average(filename):
        numbers = read_numbers(filename)
        running_average = running_average_of(numbers)
        plot(running_average)

Okay so now the `plot` and `plot_running_average` functions are actually quite understandable. Just a couple lines of code that effectively explain and document themselves. But there be dragons, in the form of `read_numbers` and `running_average_of`.

Let's zoom in on `read_numbers` first. There's a lot going on here, we have deep nesting with complex structures. It's doing all sorts of tasks at once. Whereas conceptually `read_numbers` should not need to be this complicated. If you dive into it, all we have to do is, read from a file, do some error checking for blank lines perhaps, convert everything to an integer and then return. So lets start out with just that:

    def read_numbers(filename):
        # Read from file into a list
        # Filter all blank lines
        # Convert every item to int
        # Return list

Now lets start restructuring the code, we can read from a file like so:

    def read_numbers(filename):
        # Read from file into a list
        with open(filename) as f:
            numbers = [line for line in f]

        # Filter all blank lines
        # Convert every item to int
        # Return list

Optionally you could use just a for loop or the `.readlines()` method here. Now we just need to filter out all the blank lines, which is another excellent task for a list comprehension:

    def read_numbers(filename):
        # Read from file into a list
        with open(filename) as f:
            numbers = [line for line in f]

        # Filter all blank lines
        numbers = [number for number in numbers if number != ""]

        # Convert every item to int
        # Return list

All we need to do now is convert everything to an int. Hey, that's another task for a list comprehension:

    def read_numbers(filename):
        # Read from file into a list
        with open(filename) as f:
            numbers = [line for line in f]

        # Filter all blank lines
        numbers = [number for number in numbers if number != ""]

        # Convert every item to int
        numbers = [int(number) for number in numbers]

        # Return list
        return numbers

There we go, a simple straight forward function that you can read from top to bottom. Okay, you could argue that these do not need to be separate list comprehensions:

    def read_numbers(filename):
        with open(filename) as f:
            return [int(line) for line in f if line != ""]

This gives you less code, but it's a bit harder to read. A trade-off that's up to you to make.

One dragon to go, `running_average_of`. We had this function:

      def running_average_of(numbers):
          running_average = [numbers[0]]
          for i in range(1, len(numbers)):
              running_average.append((running_average[-1] * i  + numbers[i]) / (i + 1))
          return running_average

There's a lot of 0s, 1s and -1s all over the place and oh so many brackets. Let us rethink this approach. If unfamiliar a running average is the average taken in intervals in time, or in our case elements in a list. So for instance the running average of:

    [2, 4, 6]

is:

    [2 / 1, (2 + 4) / 2, (2 + 4 + 6) / 3] = [2, 3, 4]

If we dissect this task, all we're doing is summing the numbers before our current number (also called running sum or running total) and then dividing that by how many numbers we've summed. So there's two things, summing and dividing:

    def running_average_of(numbers):
        # Compute running total
        # Compute average
        # Return running_average

Computing the running total sounds like a clear defined separate task, so lets make it its own function:

    def running_total_of(numbers):
        running_total = []
        total = 0
        for number in numbers:
            total += number
            running_total.append(total)
        return running_total

Great, now we can just call that from `running_average_of`:

    def running_average_of(numbers):
        running_total = running_total_of(numbers)
        # Compute average
        # Return running_average

Now we just have to do some division:

    def running_average_of(numbers):
        running_total = running_total_of(numbers)

        # Compute average
        running_average = []
        for i in range(len(running_total)):
            n = i + 1
            running_average.append(running_total[i] / n)

        return running_average

That's it, another function that's easy to understand reading from top to bottom.

Let's just piece everything back together:

    def read_numbers(filename):
        with open(filename) as f:
            return [int(line) for line in f if line != ""]

    def running_total_of(numbers):
        running_total = []
        total = 0
        for number in numbers:
            total += number
            running_total.append(total)
        return running_total

    def running_average_of(numbers):
        running_total = running_total_of(numbers)

        # Compute average
        running_average = []
        for i in range(len(running_total)):
            n = i + 1
            running_average.append(running_total[i] / n)

        return running_average

    def plot(numbers):
        plt.ylabel("Running average")
        plt.title("A beautiful graph")
        plt.plot(numbers)

    def plot_running_average(filename):
        numbers = read_numbers(filename)
        running_average = running_average_of(numbers)
        plot(running_average)

The program has gotten larger, there's more lines of code, but every part does just one thing in a straightforward manner. That makes the code much easier to read, and bugs that much easier to spot. We kept it Simple, Stupid.
