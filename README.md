# Switch Statements

## Learning Goals

- Explain what a switch statement is.
- Discuss why a `break` statement should be included.

## What is a Switch Statement?

A **switch statement** is a multiway branch that is more efficient than nested
`if` statements in that it can have multiple execution paths. To help understand
more about what goes into a switch statement, let us look at the syntax:

```java
switch (expression) {
    // case statements
    // values must be the same data type as the expression
    case value1:
        // statement sequence
        break;    // breaks out of the case statement
        
    case value2:
        // statement sequence
        break;    // breaks out of the case statement

    // There can be multiple case statements
    // and the default case statement is executed if none of the above
    // cases are true
    default:
        // statement sequence
        // no break is needed in the default case
}
```

Duplicate cases are not allowed in switch statements.

The `break` statement, while optional, is highly recommended. It tells Java that
they have finished writing the code needed within the case and that it can get
out of the `switch`. When the code reaches a `break`, it will exit from the
`switch` and continue on with the next statement outside the `switch`. More on
what happens if we omit the `break` statement in a little bit.

`default` statements are also optional and usually appear at the end of the
`switch`. The `default` statement sequence is executed if no `case` matches. If
the `default` statement is omitted, then no action will take place.

The advantage of using a `switch` statement over a typical chained conditional
(if-else-if-else block) is the readability of a `switch` statement. Since
`switch` statements tend to be easier to read by a developer, they also can be
easier to maintain. Let's look at an example of a chained conditional that could
be transformed into a `switch`statement:

```java
char grade = 'B';
if (grade == 'A') {
    System.out.println("Wow! You got an A!");
} else if (grade == 'B') {
    System.out.println("Great job!");
} else if (grade == 'C') {
    System.out.println("Congrats! You passed!");
} else if (grade == 'D') {
    System.out.println("Whew! You just passed!");
} else if (grade == 'F') {
    System.out.println("Oops! Better luck next time!");
} else {
    System.out.println("Invalid letter grade");
}
```

Now let us use a `switch` instead of the if-else-if-else cascade:

```java
char grade = 'B';
switch (grade) {
    case 'A':
        System.out.println("Wow! You got an A!");
        break;
    case 'B':
        System.out.println("Great job!");
        break;
    case 'C':
        System.out.println("Congrats! You passed!");
        break;
    case 'D':
        System.out.println("Whew! You just passed!");
        break;
    case 'F':
        System.out.println("Oops! Better luck next time!");
        break;
    default:
        System.out.println("Invalid letter grade");
}
```

The switch statement tends to look cleaner and more readable than the
if-else-if-else block. It also can avoid repetitive code.

## Omitting the Break Statement

As we mentioned before, a `break` statement is optional, although it is good
practice to use them within `switch` statements. A forgotten `break` statement
is a very common cause of bugs. Let's consider the previous example, but this
time, omit the `break` statements:

```java
char grade = 'B';
switch (grade) {
    case 'A':
        System.out.println("Wow! You got an A!");
    case 'B':
        System.out.println("Great job!");
    case 'C':
        System.out.println("Congrats! You passed!");
    case 'D':
        System.out.println("Whew! You just passed!");
    case 'F':
        System.out.println("Oops! Better luck next time!");
    default:
        System.out.println("Invalid letter grade");
}
```

Let's look at this closer in the debugger by setting a breakpoint at the line
`switch (grade)`:

![switch-breakpoint](https://curriculum-content.s3.amazonaws.com/java-mod-1/switch-statement/intellij-debugger-switch-breakpoint.png)

Since we have hard-coded the `grade` variable to hold the character `B`, we
should see it enter the `case B` block. Let's step-over and find out!

![enter-case-b](https://curriculum-content.s3.amazonaws.com/java-mod-1/switch-statement/intellij-debugger-enter-case-b.png)

Sure enough, it does! When we step-over again we should see it print
"Great job!" to the console. But look at what else happens when we step-over:

![enter-case-c](https://curriculum-content.s3.amazonaws.com/java-mod-1/switch-statement/intellij-debugger-enter-case-c.png)

It looks like it didn't exit out of the `switch` statement! That is because if
the `break` statement is not present, then it will "fall through" and the code
will continue onto the next case until it sees a `break`. This means, it will
continue with the next case without any checks!

So, if we were to resume the program, the final output we would be:

```text
Great job!
Congrats! You passed!
Whew! You just passed!
Oops! Better luck next time!
Invalid letter grade
```

Now let's put the `break` statements back in and then step-over to see the line
of execution move to the `case B` block:

![enter-case-b](https://curriculum-content.s3.amazonaws.com/java-mod-1/switch-statements/intellij-debugger-case-b.png)

We're back to where we expect everything to be! Now step-over again, and we'll
hit the `break` statement:

![break-statement](https://curriculum-content.s3.amazonaws.com/java-mod-1/switch-statement/intellij-debugger-hit-break-statement.png)

When we step-over the `break` statement, we exit out of the `switch` and the
only message printed to the console was "Great job!".

![exit-switch](https://curriculum-content.s3.amazonaws.com/java-mod-1/switch-statement/intellij-debugger-exit-switch-statement.png)

This is the expected behavior that we were hoping to accomplish. As we can see,
the `break` statement definitely makes a difference!
