# JS Codeacademy Intro Notes Pt.1

## Console.log

- In JavaScript, the console keyword refers to an object, a collection of data and actions, that we can use in our code
- A single line comment will comment out a single line and is denoted with two forward slashes // preceding it.
- A multi-line comment will comment out multiple lines and is denoted with /* to begin the comment, and */ to end the comment.
- You can also use this syntax to comment something out in the middle of a line of code:

    console.log(/*IGNORED!*/ 5);  // Still just prints 5

## Data Types

*Data types* are the classifications we give to the different kinds of data that we use in programming. In JavaScript, there are seven fundamental data types:

1. *Number*: Any number, including numbers with decimals: `4`, `8`, `1516`, `23.42`.
2. *String*: Any grouping of characters on your keyboard (letters, numbers, spaces, symbols, etc.) surrounded by single quotes: `' ... '` or double quotes `" ... "`. Though we prefer single quotes. Some people like to think of string as a fancy word for text.
3. *Boolean*: This data type only has two possible values— either `true`or `false` (without quotes). It’s helpful to think of booleans as on and off switches or as the answers to a "yes" or "no" question.
4. *Null*: This data type represents the intentional absence of a value, and is represented by the keyword `null` (without quotes).
5. *Undefined*: This data type is denoted by the keyword `undefined`(without quotes). It also represents the absence of a value though it has a different use than `null`.
6. *Symbol*: A newer feature to the language, symbols are unique identifiers, useful in more complex coding. No need to worry about these for now.
7. *Object*: Collections of related data.

    The first 6 of those types are considered *primitive data types*. They are the most basic data types in the language. *Objects* are more complex, and you’ll learn much more about them as you progress through JavaScript. At first, seven types may not seem like that many, but soon you’ll observe the world opens with possibilities once you start leveraging each one. As you learn more about objects, you’ll be able to create complex collections of data.

    ## Arithmetic Operators

    Basic arithmetic often comes in handy when programming.

    An *operator* is a character that performs a task in our code. JavaScript has several built-in in *arithmetic operators*, that allow us to perform mathematical calculations on numbers. These include the following operators and their corresponding symbols:

    1. Add: `+`
    2. Subtract: `-`
    3. Multiply: `*`
    4. Divide: `/`
    5. Remainder: `%`

    The remainder operator, sometimes called modulo, returns the number that remains after the right-hand number divides into the left-hand number as many times as it evenly can: 11 % 3 equals 2 because 3 fits into 11 three times, leaving 2 as the remainder.

    ## String Concatenation

    - Operators aren't just for numbers! When a `+` operator is used on two strings, it appends the right string to the left string:

        console.log('hi' + 'ya'); // Prints 'hiya'
        console.log('wo' + 'ah'); // Prints 'woah'
        console.log('I love to ' + 'code.')
        // Prints 'I love to code.'

    ## Properties

    - When you introduce a new piece of data into a JavaScript program, the browser saves it as an instance of the data type. Every string instance has a property called `length` that stores the number of characters in that string. You can retrieve property information by appending the string with a period and the property name:

        console.log('Hello'.length); // Prints 5

    The `.` is another operator! We call it the *dot operator*.

    In the example above, the value saved to the `length` property is retrieved from the instance of the string, `'Hello'`. The program prints `5` to the console, because `Hello` has five characters in it.

    ## Methods

    - Remember that methods are actions we can perform. JavaScript provides a number of string methods.

    We *call*, or use, these methods by appending an instance with a period (the dot operator), the name of the method, and opening and closing parentheses: ie. `'example string'.methodName()`.

    Does that syntax look a little familiar? When we use `console.log()`we're calling the `.log()` method on the `console` object. 

        console.log('hello'.toUpperCase()); // Prints 'HELLO'
        console.log('Hey'.startsWith('H')); // Prints true

    ## Built-in Objects

        console.log(Math.random()); // Prints a random number between 0 and 1

    In the example above, we called the `.random()` method by appending the object name with the dot operator, the name of the method, and opening and closing parentheses. This method returns a random number between 0 and 1.

    ## Review

    - Data is printed, or logged, to the console, a panel that displays messages, with `console.log()`.
    - You can write single-line comments with `//` and multi-line comments between `/*` and `*/`.
    - There are 7 fundamental data types in JavaScript: strings, numbers, booleans, null, undefined, symbol, and object.
    - Numbers are any number without quotes: `23.8879`
    - Strings are characters wrapped in single or double quotes: `'Sample String'`
    - The built-in arithmetic operators include `+`, `-`, `*`, `/`, and `%`.
    - Objects, including instances of data types, can have properties, stored information. The properties are denoted with a `.` after the name of the object, for example: `'Hello'.length`.
    - Objects, including instances of data types, can have methods which perform actions. Methods are called by appending the object or instance with a period, the method name, and parentheses. For example: `'hello'.toUpperCase()`.
    - We can access properties and methods by using the `.`, dot operator.
    - Built-in objects, including `Math`, are collections of methods and properties that JavaScript provides.

    ## Variables

    - In programming, a *variable* is a container for a value. You can think of variables as little containers for information that live in a computer's memory. Information stored in variables, such as a username, account number, or even personalized greeting can then be found in memory.
    - Variables also provide a way of labeling data with a descriptive name, so our programs can be understood more clearly by the reader and ourselves.
    - In short, variables label and store data in memory. There are only a few things you can do with variables:
    - Create a variable with a descriptive name.
    - Store or update information stored in a variable.
    - Reference or “get” information stored in a variable
    - Variable names cannot start with numbers.
    - Variable names are case sensitive, so `myName` and `myname` would be different variables. It is bad practice to create two variables that have the same name using different cases.
    - Variable names cannot be the same as *keywords*. For a comprehensive list of keywords check out [MDN's keyword documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords).

        The `let` keyword signals that the variable can be reassigned a different value. Take a look at the example:

        let meal = 'Enchiladas';
        console.log(meal); // Output: Enchiladas
        meal = 'Burrito';
        console.log(meal); // Output: Burrito

    Another concept that we should be aware of when using `let` (and even `var`) is that we can declare a variable without assigning the variable a value. In such a case, the variable will be automatically initialized with a value of `undefined`:

        let price;
        console.log(price); // Output: undefined
        price = 350;
        console.log(price); // Output: 350

    Just like with `var` and `let` you can store any value in a `const`variable. The way you declare a `const` variable and assign a value to it follows the same structure as `let` and `var`. Take a look at the following example:

        const myName = 'Gilberto';
        console.log(myName); // Output: Gilberto

    However, a `const` variable cannot be reassigned because it is *constant*. If you try to reassign a `const` variable, you'll get a `TypeError`.

    Constant variables *must* be assigned a value when declared. If you try to declare a `const` variable without a value, you'll get a `SyntaxError`.

    If you're trying to decide between which keyword to use, `let` or `const`, think about whether you'll need to reassign the variable later on. If you do need to reassign the variable use `let`, otherwise, use `const`.

    ## Mathematical Assignment Operators

    +, -, /, *, (% gives a remainder)

    += etc will assign a new value to a variable after applying the math operator.

    Other mathematical assignment operators include the *increment operator*(`++`) and *decrement operator* (`--`).

    The increment operator will increase the value of the variable by 1. The decrement operator will decrease the value of the variable by 1. For example

    Just like the previous mathematical assignment operators (+=, -=, *=, /=), the variable's value is updated and assigned as the new value of that variable.

    The `+` operator can be used to combine two string values even if those values are being stored in variables:

        let myPet = 'armadillo';
        console.log('I own a pet ' + myPet + '.'); 
        // Output: 'I own a pet armadillo.'

    Check out the following example where a template literal is used to log strings together:

        const myPet = 'armadillo';
        console.log(`I own a pet ${myPet}.`);
        // Output: I own a pet armadillo.

    - If you need to check the data type of a variable's value, you can use the typeof operator.

        const unknown1 = 'foo';
        console.log(typeof unknown1); // Output: string

    - Variables hold reusable data in a program and associate it with a name.
    - Variables are stored in memory.
    - The `var` keyword is used in pre-ES6 versions of JS.
    - `let` is the preferred way to declare a variable when it can be reassigned, and `const` is the preferred way to declare a variable with a constant value.
    - Variables that have not been initialized store the primitive data type `undefined`.
    - Mathematical assignment operators make it easy to calculate a new value and assign it to the same variable.
    - The `+` operator is used to concatenate strings including string values held in variables
    - In ES6, template literals use backticks ``` and `${}` to interpolate values into a string.
    - The `typeof` keyword returns the data type (as a string) of a value.

    ## Conditional Statements

    In programming, we can also perform a task based on a condition using an `if` statement:

        if (true) {
          console.log('This message will print!'); 
        } 
        // Prints "This message will print!"

    Notice in the example above, we have an `if` statement. The `if`statement is composed of:

    - The `if` keyword followed by a set of parentheses `()` which is followed by a *code block*, or *block statement*, indicated by a set of curly braces `{}`.
    - Inside the parentheses `()`, a condition is provided that evaluates to `true` or `false`.
    - If the condition evaluates to `true`, the code inside the curly braces `{}` runs, or *executes*.
    - If the condition evaluates to `false`, the block won't execute.

    Use the `if` statement to specify a block of JavaScript code to be executed if a condition is true.

    # Syntax

    if (condition) { // *block of code to be executed if the condition is true*}

    Note that `if` is in lowercase letters. Uppercase letters (If or IF) will generate a JavaScript error.

    # Example

    Make a "Good day" greeting if the hour is less than 18:00:

    if (hour < 18) { greeting = "Good day";}

    The result of greeting will be:

    `Good day`

    When writing conditional statements, sometimes we need to use different types of operators to compare values. These operators are called *comparison operators*.

    Here is a list of some handy comparison operators and their syntax:

    - Less than: `<`
    - Greater than: `>`
    - Less than or equal to: `<=`
    - Greater than or equal to: `>=`
    - Is equal to: `===`
    - Is NOT equal to: `!==`

    Working with conditionals means that we will be using booleans, `true` or `false` values. In JavaScript, there are operators that work with boolean values known as *logical operators*. We can use logical operators to add more sophisticated logic to our conditionals. There are three logical operators:

    - the *and* operator (`&&`)
    - the *or* operator (`||`)
    - the *not* operator, otherwise known as the *bang* operator (`!`)

    Sometimes, you'll want to check if a variable exists and you won't necessarily want it to equal a specific value— you'll only check to see if the variable has been assigned a value.

    Here's an example:

        let myVariable = 'I Exist!';
        if (myVariable) {
           console.log(myVariable)
        } else {
           console.log('The variable does not exist.')
        }

    The code block in the `if` statement will run because `myVariable` has a*truthy* value; even though the value of `myVariable` is not explicitly the value `true`, when used in a boolean or conditional context, it evaluates to `true` because it has been assigned a non-falsy value.

    So which values are *falsy*— or evaluate to `false` when checked as a condition? The list of falsy values includes:

    - `0`
    - Empty strings like `""` or `''`
    - `null` which represent when there is no value at all
    - `undefined` which represent when a declared variable lacks a value
    - `NaN`, or Not a Number
    - In a boolean condition, JavaScript assigns the truthy value to a variable if you use the || operator in your assignment

    - We can use a *ternary operator* to simplify an `if...else` statement.

    Take a look at the `if...else` statement example:

        let isNightTime = true;
        
        if (isNightTime) {
          console.log('Turn on the lights!');
        } else {
          console.log('Turn off the lights!');
        }

    We can use a *ternary operator* to perform the same functionality:

        isNightTime ? console.log('Turn on the lights!') : console.log('Turn off the lights!');

    - Like if...else statements, ternary operators can be used for conditions which evaluate to true or false.

    The `else if` statement always comes after the `if` statement and before the `else` statement. The `else if` statement also takes a condition. Let’s take a look at the syntax:

        let stopLight = 'yellow';
        
        if (stopLight === 'red') {
          console.log('Stop!');
        } else if (stopLight === 'yellow') {
          console.log('Slow down.');
        } else if (stopLight === 'green') {
          console.log('Go!');
        } else {
          console.log('Caution, unknown!');
        }

    A `switch` statement provides an alternative syntax that is easier to read and write. A `switch` statement looks like this:

        let groceryItem = 'papaya';
        
        switch (groceryItem) {
          case 'tomato':
            console.log('Tomatoes are $0.49');
            break;
          case 'lime':
            console.log('Limes are $1.49');
            break;
          case 'papaya':
            console.log('Papayas are $1.29');
            break;
          default:
            console.log('Invalid item');
            break;
        }
        
        // Prints 'Papayas are $1.29'

    - The `switch` keyword initiates the statement and is followed by `( ... )`, which contains the value that each `case` will compare. In the example, the value or expression of the `switch` statement is `groceryItem`.
    - Inside the block, `{ ... }`, there are multiple `case`s. The `case`keyword checks if the expression matches the specified value that comes after it. The value following the first `case` is `'tomato'`. If the value of `groceryItem` equalled `'tomato'`, that `case`'s `console.log()` would run.
    - The value of `groceryItem` is `'papaya'`, so the third `case` runs— `Papayas are $1.29` is logged to the console.
    - The `break` keyword tells the computer to exit the block and not execute any more code or check any other cases inside the code block. Note: Without the `break` keyword at the end of each case, the program would execute the code for all matching cases and the default code as well. This behavior is different from `if`/`else`conditional statements which execute only one block of code.
    - At the end of each `switch` statement, there is a `default` statement. If none of the `case`s are true, then the code in the `default`statement will run.

    - An `if` statement checks a condition and will execute a task if that condition evaluates to `true`.
    - `if...else` statements make binary decisions and execute different code blocks based on a provided condition.
    - We can add more conditions using `else if` statements.
    - Comparison operators, including `<`, `>`, `<=`, `>=`, `===`, and `!==` can compare two values.
    - The logical and operator, `&&`, or "and", checks if both provided expressions are truthy.
    - The logical operator `||`, or "or", checks if either provided expression is truthy.
    - The bang operator, `!`, switches the truthiness and falsiness of a value.
    - The ternary operator is shorthand to simplify concise `if...else`statements.
    - A `switch` statement can be used to simplify the process of writing multiple `else if` statements. The `break` keyword stops the remaining `case`s from being checked and executed in a `switch`statement.