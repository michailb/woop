# JS Codeacademy Intro Notes Pt.2

## Functions

In programming, we often use code to perform a specific task multiple times. Instead of rewriting the same code, we can group a block of code together and associate it with one task, then we can reuse that block of code whenever we need to perform the task again. We achieve this by creating a function. A function is a reusable block of code that groups together a sequence of statements to perform a specific task.

A function declaration consists of:

- The `function` keyword.
- The name of the function, or its identifier, followed by parentheses.
- A function body, or the block of statements required to perform a specific task, enclosed in the function’s curly brackets, `{ }`.
- a function declaration binds a function to an identifier.

However, a function declaration does not ask the code inside the function body to run, it just declares the existence of the function. The code inside a function body runs, or *executes*, only when the function is *called*. To call a function in your code, you type the function name followed by parentheses.

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/name.svg)

This

*function call*

executes the function body, or all of the statements between the curly braces in the function declaration.

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/function+execution.svg)

We can call the same function as many times as needed.

- Observe how to specify parameters in our function declaration:

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/function+parameters.svg)

In the diagram above, `calculateArea()`, computes the area of a rectangle, based on two inputs, `width` and `height`. The parameters are specified between the parenthesis as `width` and `height`, and inside the function body, they act just like regular variables. `width` and `height` act as placeholders for values that will be multiplied together.

When calling a function that has parameters, we specify the values in the parentheses that follow the function name. The values that are passed to the function when it is called are called *arguments*. Arguments can be passed to the function as values or variables.

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/by_value.svg)

In the function call above, the number `10` is passed as the `width` and `6`is passed as `height`. Notice that the order in which arguments are passed and assigned follows the order that the parameters are declared.

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/by_variable.svg)

The variables `rectWidth` and `rectHeight` are initialized with the values for the height and width of a rectangle before being used in the function call.

By using parameters, `calculateArea()` can be reused to compute the area of any rectangle! Functions are a powerful tool in computer programming so let’s practice creating and calling functions with parameters.

- One of the features added in ES6 is the ability to use *default parameters*. Default parameters allow parameters to have a predetermined value in case there is no argument passed into the function or if the argument is `undefined` when called.

Take a look at the code snippet below that uses a default parameter:

    function greeting (name = 'stranger') {
      console.log(`Hello, ${name}!`)
    }
    
    greeting('Nick') // Output: Hello, Nick!
    greeting() // Output: Hello, stranger!

- In the example above, we used the `=` operator to assign the parameter `name` a default value of `'stranger'`. This is useful to have in case we ever want to include a non-personalized default greeting!
- When the code calls `greeting('Nick')` the value of the argument is passed in and, `'Nick'`, will override the default parameter of `'stranger'` to log `'Hello, Nick!'` to the console.
- When there isn't an argument passed into `greeting()`, the default value of `'stranger'` is used, and `'Hello, stranger!'` is logged to the console.

- When a function is called, the computer will run through the function's code and evaluate the result of calling the function. By default that resulting value is `undefined`.

    function rectangleArea(width, height) {
      let area = width * height 
    }
    console.log(rectangleArea(5, 7)) // Prints undefined

In the code example, we defined our function to calculate the `area` of a `width` and `height` parameter. Then `rectangleArea()` is invoked with the arguments `5` and `7`. But when we went to print the results we got `undefined`. Did we write our function wrong? No! In fact, the function worked fine, and the computer did calculate the area as `35`, but we didn't capture it. So how can we do that? With the keyword `return`!

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/function+return.svg)

To pass back information from the function call, we use a return statement. To create a return statement, we use the `return` keyword followed by the value that we wish to return. Like we saw above, if the value is omitted, `undefined` is returned instead.

When a `return` statement is used in a function body, the execution of the function is stopped and the code that follows it will not be executed. Look at the example below:

- If we wanted to define a function that converts the temperature from Celsius to Fahrenheit, we could write two functions like:

    function multiplyByNineFifths(number) {
      return number * (9/5);
    };
    
    function getFahrenheit(celsius) {
      return multiplyByNineFifths(celsius) + 32;
    };
    
    getFahrenheit(15); // Returns 59

In the example above:

- `getFahrenheit()` is called and `15` is passed as an argument.
- The code block inside of `getFahrenheit()` calls `multiplyByNineFifths()` and passes `15` as an argument.
- `multiplyByNineFifths()` takes the argument of `15` for the `number`parameter.
- The code block inside of `multiplyByNineFifths()` function multiplies `15` by `(9/5)`, which evaluates to `27`.
- `27` is returned back to the function call in `getFahrenheit()`.
- `getFahrenheit()` continues to execute. It adds `32` to `27`, which evaluates to `59`.
- Finally, `59` is returned back to the function call `getFahrenheit(15)`.

In a function expression, the function name is usually omitted. A function with no name is called an *anonymous function*. A function expression is often stored in a variable in order to refer to it.

Consider the following function expression:

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/expression.svg)

To declare a function expression:

1. Declare a variable to make the variable’s name be the name, or identifier, of your function. Since the release of ES6, it is common practice to use `const` as the keyword to declare the variable.
2. Assign as that variable's value an anonymous function created by using the `function` keyword followed by a set of parentheses with possible parameters. Then a set of curly braces that contain the function body.

To invoke a function expression, write the name of the variable in which the function is stored followed by parentheses enclosing any arguments being passed into the function.

    variableName(argument1, argument2)

Unlike function declarations, function expressions are not hoisted so they cannot be called before they are defined.

- S6 introduced *arrow function syntax*, a shorter way to write functions by using the special "fat arrow" `() =>` notation.

Arrow functions remove the need to type out the keyword `function`every time you need to create a function. Instead, you first include the parameters inside the `( )` and then add an arrow `=>` that points to the function body surrounded in `{ }` like this:

    const rectangleArea = (width, height) => {
      let area = width * height;
      return area
    }

1. Functions that take only a single parameter do not need that parameter to be enclosed in parentheses. However, if a function takes zero or multiple parameters, parentheses are required.

    ![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/parameters.svg)

2. A function body composed of a single-line block does not need curly braces. Without the curly braces, whatever that line evaluates will be automatically returned. The contents of the block should immediately follow the arrow `=>` and the `return` keyword can be removed. This is referred to as *implicit return*.

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/return.svg)

So if we have a function:

    const squareNum = (num) => {
      return num * num;
    };

We can refactor the function to:

    const squareNum = num => num * num;

Notice the following changes:

- The parentheses around `num` have been removed, since it has a single parameter.
- The curly braces `{ }` have been removed since the function consists of a single-line block.
- The `return` keyword has been removed since the function consists of a single-line block.

## Functions Review

- A *function* is a reusable block of code that groups together a sequence of statements to perform a specific task.
- A *function declaration* :

    ![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/declaration.svg)

- A parameter is a named variable inside a function's block which will be assigned the value of the argument passed in when the function is invoked:

    ![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/function+parameters.svg)

- To *call* a function in your code:

    ![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/name.svg)

- ES6 introduces new ways of handling arbitrary parameters through *default parameters* which allow us to assign a default value to a parameter in case no argument is passed into the function.
- To return a value from a function, we use a *return statement*.
- To define a function using *function expressions*:

    ![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/expression.svg)

- To define a function using *arrow function notation*:

    ![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/arrow+notation.svg)

- Function definition can be made concise using concise arrow notation:

    ![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-functions/Diagram/return.svg)

It's good to be aware of the differences between function expressions, arrow functions, and function declarations. As you program more in JavaScript, you'll see a wide variety of how these function types are used.