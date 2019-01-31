# JS Codeacademy Intro Notes Pt.5

## Objects

- Objects can be assigned to variables just like any JavaScript type. We use curly braces, `{}`, to designate an *object literal*:

    let spaceship = {}; // spaceship is an empty object

We fill an object with unordered data. This data is organized into *key-value pairs*. A key is like a variable name that points to a location in memory that holds a value.

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-objects/key+value.svg)

A key's value can be of any data type in the language including functions or other objects.

We make a key-value pair by writing the key's name, or *identifier*, followed by a colon and then the value. We separate each key-value pair in an object literal with a comma (`,`). Keys are strings, but when we have a key that does not have any special characters in it, JavaScript allows us to omit the quotation marks:

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-objects/objectliteraldiagram.svg)

    // An object literal with two key-value pairs
    let spaceship = {
      'Fuel Type': 'diesel',
      color: 'silver'
    };

The `spaceship` object has two properties `Fuel Type` and `color`. `'Fuel Type'` has quotation marks because it contains a space character.

- With property dot notation, we write the object's name, followed by the dot operator and then the property name (key):

    let spaceship = {
      homePlanet: 'Earth',
      color: 'silver'
    };
    spaceship.homePlanet; // Returns 'Earth',
    spaceship.color; // Returns 'silver',

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-objects/object+dot+notation.svg)

If we try to access a property that does not exist on that object,

`undefined`

will be returned.

    spaceship.favoriteIcecream; // Returns undefined

- The second way to access a key's value is by using bracket notation, .
- To use bracket notation to access an object's property, we pass in the property name (key) as a string.

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-objects/object+access+bracket.svg)

We

*must*

use bracket notation when accessing keys that have numbers, spaces, or special characters in them. Without bracket notation in these situations, our code would throw an error.

    let spaceship = {
      'Fuel Type': 'Turbo Fuel',
      'Active Duty': true,
      homePlanet: 'Earth',
      numCrew: 5
    };
    spaceship['Active Duty'];   // Returns true
    spaceship['Fuel Type'];   // Returns  'Turbo Fuel'
    spaceship['numCrew'];   // Returns 5
    spaceship['!!!!!!!!!!!!!!!'];   // Returns undefined

With bracket notation you can also use a variable inside the brackets to select the keys of an object. This can be especially helpful when working with functions:

    let returnAnyProp = (objectName, propName) => objectName[propName];
    
    returnAnyProp(spaceship, 'homePlanet'); // Returns 'Earth'

If we tried to write our `returnAnyProp()` function with dot notation (`objectName.propName`) the computer would look for a key of `'propName'` on our object and not the value of the `propName`parameter.

- Once we've defined an object, we're not stuck with all the properties we wrote. Objects are *mutable* meaning we can update them after we create them!

We can use either dot notation, `.`, or bracket notation, `[]`, and the assignment operator, `=` to add new key-value pairs to an object or change an existing property.

