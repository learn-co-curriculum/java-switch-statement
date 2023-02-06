# Switch Statements

## Learning Goals

- Explain what a switch statement is.

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

The `break` statement is optional, although most programmers tend to use it to
show that they have finished writing the code needed within the case and that it
can get out of the `switch`. When the code reaches a `break`, it will exit from
the `switch` and continue on with the next statement outside the `switch`. If
the `break` is not present, then it will "fall through" and the code will
continue onto the next case until it sees a `break` statement.

`default` statements are also optional and usually appear at the end of the
`switch`. The `default` statement sequence is executed if no `case` matches. If
the `default` statement is omitted, then no action will take place.

The advantage of switch statements are that they tend to be more efficient than
a typical if-else-if-else block. Let's look at an example of an if-else-if-else
block that could benefit from being a switch statement:

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

We can walk through this `switch` using the browser based Java Visualizer below:

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=public%20class%20SwitchExample%20%7B%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20char%20grade%20%3D%20'B'%3B%0A%20%20%20%20%20%20%20%20switch%20%28grade%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20case%20'A'%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Wow!%20You%20got%20an%20A!%22%29%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20break%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20case%20'B'%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Great%20job!%22%29%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20break%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20case%20'C'%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Congrats!%20You%20passed!%22%29%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20break%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20case%20'D'%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Whew!%20You%20just%20passed!%22%29%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20break%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20case%20'F'%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Oops!%20Better%20luck%20next%20time!%22%29%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20break%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20default%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Invalid%20letter%20grade%22%29%3B%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%7D&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>
