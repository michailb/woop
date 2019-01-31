# JS Codeacademy Intro Notes Pt.3

## Scope

- *block scope*. When a variable is defined inside a block, it is only accessible to the code within the curly braces `{}`. We say that variable has *block scope* because it is *only* accessible to the lines of code within that block.

Variables that are declared with block scope are known as *local variables*because they are only available to the code that is part of the same block.

Block scope works like this:

    const logSkyColor = () => {
      let color = 'blue'; 
      console.log(color); // blue 
    };
    
    logSkyColor(); // blue 
    console.log(color); // ReferenceError

You'll notice:

- We define a function `logSkyColor()`.
- Within the function, the `color` variable is only available within the curly braces of the function.
- If we try to log the same variable outside the function, throws a `ReferenceError`.

- When you declare global variables, they go to the global namespace. The global namespace allows the variables to be accessible from anywhere in the program. These variables remain there until the program finishes which means our global namespace can fill up really quickly.
- Tightly scoping your variables will greatly improve your code in several ways:
- It will make your code more legible since the blocks will organize your code into discrete sections.
- It makes your code more understandable since it clarifies which variables are associated with different parts of the program rather than having to keep track of them line after line!
- It's easier to maintain your code, since your code will be modular.
- It will save memory in your code because it will cease to exist after the block finishes running.
- **Scope** is the idea in programming that some variables are accessible/inaccessible from other parts of the program.
- **Blocks** are statements that exist within curly braces `{}`.
- **Global scope** refers to the context within which variables are accessible to every part of the program.
- **Global variables** are variables that exist within global scope.
- **Block scope** refers to the context within which variables that are accessible only within the block they are defined.
- **Local variables** are variables that exist within block scope.
- **Global namespace** is the space in our code that contains globally scoped information.
- **Scope pollution** is when too many variables exist in a namespace or variable names are reused.

## Arrays

- One way we can create an array is to use an *array literal*. An array literal creates an array by wrapping items in square brackets `[]`. Remember from the previous exercise, arrays can store any data type — we can have an array that holds all the same data types or an array that holds different data types.

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-arrays/array+literal.svg)

Let's take a closer look at the syntax in the array example:

- The array is represented by the square brackets `[]` and the content inside.
- Each content item inside an array is called an *element*.
- There are three different elements inside the array.
- Each element inside the array is a different data type.

We can also save an array to a variable. You may have noticed we did this in the previous exercise:

- Each element in an array has a numbered position known as its *index*. We can access individual items using their index, which is similar to referencing an item in a list based on the item's position.

Arrays in JavaScript are *zero-indexed*, meaning the positions start counting from `0` rather than `1`. Therefore, the first item in an array will be at position `0`. Let's see how we could access an element in an array:

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-arrays/array+indices.svg)

In the code snippet above:

- `cities` is an array that has three elements.
- We're using bracket notation, `[]` with the index after the name of the array to access the element.
- `cities[0]` will access the element at index `0` in the array `cities`. You can think of `cities[0]` as accessing the space in memory that holds the string `'New York'`.

- Once you have access to an element in an array, you can update its value.

    let seasons = ['Winter', 'Spring', 'Summer', 'Fall'];
    
    seasons[3] = 'Autumn';
    console.log(seasons); 
    //Output: ['Winter', 'Spring', 'Summer', 'Autumn']

In the example above, the `seasons` array contained the names of the four seasons.

However, we decided that we preferred to say `'Autumn'` instead of `'Fall'`.

The line, `seasons[3] = 'Autumn';` tells our program to change the item at index 3 of the `seasons` array to be `'Autumn'` instead of what is already there.

- Variables declared with the const keyword cannot be reassigned. However, elements in an array declared with const remain mutable. Meaning that we can change the contents of a const array, but cannot reassign a new array or a different value.
- One of an array's built-in properties is `length` and it returns the number of items in the array. We access the `.length` property just like we do with strings. Check the example below:

    const newYearsResolutions = ['Keep a journal', 'Take a falconry class'];
    
    console.log(newYearsResolutions.length);
    // Output: 2

In the example above, we log `newYearsResolutions.length` to the console using the following steps:

- We use *dot notation*, chaining a period with the property name to the array, to access the `length` property of the `newYearsResolutions`array.
- Then we log the `length` of `newYearsResolution` to the console.
- Since `newYearsResolution` has two elements, so `2` would be logged to the console.