![](https://s3.amazonaws.com/codecademy-content/courses/learn-javascript-objects/object+update+property.svg)

One of two things can happen with property assignment:

- If the property already exists on the object, whatever value it held before will be replaced with the newly assigned value.
- If there was no property with that name, a new property will be added to the object.

It's important to know that although we can't reassign an object declared with `const`, we can still mutate it, meaning we can add new properties and change the properties that are there.

    const spaceship = {type: 'shuttle'};
    spaceship = {type: 'alien'}; // TypeError: Assignment to constant variable.
    spaceship.type = 'alien'; // Changes the value of the type property
    spaceship.speed = 'Mach 5'; // Creates a new key of 'speed' with a value of 'Mach 5'

You can delete a property from an object with the `delete` operator.

    const spaceship = {
      'Fuel Type': 'Turbo Fuel',
      homePlanet: 'Earth',
      mission: 'Explore the universe' 
    };
    
    delete spaceship.mission;  // Removes the mission property

- When the data stored on an object is a function we call that a *method*. A property is what an object has, while a method is what an object does.

Do object methods seem familiar? That’s because you've been using them all along! For example `console` is a global javascript object and `.log()` is a method on that object. `Math` is also a global javascript object and `.floor()` is a method on it.

We can include methods in our object literals by creating ordinary, comma-separated key-value pairs. The key serves as our method's name, while the value is an anonymous function expression.

    const alienShip = {
      invade: function () { 
        console.log('Hello! We have come to dominate your planet. Instead of Earth, it shall be called New Xaculon.')
      }
    };

With the new method syntax introduced in ES6 we can omit the colon and the `function` keyword.

    const alienShip = {
      invade () { 
        console.log('Hello! We have come to dominate your planet. Instead of Earth, it shall be called New Xaculon.')
      }
    };

Object methods are invoked by appending the object's name with the dot operator followed by the method name and parentheses:

    alienShip.invade(); // Prints 'Hello! We have come to dominate your planet. Instead of Earth, it shall be called New Xaculon.'

- Objects are *passed by reference*. This means when we pass a variable assigned to an object into a function as an argument, the computer interprets the parameter name as pointing to the space in memory holding that object. As a result, functions which change object properties actually mutate the object permanently (even when the object is assigned to a `const` variable).

    const spaceship = {
      homePlanet : 'Earth',
      color : 'silver'
    };
    
    let paintIt = obj => {
      obj.color = 'glorious gold'
    };
    
    paintIt(spaceship);
    
    spaceship.color // Returns 'glorious gold'

Our function `paintIt()` permanently changed the color of our `spaceship` object. However, reassignment of the `spaceship` variable wouldn't work in the same way:

    let spaceship = {
      homePlanet : 'Earth',
      color : 'red'
    };
    let tryReassignment = obj => {
      obj = {
        identified : false, 
        'transport type' : 'flying'
      }
      console.log(obj) // Prints {'identified': false, 'transport type': 'flying'}
    
    };
    tryReassignment(spaceship) // The attempt at reassignment does not work.
    spaceship // Still returns {homePlanet : 'Earth', color : 'red'};
    
    spaceship = {
      identified : false, 
      'transport type': 'flying'
    }; // Regular reassignment still works.

Let's look at what happened in the code example:

- We declared this `spaceship` object with `let`. This allowed us to reassign it to a new object with `identified` and `'transport type'`properties with no problems.
- When we tried the same thing using a function designed to reassign the object passed into it, the reassignment didn't stick (even though calling `console.log()` on the object produced the expected result).
- When we passed `spaceship` into that function, `obj` became a reference to the memory location of the `spaceship` object, but *not* to the `spaceship` variable. This is because the `obj` parameter of the `tryReassignment()` function is a variable in its own right. The body of `tryReassignment()` has no knowledge of the `spaceship` variable at all!
- When we did the reassignment in the body of `tryReassignment()`, the `obj` variable came to refer to the memory location of the object `{'identified' : false, 'transport type' : 'flying'}`, while the `spaceship` variable was completely unchanged from its earlier value.

- `for...in` will execute a given block of code for each property in an object.

    let spaceship = {
        crew: {
        captain: { 
            name: 'Lily', 
            degree: 'Computer Engineering', 
            cheerTeam() { console.log('You got this!') } 
            },
        'chief officer': { 
            name: 'Dan', 
            degree: 'Aerospace Engineering', 
            agree() { console.log('I agree, captain!') } 
            },
        medic: { 
            name: 'Clementine', 
            degree: 'Physics', 
            announce() { console.log(`Jets on!`) } },
        translator: {
            name: 'Shauna', 
            degree: 'Conservation Science', 
            powerFuel() { console.log('The tank is full!') } 
            }
        }
    }; 
    // for...in
    for (let crewMember in spaceship.crew) {
      console.log(`${crewMember}: ${spaceship.crew[crewMember].name}`)
    };

Our `for...in` will iterate through each element of the `spaceship.crew`object. In each iteration, the variable `crewMember` is set to one of `spaceship.crew`'s keys, enabling us to log a list of crew members' role and `name`.

Objects Review:

- Objects store collections of *key-value* pairs.
- Each key-value pair is a property—when a property is a function it is known as a method.
- An object literal is composed of comma-separated key-value pairs surrounded by curly braces.
- You can access, add or edit a property within an object by using dot notation or bracket notation.
- We can add methods to our object literals using key-value syntax with anonymous function expressions as values or by using the new ES6 method syntax.
- We can navigate complex, nested objects by chaining operators.
- Objects are mutable—we can change their properties even when they're declared with `const`.
- Objects are passed by reference— when we make changes to an object passed into a function, those changes are permanent.
- We can iterate through objects using the `For...in` syntax.

## Advanced Objects Introduction

- Objects in JavaScript are containers that store data and functionality. In this lesson, we will build upon the fundamentals of creating objects and explore some advanced concepts.
- Objects are collections of related data and functionality. We store that functionality in methods on our objects:

    const goat = {
      dietType: 'herbivore',
      makeSound() {
        console.log('baaa');
      }
    };

In our `goat` object we have a `.makeSound()` method. We can invoke the `.makeSound()` method on `goat`.

    goat.makeSound(); // Prints baaa

Nice, we have a `goat` object that can print `baaa` to the console. Everything seems to be working fine. What if we wanted to add a new method to our `goat` object called `.diet()` that prints the `goat`'s `dietType`?

    const goat = {
      dietType: 'herbivore',
      makeSound() {
        console.log('baaa');
      },
      diet() {
        console.log(dietType);
      }
    };
    goat.diet(); 
    // Output will be "ReferenceError: dietType is not defined"

That's strange, why is `dietType` not defined even though it's a property of `goat`? That's because inside the scope of the `.diet()` method, we don't automatically have access to other properties of the `goat` object.

Here's where the `this` keyword comes to the rescue. If we change the `.diet()` method to use the `this`, the `.diet()` works! :

    const goat = {
      dietType: 'herbivore',
      makeSound() {
        console.log('baaa');
      },
      diet() {
        console.log(this.dietType);
      }
    };
    
    goat.diet(); 
    // Output: herbivore

The `this` keyword references the *calling object* which provides access to the calling object's properties. In the example above, the calling object is `goat` and by using `this` we're accessing the `goat` object itself, and then the `dietType` property of `goat` by using property dot notation.

- If we use the `this` keyword in a method then the value of `this` is the calling object. However, it becomes a bit more complicated when we start using arrow functions for methods. Take a look at the example below:

    const goat = {
      dietType: 'herbivore',
      makeSound() {
        console.log('baaa');
      },
      diet: () => {
        console.log(this.dietType);
      }
    };
    
    goat.diet(); // Prints undefined

In the comment, you can see that `goat.diet()` would log `undefined`. So what happened? Notice that in the `.diet()` is defined using an arrow function.

Arrow functions inherently *bind*, or tie, an already defined `this` value to the function itself that is NOT the calling object. In the code snippet above, the value of `this` is the *global object*, or an object that exists in the global scope, which doesn't have a `dietType` property and therefore returns `undefined`.

- Accessing and updating properties is fundamental in working with objects. However, there are cases in which we don't want other code simply accessing and updating an object's properties. When discussing *privacy* in objects, we define it as the idea that only certain properties should be mutable or able to change in value.

Certain languages have privacy built-in for objects, but JavaScript does not have this feature. Rather, JavaScript developers follow naming conventions that signal to other developers how to interact with a property. One common convention is to place an underscore `_` before the name of a property to mean that the property should not be altered. Here's an example of using `_` to prepend a property.

    const bankAccount = {
      _amount: 1000
    }

In the example above, the `_amount` is not intended to be directly manipulated.

Even so, it is still possible to reassign `_amount`:

    bankAccount._amount = 1000000;

In later exercises, we'll cover the use of methods called *getters* and *setters*. Both methods are used to respect the intention of properties prepended, or began, with `_`. Getters can return the value of internal properties and setters can safely reassign property values.

- *Getters* are methods that get and return the internal properties of an object. But they can do more than just retrieve the value of a property! Let's take a look at a getter method:

    const person = {
      _firstName: 'John',
      _lastName: 'Doe',
      get fullName() {
        if (this._firstName && this._lastName){
          return `${this._firstName} ${this._lastName}`;
        } else {
          return 'Missing a first name or a last name.';
        }
      }
    }
    
    // To call the getter method: 
    person.fullName; // 'John Doe'

Notice that in the getter method above:

- We use the `get` keyword followed by a function.
- We use an `if...else` conditional to check if both `_firstName` and `_lastName` exist (by making sure they both return truthy values) and then return a different value depending on the result.
- We can access the calling object's internal properties using `this`. In `fullName`, we're accessing both `this._firstName` and `this._lastName`.
- In the last line we call `fullName` on `person`. In general, getter methods do not need to be called with a set of parentheses. Syntactically, it looks like we're accessing a property.

Now that we've gone over syntax, let's discuss what some notable advantages of using a getter method:

- Getters can perform an action on the data when getting a property.
- Getters can return different values using conditionals.
- In a getter, we can access the properties of the calling object using `this`.
- The functionality of our code is easier for other developers to understand.

- Along with getter methods, we can also create *setter* methods which reassign values of existing properties within an object. Let's see an example of a setter method:

    const person = {
      _age: 37,
      set age(newAge){
        if (typeof newAge === 'number'){
          this._age = newAge;
        } else {
          console.log('You must assign a number to age');
        }
      }
    };

Notice that in the example above:

- We can perform a check for what value is being assigned to `this._age`.
- When we use the setter method, only values that are numbers will reassign `this._age`
- There are different outputs depending on what values are used to reassign `this._age`.

Then to use the setter method:

    person.age = 40;
    console.log(person._age); // Logs: 40
    person.age = '40'; // Logs: You must assign a number to age

Setter methods like `age` do not need to be called with a set of parentheses. Syntactically, it looks like we're reassigning the value of a property.

Like getter methods, there are similar advantages to using setter methods that include checking input, performing actions on properties, and displaying a clear intention for how the object is supposed to be used. Nonetheless, even with a setter method, it is still possible to directly reassign properties. For example, in the example above, we can still set `._age` directly:

    person._age = 'forty-five'
    console.log(person._age); // Prints forty-five

- ES6 introduced some new shortcuts for assigning properties to variables known as *destructuring*.

In the previous exercise, we created a factory function that helped us create objects. We had to assign each property a key and value even though the key name was the same as the parameter name we assigned to it. To remind ourselves, here's a truncated version of the factory function:

    const monsterFactory = (name, age) => {
      return { 
        name: name,
        age: age
      }
    };

Imagine if we had to include more properties, that process would quickly become tedious! But we can use a destructuring technique, called *property value shorthand*, to save ourselves some keystrokes. The example below works exactly like the example above:

    const monsterFactory = (name, age) => {
      return { 
        name,
        age 
      }
    };

Notice that we don't have to repeat ourselves for property assignments!

- In the previous exercises we've been creating instances of objects that have their own methods. But, we can also take advantage of built-in methods for Objects!

For example, we have access to object instance methods like: `.hasOwnProperty()`, `.valueOf()`, and many more! Practice your documentation reading skills and check out: [MDN's object instance documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object#Methods).

There are also useful Object class methods such as `Object.assign()`, `Object.entries()`, and `Object.keys()` just to name a few. For a comprehensive list, browse: [MDN's object instance documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object#Methods_of_the_Object_constructor).

Advanced Objects Review:

- The object that a method belongs to is called the *calling object*.
- The `this` keyword refers the calling object and can be used to access properties of the calling object.
- Methods do not automatically have access to other internal properties of the calling object.
- The value of `this` depends on where the `this` is being accessed from.
- We cannot use arrow functions as methods if we want to access other internal properties.
- JavaScript objects do not have built-in privacy, rather there are conventions to follow to notify other developers about the intent of the code.
- The usage of an underscore before a property name means that the original developer did not intend for that property to be directly changed.
- Setters and getter methods allow for more detailed ways of accessing and assigning properties.
- Factory functions allow us to create object instances quickly and repeatedly.
- There are different ways to use object destructuring: one way is the property value shorthand and another is destructured assignment.
- As with any concept, it is a good skill to learn how to use the documentation with objects!