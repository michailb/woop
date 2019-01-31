# JS Codeacademy Intro Notes Pt.4

## Loops

- A `for` loop contains three expressions separated by `;` inside the parentheses:
1. an *initialization* starts the loop and can also be used to declare the iterator variable.

1. a *stopping condition* is the condition that the iterator variable is evaluated against— if the condition evaluates to `true` the code block will run, and if it evaluates to `false` the code will stop.
2. an *iteration statement* is used to update the iterator variable on each loop.

The `for` loop syntax looks like this:

    for (let counter = 0; counter < 4; counter++) {
      console.log(counter);
    }

In this example, the output would be the following:

    0
    1
    2
    3

Let’s break down the example:

- The initialization is `let counter = 0`, so the loop will start counting at `0`.
- The stopping condition is `counter < 4`, meaning the loop will run as long as the iterator variable, `counter`, is less 4.
- The iteration statement is `counter++`. This means after each loop, the value of `counter` will increase by 1. For the first iteration `counter`will equal `0`, for the second iteration `counter` will equal 1, and so on.
- The code block is inside of the curly braces, `console.log(counter)`, will execute until the condition evaluates to `false`. The condition will be false when `counter` is greater than or equal to 4 — the point that the condition becomes false is sometimes called the *stop condition*.

- One use for a nested `for` loop is to compare the elements in two arrays. For each round of the outer `for` loop, the inner `for` loop will run completely.
- Let’s look at an example of a nested `for` loop:

    const myArray = [6, 19, 20];
    const yourArray = [19, 81, 2];
    for (let i = 0; i < myArray.length; i++) {
      for (let j = 0; j < yourArray.length; j++) {
        if (myArray[i] === yourArray[j]) {
          console.log('Both loops have the number: ' + yourArray[j])
        }
      }
    };

- Let's think about what's happening in the nested loop in our example. For each element in the outer loop array, `myArray`, the inner loop will run in its entirety comparing the current element from the outer array, `myArray[i]`, to each element in the inner array, `yourArray[j]`. When it finds a match, it prints a string to the console.
- The syntax of a for loop is ideal when we know how many times the loop should run, but we don't always know this in advance. Think of eating like a while loop: when you start taking bites, you don't know the exact number you'll need to become full. Rather you'll eat while you're hungry. In situations when we want a loop to execute an undetermined number of times, while loops are the best choice.
- `while` loop:

    // A for loop that prints 1, 2, and 3
    for (let counterOne = 1; counterOne < 4; counterOne++){
      console.log(counterOne);
    }
    
    // A while loop that prints 1, 2, and 3
    let counterTwo = 1;
    while (counterTwo < 4) {
      console.log(counterTwo);
      counterTwo++;
    }

- A `do...while` statement says to do a task once and then keep doing it until a specified condition is no longer met. The syntax for a `do...while`statement looks like this:

    let countString = '';
    let i = 0;
    
    do {
      countString = countString + i;
      i++;
    } while (i < 5);
    
    console.log(countString);

In this example, the code block makes changes to the `countString`variable by appending the string form of the `i` variable to it. First, the code block after the `do` keyword is executed once. Then the condition is evaluated. If the condition evaluates to `true`, the block will execute again. The looping stops when the condition evaluates to `false`.

Note that the `while` and `do...while` loop are different! Unlike the `while`loop, `do...while` will run at least once whether or not the condition evaluates to `true`.

    const firstMessage = 'I will print!';
    const secondMessage = 'I will not print!'; 
    
    // A do while with a stopping condition that evaluates to false
    do {
     console.log(firstMessage)
    } while (true === false);
    
    // A while loop with a stopping condition that evaluates to false
    while (true === false){
      console.log(secondMessage)
    };

- The `break` keyword allows programs to “break” out of the loop from within the loop's block.

Let’s check out the syntax of a `break` keyword:

    for (let i = 0; i < 99; i++) {
      if (i > 2 ) {
         break;
      }
      console.log('Banana.');
    }
    
    console.log('Orange you glad I broke out the loop!');

This is the output for the code:

    Banana.
    Banana.
    Banana.
    Orange you glad I broke out the loop!

`break`

Loops Review:

- Loops perform repetitive actions so we don’t have to code that process manually every time.
- How to write `for` loops with an iterator variable that increments or decrements
- How to use a `for` loop to iterate through an array
- A nested `for` loop is a loop inside another loop
- `while` loops allow for different types of stopping conditions
- Stopping conditions are crucial for avoiding infinite loops.
- `do...while` loops run code at least once— only checking the stopping condition after the first execution
- The `break` keyword allows programs to leave a loop during the execution of its block

## Higher Order Functions

- In JavaScript, functions are *first class objects*, this means that like other objects you've encountered, JavaScript functions can have properties and methods.

Since functions are a type of object, they have properties such as `.length` and `.name` and methods such as `.toString()`. You can see more about the methods and properties of functions [in the documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function).