When we want to know how many elements are in an array, we can access the `.length` property.

- One method, `.push()` allows us to add items to the end of an array. Here is an example of how this is used:

    const itemTracker = ['item 0', 'item 1', 'item 2'];
    
    itemTracker.push('item 3', 'item 4');
    
    console.log(itemTracker); 
    // Output: ['item 0', 'item 1', 'item 2', 'item 3', 'item 4'];

- Another array method, `.pop()`, removes the last item of an array.

    const newItemTracker = ['item 0', 'item 1', 'item 2'];
    
    const removed = newItemTracker.pop();
    
    console.log(newItemTracker); 
    // Output: [ 'item 0', 'item 1' ]
    console.log(removed);
    // Output: item 2

- In the example above, calling `.pop()` on the `newItemTracker` array removed `item 2` from the end.
- `.pop()` does not take any arguments, it simply removes the last element of `newItemTracker`.
- `.pop()` returns the value of the last element. In the example, we store the returned value in a variable `removed` to be used for later.
- `.pop()` is a method that mutates the initial array.
- There are many more array methods than just .push() and .pop(). You can read about all of the array methods that exist on the Mozilla Developer Network (MDN) array documentation.
- Some arrays methods that are available to JavaScript developers include: .join(), .slice(), .splice(), .shift(), .unshift(), and .concat() amongst many others. Using these built-in methods make it easier to do some common tasks when working with arrays.
- The slice() method returns a shallow copy of a portion of an array into a new array object selected from begin to end (end not included). The original array will not be modified.
- Take a look at the following example where we call `.push()` on an array inside a function. Recall, the `.push()` method mutates, or changes, an array:

    const flowers = ['peony', 'daffodil', 'marigold'];
    
    function addFlower(arr) {
      arr.push('lily');
    }
    
    addFlower(flowers);
    
    console.log(flowers); // Output: ['peony', 'daffodil', 'marigold', 'lily']

Let's go over what happened in the example:

- The `flowers` array that has 3 elements.
- The function `addFlower()` has a parameter of `arr` uses `.push()` to add a `'lily'` element into `arr`.
- We call `addFlower()` with an argument of `flowers` which will execute the code inside `addFlower`.
- We check the value of `flowers` and it now includes the `'lily'`element! The array was mutated!

- When an array contains another array it is known as a *nested array*. Examine the example below:
- const nestedArr = [[1], [2, 3]];
- To access the nested arrays we can use bracket notation with the index value, just like we did to access any other element:
- const nestedArr = [[1], [2, 3]];

console.log(nestedArr[1]); // Output: [2, 3]
- Notice that `nestedArr[1]` will grab the element in index 1 which is the array `[2, 3]`. Then, if we wanted to access the elements within the nested array we can *chain*, or add on, more bracket notation with index values.
- const nestedArr = [[1], [2, 3]];

console.log(nestedArr[1]); // Output: [2, 3]
console.log(nestedArr[1][0]); // Output: 2
- In the second `console.log()` statement, we have two bracket notations chained to `nestedArr`. We know that `nestedArr[1]` is the array `[2, 3]`. Then to grab the first element from that array, we use `nestedArr[1][0]`and we get the value of `2`.

Arrays review 

- Arrays are lists that store data in JavaScript.
- Arrays are created with brackets `[]`.
- Each item inside of an array is at a numbered position, or index, starting at `0`.
- We can access one item in an array using its index, with syntax like: `myArray[0]`.
- We can also change an item in an array using its index, with syntax like `myArray[0] = 'new string'`;
- Arrays have a `length` property, which allows you to see how many items are in an array.
- Arrays have their own methods, including `.push()` and `.pop()`, which add and remove items from an array, respectively.
- Arrays have many methods that perform different tasks, such as `.slice()` and `.shift()`, you can find documentation at the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) website.
- Some built-in methods are mutating, meaning the method will change the array, while others are not mutating. You can always check the documentation.
- Variables that contain arrays can be declared with `let` or `const`. Even when declared with `const`, arrays are still mutable. However, a variable declared with `const` cannot be reassigned.
- Arrays mutated inside of a function will keep that change even outside the function.
- Arrays can be nested inside other arrays.
- To access elements in nested arrays chain indices using bracket notation.