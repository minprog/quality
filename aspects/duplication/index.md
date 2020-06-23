# Duplication

Duplicate code can make your code harder to understand and harder to change. You'll often find that you need similar logic in multiple places. With just two keyboard shortcuts (ctrl+c, ctrl+v) you'll be able to take that code you wrote earlier and give it another home. And that's tempting right? But now there's twice as much code and that means doubling your odds on pesky bugs. Imagine fixing a bug in a piece of code, only to later find out that this piece of code is duplicated throughout your project?

Enough horror stories, there are techniques to reduce code duplication. You could look into introducing your own function, and then call that whenever you need its functionality. Perhaps that's too much, and you can fix your duplication by introducing a loop, or maybe an extra variable. You'll find that different problems require different solutions and this is where we ask you to use your best judgement.

Is duplication all bad? No, not necessarily. Occasionally you'll find that reducing duplication makes your code significantly more complex or harder to understand. In that case you might opt to live with a little duplication. Ultimately it's all about balancing trade-offs.