- A *higher-order function* is a function that either accepts functions as parameters, returns a function, or both! We call the functions that get passed in as parameters and invoked *callback functions*because they get called during the execution of the higher-order function.

When we pass a function in as an argument to another function, we don't invoke it. Invoking the function would evaluate to the return value of that function call. With callbacks, we pass in the function itself by typing the function name *without* the parentheses (that would evaluate to the result of calling the function):

    const timeFuncRuntime = funcParameter => {
       let t1 = Date.now();
       funcParameter();
       let t2 = Date.now();
       return t2 - t1;
    }
    
    const addOneToOne = () => 1 + 1;
    
    timeFuncRuntime(addOneToOne);

We wrote a higher-order function, `timeFuncRuntime()`. It takes in a function as an argument, saves a starting time, invokes the callback function, records the time after the function was called, and returns the time the function took to run by subtracting the starting time from the ending time.

Review:

- Abstraction allows us to write complicated code in a way that's easy to reuse, debug, and understand for human readers
- We can work with functions the same way we would any other type of data including reassigning them to new variables
- JavaScript functions are first-class objects, so they have properties and methods like any object
- Functions can be passed into other functions as parameters
- A higher-order function is a function that either accepts functions as parameters, returns a function, or both

## Iterators

`.forEach()`

will execute the same code for each element of an array.

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-iterators/iterator+anatomy.svg)

The code above will log a nicely formatted list of the groceries to the console. Let's explore the syntax of invoking `.forEach()`.

- `groceries.forEach()` calls the `forEach` method on the `groceries`array.
- `.forEach()` takes an argument of callback function. Remember, a callback function is a function passed as an argument into another function.
- `.forEach()` loops through the array and executes the callback function for each element. During each execution, the current element is passed as an argument to the callback function.
- The return value for `.forEach()` will always be `undefined`.

Another way to pass a callback for `.forEach()` is to use arrow function syntax.

    groceries.forEach(groceryItem => console.log(groceryItem));

- When `.map()` is called on an array, it takes an argument of a callback function and returns a new array! Take a look at an example of calling `.map()`:

    const numbers = [1, 2, 3, 4, 5]; 
    
    const bigNumbers = numbers.map(number => {
      return number * 10;
    });

`.map()` works in a similar manner to `.forEach()`— the major difference is that `.map()` returns a new array.

In the example above:

- `numbers` is an array of numbers.
- `bigNumbers` will store the return value of calling `.map()` on `numbers`.
- `numbers.map` will iterate through each element in the `numbers` array and pass the element into the callback function.
- `return number * 10` is the code we wish to execute upon each element in the array. This will save each value from the `numbers`array, multiplied by `10`, to a new array.

- Like `.map()`, `.filter()`returns a new array. However, `.filter()` returns an array of elements after filtering out certain elements from the original array. The callback function for the `.filter()` method should return `true` or `false`depending on the element that is passed to it. The elements that cause the callback function to return `true` are added to the new array. Take a look at the following example:

    const words = ['chair', 'music', 'pillow', 'brick', 'pen', 'door']; 
    
    const shortWords = words.filter(word => {
      return word.length < 6;
    });

- `words` is an array that contains string elements.
- `const shortWords =` declares a new variable that will store the returned array from invoking `.filter()`.
- The callback function is an arrow function has a single parameter, `word`. Each element in the `words` array will be passed to this function as an argument.
- `word.length < 6;` is the condition in the callback function. Any `word`from the `words` array that has fewer than `6` characters will be added to the `shortWords` array.

Let's also check the values of `words` and `shortWords`:

    console.log(words); // Output: ['chair', 'music', 'pillow', 'brick', 'pen', 'door']; 
    console.log(shortWords); // Output: ['chair', 'music', 'brick', 'pen', 'door']

- Calling `.findIndex()` on an array will return the index of the first element that evaluates to `true` in the callback function.

    const jumbledNums = [123, 25, 78, 5, 9]; 
    
    const lessThanTen = jumbledNums.findIndex(num => {
      return num < 10;
    });

- `jumbledNums` is an array that contains elements that are numbers.
- `const lessThanTen =` declares a new variable that stores the returned index number from invoking `.findIndex()`.
- The callback function is an arrow function has a single parameter, `num`. Each element in the `jumbledNums` array will be passed to this function as an argument.
- `num < 10;` is the condition that elements are checked against. `.findIndex()` will return the index of the first element which evaluates to `true` for that condition.

Let's take a look at what `lessThanTen` evaluates to:

    console.log(lessThanTen); // Output: 3

If we check what element has index of 3:

    console.log(jumbledNums[3]); // Output: 5

Great, the element in index `3` is the number `5`. This makes sense since `5` is the first element that is less than 10.

If there isn't a single element in the array that satisfies the condition in the callback, then `.findIndex()` will return `-1`.

    const greaterThan1000 = jumbledNums.findIndex(num => {
      return num > 1000;
    });
    
    console.log(greaterThan1000); // Output: -1