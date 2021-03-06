# JAVASCRIPT BASICS (INCLUDING ES6)

These notes cover modern Javascript up to and including ES2015 aka ES6. More detail on [ECMA Script](https://en.wikipedia.org/wiki/ECMAScript) 

### Web and Javascript Tools
  | Name                                                                     | Description                                            |
  | -------------------------------------------------------------------------|--------------------------------------------------------|
  | [lodash](https://lodash.com/)                                            | Modern JS utility library for utilites/performance     |
  | [npm](https://www.npmjs.com/)                                            | NodeJS Package Manager                                 |
  | [Yarn](https://yarnpkg.com/)                                             | Package manager                                        |
  | [Jest](https://jestjs.io/)                                               | Preferred testing framework                            |
  | [TypeScript](https://www.typescriptlang.org/)                            | Typescript (TS) adds optional static typing            |
  | [Flow](https://flow.org/)                                                | A static type checker for javascript                   |
  | [Gulp](https://gulpjs.com/)                                              | Task/pipeline runner used for build                    |
  | [Webpack](https://webpack.js.org/)                                       | Module bundler and packaging for browser               |
  | [Babel](https://babeljs.io/)                                             | Compiler / transpiler                                  |
  | [Bootstrap](https://getbootstrap.com/)                                   | CSS framework for responsive web                       |
  | [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)  | Fetch API for interacting with REST endpoints          |
  | [Axios](https://github.com/axios/axios)                                  | Promise based HTTP client for the browser and node.js  |
  | [Materialize](https://materializecss.com/)                               | A modern responsive front-end/CSS framework            | 
<hr>


### Variables & Scope
- JavaScript is a **weakly typed** language. It has a notion of types, but it's relaxed about them, and can treat values somewhat arbitrarily. The stronger the typing system is — the stricter the rules are. (Static typing can be used with **Typescript** and **Flow**)
- **Variable Declaration var vs let** 
   - `var` :  function or global scope if outside function 
   - `let` : block scope (can be updated but not redeclared) 
   - `const` : immutable constant (but obviously a `Map` declared as a `const` can still be mutated)
   -  [Opinion: Should we never use var?](#https://dev.to/johnwolfe820/should-you-never-truly-use-var-bdi)
   
- **Primitive Types** is data that is not an object, has no methods and represented directly at the lowest level of the language implementation. All primitives are immutable, i.e., they cannot be altered. It is important not to confuse a primitive itself with a variable assigned a primitive value. The variable may be reassigned a new value, but the existing value cannot be changed in the ways that objects, arrays, and functions can be altered. The six types are:    
    - `undefined : typeof instance === "undefined"` (all variables are undefined by default)
    - `Boolean : typeof instance === "boolean"`
    - `Number : typeof instance === "number"` (this includes decimal, floats etc.)
    - `String : typeof instance === "string"`
    - `BigInt : typeof instance === "bigint"`
    - `Symbol : typeof instance === "symbol"` (ES6)
    - `null` is seemingly primitive but is a special case (for every Object: and any structured type is derived from null by the *Prototype Chain*.) 
        
- **Reference Types** are held on the heap and have methods. Examples are: 
    - `Array`, Object Literals, functions, `Date` 
- **falsy** is a term used in JavaScript type comparison and conversion. Falsy values in JavaScript translate to the Boolean false when used in type comparisons. Examples of falsy values are null, undefined, 0, and the Boolean false.
- [Explaining Value vs. Reference in Javascript](https://codeburst.io/explaining-value-vs-reference-in-javascript-647a975e12a0)
- Why is `NaN` not a number? (`NaN` is defined as a numeric type, but it’s not a real number. NaN is result of some mathematical operations that can’t be quantified as a number)
  - The `isNaN()` function determines whether a value is NaN or not. Note: coercion inside the isNaN function has interesting rules; you may alternatively want to use `Number.isNaN()`
- **Objects Literals** are comma-separated list of name-value pairs inside of curly braces; values can be properties and functions. All members of an object literal in JavaScript, both properties and functions, are public. Private members can only be inside a function. You cannot copy an object literal without manually copying all the values.   
- More detail on JavaScript's [data types and data structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures) and on JS' [memory lifecycle](https://blog.alexdevero.com/memory-life-cycle-heap-stack-javascript)    
- **Function Scope** is created inside functions. When a function is declared, a new scope block is created inside body of that function. A `var` declared inside the new function scope cannot be accessed from parent scope, however, the function scope has access to variables in the parent scope. When a variable is created with function scope, it's declaration automatically gets hoisted to the top of the scope. 
- **Type Coercion** occurs because JS has weak types. We can explicitly conver these tpyes or sometimes will convert one type to another

  <pre>
     let dateAsString = String(new Date());  //explicit converstion
     let arryAsString = String([1,2,3,4]);
     let numbAsString = (5).toString();
     console.log(typeof dateAsString);  //outputs string
     val n = Number('5'); //explicit conversion of string to number
     console.log(n.toFixed(2));  //outputs 5.00
     
     const v1 = '5';
     const v2 = 6;
     console.log(v1 + v2); //outputs 56 - type coercion occurs as v2 gets coerced into a string      
  </pre>

- Difference between `==` and `===` (when in doubt always use triple equals). See [Double Equals vs. Triple Equals](#https://codeburst.io/javascript-double-equals-vs-triple-equals-61d4ce5a121a)
- **Hoisting** means that the interpreter moves the instantiation of an entity to the top of the scope it was declared in, regardless of where in the scope block it is defined. Functions and variables declared using var are hoisted in JavaScript; that is, a function or a variable can be used before it has been declared. When a variable is created with function scope, it's declaration automatically gets hoisted to the top of that scope (i.e. the interpreter moves the instantiation of an entity to the top of the scope it was declared in, regardless of where in the scope block it is defined.) Functions and variables declared using `var` are hoisted in JavaScript so a function or a variable can be used before it has been declared.
- **Temporal Dead Zone (TDZ)** is the period between when a scope is entered and when a variable is declared. Variables that are added are not hoisted and are subject to the TDZ. If variable is accessed inside the TDZ, then a runtime error will be thrown.


### Mathematical functions
- JS has mathematical constants: `Math.PI`, `Math.E`
- Rounding can be done via `Math.round(x)` and `Math.ceil(x)` (rounds up) and `Math.floor(x)`' (rounds down)
- `Math.sqrt(x)` provides square root, `Maths.abs(x)` (absolute value), `Math.pow(x,x)` (power function = x^y)
- `Math.min(x,y,z...)` (take minimum of any series numbers), `Math.max(x,y,z...)` (take maximum of any series numbers)
- `Math.random()` generates random decimal numbers between 0 and 1 (so to get between 1 and 20 use `Math.floor(Math.random() * 20 + 1))` and `substring(x,y)`
- `Math.isFinite()` to check number is finite 

### String functions
- Before ES6, Strings can be appended using `+` and `+=`
- String escaping is done via backslash
- The `concat` method can be used to concatenate strings e.g. `firstName.concat(' ',lastName)`;
- String provides `toUpperCase()` and `toLowerCase()`
- Strings can also be treated like arrays so we can use `indexOf('x)`, `lasIndexOf('x)` and `charAt(0)`
- Other useful array-type methods on strings are 
  - `slice(0,4)` (takes first 4 chars) or `slice(-4)` (takes last 4 chars)
  - `split(',')` (splits a string by a token)
  - `replace('foo','bar')` (replaces all occurences of foo with bar)
  - `includes('foo')` (returns a boolean value if the supplied string occurs)
- ES6 introduces `padStart()` and `padEnd()` which add specific characters to existing string. You specify the amount of characters these methods should add through a parameter called targetLength. Note this is not the length in the terms of the number of characters you want to add but is the *whole* length of string you want to change. 
- The `eval()` method evaluates javascript within a string

### Adding And Removing From Arrays Without Mutation
- There are two ways to add to an array without mutating the original array: `concat` and using the spread operator `...`
  
  <pre>
     //ES5 style using prototype
     ShoppingList.prototype.addItem = function(item) {    
       this.groceries = this.groceries.concat([item]);
     }
     
     //ES6 class method
     addItem(item){  
       this.groceries = [...this.groceries, item];
     }
  </pre>
  
- Here is the equivalent for remove  
     
  <pre>   
     //ES5 style using prototype
     ShoppingList.prototype.removeItem = function(item){      
       this.groceries = this.groceries.filter(function(grocery){
           return item !== grocery;
         });
     }
     
     //ES6 style with arrow function
     remove(item) {    
       this.groceries = this.groceries.filter( (grocery) => item != grocery); 
     }
  </pre> 

### String Template Literals (ES6)
- ES6 introduce template literals or template strings. Here we can use `${foo}` for expressions (so variables, functions or, say an expression using the ternary operator). New lines will be included in the output (so we don't need to escape line breaks.) To escape a template literal, simply use a backslash.

  <pre>
    console.log(`Template literals are ${ example }`);
    console.log(`${a} + ${b} is equal to ${a + b}`);
  </pre>   

- You can also *nest* template literals:

  <pre>
    const p = `Learning ${ `Professional ${ javascriptOrCPlusPlus() }` }`
  </pre>

-  **Tag functions** allow you to parse template literals with a function; these functions take a string array and then arguments

  <pre>
    function myTag(strings, personExp, ageExp) { ...}
    let output = myTag`That ${ person } is a ${ age }`;
  </pre>

Special property `raw` is available for the first argument of a tagged template. This returns array that contains the raw, unescaped, versions of each part of the split template literal.

### Arrays and Array Methods
- Arrays are widely use in javascript and can be of fixed or mixed types

  <pre>
    const numbers = [1,2,3,4];
    const numbers = new Array[1,2,3,4];   //using Array constructor
    const mixed = [undefined, 1, 'red', new Date(), null, {a:1, b:2}];  //a mixed array
  </pre>

- `Array.isArray(x)` is a useful method to check if something is an array (good when working with DOM because a node list, for example, is not actually an array)
- Arrays are not immutable so we can say `numbers[2] = 100` and we can use `indexOf(100)` to find the first element in an array
- You can add on to the end of an array using `push(x)` and to the front using `unshift(x)`
- To remove from the end use `pop()` and use `shift()` to remove from the front
- You can splices values using `splice(x,y)` to slice from position x to position y
- You can also `sort()`, `reverse()` arrays and concatenate arrays using `concat(otherArray)`
- Note that can provide a function to `sort(fn)` which acts as a comparator to work out how to sort
- The `find(f)` method takes a predicate function and returns element matching the function 
  - e.g `f = function under50(x){ return x < 50; })`
- ES6 introduces `includes()` which provides a fast way to find if an array contains specific item, or value (so no iteration is necessary.) You can also specify at which index should includes() start to look for that value or item. In that case, includes() method will not start from the beginning of the array, which is the default. Instead, it will start from the index you specified and ignore all values or items that exist in the array before this index.

### Object Literals
- Object literals are widely used in JS and can comprise properties and methods (when a function is an object literal it is called a method):
- **Gotcha!** Note that object literals looks like JSON but the keys/values are not double-quoted like JSON     
    <pre>
      let person = { 
         name: 'John', 
         lastname: 'Smith' 
         age: 50,
         address: {
           city: 'London',
           postcode: 'W1 1BT'
         },
         hobbies: ['fishing','cinema'],
         getBirthYear(): {
            //we need to use 'this' here to refer to the scope
            return new Date().getFullYear() - this.age  
         }
      };
      
      console.log(person.name);
      console.log(person.hobbies[1]); //cinema
    </pre>

- We can also have arrays of object literals 

  <pre>
    const people = [
     {name: 'Mike', age: 30},
     {name: 'Dave', age: 45}
    ];
    
    for(let i =0; i < people.length; i++){
      console.log(people[i].name);
    }
  </pre>

- ES6 provides **Object Literal Enhancements** (i.e. some syntactic sugar to allow us to easily collate properties into an object literal): 
  
  <pre>
      const pizza = {
         name: 'Pepperoni',
         price: 12
      }
      const toppings = ['red chilli','pepperoni'];
      const orderES5 = {pizza: pizza, toppings: toppings};  
      const orderES6 = { pizza, toppings};  
  </pre>

- Here's an example grouping parameters of a function into an object literal comparing the old ES6 and new ES6 way: 
 
  <pre>
    function getPersonES5( name, age, height ) { 
     return { name: name, age: age, height: height }; 
    }
  
    function getPersonES6( name, age, height ) { 
      return { name, age, height};  //we no longer need the names
    }
  </pre>

- And also including function declarations...

  <pre>   
    function getPersonES5( name, age, height ) { 
       return { name: name, height: height, getAge: function(){ return age; } }; 
    }
  
    function getPersionES6( name, age, height ) { 
       return { name, height, getAge() { return age; } };   
    }
  </pre>

- ES6 introduced [Object.assign()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign) which copies all enumerable own properties from one or more source objects to a target object and returns the target object.

### Dates and Times
- A new Date() will always will create a new date object with current date/time. 
- There are also `getDay()`,`getFullYear()`,`getMonth()` etc. and `getTime()` to get current timestamp in ms.
- Likewise there are equivalent setter method for the above
  <pre>
     val today = new Date(); 
     val fixed1 = new Date('9-10-1981 10:25:00');
     val fixed1 = new Date('9/10/1981');
     val month = fixed1.getMonth(); //this returns 8 as it is zero-based
  </pre>


### Comparison and Logical Operators
- Use `=` and `==` for equality / equality but this doesn't test type!
- Use '===' and `!==` to test for equality and type
- JS has standard `if (foo) { ... } else if (bar){ ... } else {... }` semantics - curly brackets are optional but are advisable
- JS also logic operators: `&&` (and), `||` (or) and `!` (not)
- JS also has ternary operator (`?`) for conditions e.g. `let voteable = (age < 18) ? "Too young":"Old enough";`

### Switches
- JS has C-style `switch` statements for handling multiple cases
<pre>
    switch(new Date().getDay()){
      case 0: 
          day = 'Sunday';
          break;
      case 6:
          day = 'Saturday';
          break;
      case default;
          day = 'A weekday';
    }
</pre>

### Functions Declarations and Default Parameters
- Functions are declared  using the `function` keyword and the name of the function can be returned getting [`.name` property](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/name): 
  <pre>
    let f = function greet(name){ 
       console.log(`hello ${name}`);
    }
    console.log(f.name);
  </pre> 
- You aren't obliged to pass parameters to any function and in this case they will be undefined:
- **Default function parameters** (ES6) allow named parameters to be initialized with default values if no value or undefined is passed:

  <pre>
    function multiply(a, b = 1) {
      return a * b;
    }
    console.log(multiply(5, 2));// expected output: 10
    console.log(multiply(5));  // expected output: 5
  </pre>
  
- **Function expressions** are usually defined anonymously (but can take a name). Expressions have benefits for hoisting and closures. 
  <pre>
    const square = function(x) {
      return x * x;
    }
  </pre>

- Functions can also be put inside objects (then known as methods):
  <pre>
    const todo = {
      add:  function() {
        console.log(`Add a todo`);
      },
      edit: function(id) {
        console.log(`Editing a todo with id ${id}`);
      }
    }
    
    //we can also add methods outside the the object
    todo.delete = function(id) {
        console.log(`Deleting a todo with id ${id}`);
    }
    
    todo.add();
    todo.edit(22);
  </pre>

- JS also has [IFFEs](#http://adripofjavascript.com/blog/drips/an-introduction-to-iffes-immediately-invoked-function-expressions.html) which are **immediately invoked function expressions**
  <pre>
    var foo = "foo";
    
    (function (innerFoo) {
        // Outputs: "foo"
        console.log(innerFoo);
    })(foo);
  </pre>
        
- **Functions: `Bind`, `Apply`, `Call`**
    - `call()` and `apply()` are very similar—they invoke a function with a specified `this` context, and optional arguments. The only difference between them is that call requires the arguments to be passed in one-by-one, and apply takes the arguments as an array.
    - `bind()` allows you to set the `this` value now while allowing you to execute the function in the future, because it returns a new function object.

- Comparing  function objects, function calls, call/apply and bind:

     | *Type*                       |*Time of Execution*| *Time of* `this` *binding* |
     |------------------------------|-------------------|----------------------------|
     | function object (f)          |      future       |   future                   |
     | function call   (f)          |       now         |     now                    |
     | `f.call()` and `f.apply()`   |       now         |     now                    |
     |      `f.bind()`              |      future       |     now                    |
    


### Loops
- JS has standard `for` (when known number of iterations), `while`(when unknown number of iterations) and `do`(when always do at least once) constructs

  <pre>
    for ( let i =0; i < 10; i++ ){   //standard for loop
      if (i == 2){
        console.log(`${i} is my favourite number`);
        continue;
      }
      if (i == 5){
         break;
      }
      console.log(i);   
    }  
    
    while(i < 10){                //basic while-loop
      console.log(i);
      i++;
    }
    
    do {                          //basic do-while loop
      console.log(i);
      i++;
    }
    while(i < 10);
  </pre>

- JS also has `forEach` which takes in an anonymous function and is simpler/cleaner for iteration:
 <pre>
    const cars = ['Ford','Toyota','Lexus'];
    
    //we can also use forEach with the index and the entire array 
    //   e.g. cars.forEach(function(car, i,cars ){...}
     
    cars.forEach(function(car){
       console.log(car);
    });
 </pre>
 
- JS also has `map` function
<pre>
    const brands = [{id: 1, brand: 'Ford'},{id: 2, brand: 'Toyota'},{id: 3, brand: 'Lexus'}];
    brands.forEach(function(brand){
       return brand.id;
    });
 </pre>
 
- JS also has `for-in` function which is ideal for key value pairs and object literals:
<pre>
    const brand = {id: 1, brand: 'Ford'};
    for(x in brand){
       console.log(`${x} : ${brand[x]}`);  
    };
    
    //outputs
    //id: 1 
    //brand: Ford
 </pre>
 
- JS also has `for-of` which iterates over values that are inside the object (whereas for-in iterates over the enumerable properties of an object). This cannot be used with object literals.
  <pre>
      const forOfExample = ['bazz', true, 21]
      
      for (let prop of forOfExample) {
        // Output all values stored inside the array
        console.log(prop)
      }
  </pre>

### Maps
- Maps provided a way of storing key-value pairs and can use *any* type  (and mixed types) for keys and values
- Map has methods `set(x,y)` and `get()`, `values()` and `keyss()` and alsso `size()` for determining the entry count
  
  <pre>
    const map1 = new Map();
    const key1 = 'some string',key2 = {}, key3 = function() {};
  
    // Set map values by key
    map1.set(key1, 'Value of key1');
    map1.set(key2, 'Value of key2');
    map1.set(key3, 'Value of key3');
  
    // Get values by key
    console.log(map1.get(key1), map1.get(key2), map1.get(key3));
  </pre>
  
- We can iterator over maps using `for-of` and `forEach` or just iterate of `keys()` or `values()` 

  <pre>
      for(let [key, value] of map1) {           // for...of to get keys and values
         console.log(`${key} = ${value}`);
      }
      
      for(let key of map1.keys()) {             // Iterate keys only
         console.log(key);
      }
      
      for(let value of map1.values()) {         // Iterate values only
        console.log(value);
      }
      
      map1.forEach(function(value, key){        // Loop with forEach
         console.log(`${key} = ${value}`);
      });
  </pre>
  
- We can also easily *convert a map to an array* using `Array.from()`

   <pre>
     const keyValArr = Array.from(map1);        // Create an array of the key value pairs
     console.log(keyValArr);
     
     const valArr = Array.from(map1.values());  // Create an array of the values
     console.log(valArr);
     
     const keyArr = Array.from(map1.keys());    // Create an array of the keys
     console.log(keyArr);
   </pre>
  
### Sets
- a JS `Set` store unique value of any type and has `entries()`, `has(x)`, `delete(x)` and `size()` methods: 
  
  <pre>
     set1.add(100);
     set1.add('A string');
     set1.add({name: 'John'});
     set1.add(true);
   
     const set2 = new Set([1, true, 'string']);  //construct from an array
     console.log(set2);
     console.log(set1.has(100));
  </pre>
       
- We can also convert an array to set:
     
  <pre>
     const setArr = Array.from(set1);           // Convert array to set
  </pre>  
  
- We can iterate over sets using `for-of` and `forEach`.

  <pre>       
     for(let item of set1) {
        console.log(item);
     }
    
     set1.forEach((value) => {
        console.log(value);
     });
     
     
  </pre>
  
  
### The Window Object
- Window is the global object/environment in client-side javascript
- The `window.document` give us the Document Object Model (DOM)
- We an use `window.alert('hello world)` (or we can just use `alert`) and we can use `prompt` to take an input and `confirm` for confirmations (but better use to Bootstrap for this)
- We can get the `innerHeight` and `outerHeight` and `innerWidth` and `innerHeight` of the window 
- We can get scrollpoints using `scrollY` and `scrollX` (used for animations with scrolling)
- We can also get `window.location` (or `window.location.hostname` or `window.location.port`) to get current location and `window.history` to get browser history (and `window.history.go(-2)` to go back 2 in history)
- We can use `window.location.search` to get query parameters
- We can use `window.location.href` to redirect, `window.location.reload` to reload and   
- We can use `window.navigator` which is to do with the browser and has geolocation, browser version, user's OS etc

### Event Listeners
- A very common thing to do with DOM objects is to add event listener using [`addEventListener`](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener) method which sets up a function that will be called whenever the specified event is delivered to the target. Common targets are `Element`, `Document`, and `Window`, but the target may be any object that supports events (such as `XMLHttpRequest`). The method takes 2 parameters (type and listener function) and optional parameters:
  - `type`: A case-sensitive string representing the event type to listen for.
  - `listener`: The object that receives a notification (an object that implements the Event interface) when an event of the specified type occurs. This must be an object implementing the EventListener interface, or a JavaScript function. See The event listener callback for details on the callback itself.
  - `options` (Optional) : An options object specifies characteristics about the event listener. The available options are:
    - `capture`: boolean indicating that events of this type will be dispatched to the registered listener before being dispatched to any EventTarget beneath it in the DOM tree.
    - `once`: boolean indicating that the listener should be invoked at most once after being added. If true, the listener would be automatically removed when invoked.
    - `passive`: boolean that, if true, indicates that the function specified by listener will never call preventDefault(). If a passive listener does call preventDefault(), the user agent will do nothing other than generate a console warning. See Improving scrolling performance with passive listeners to learn more.
    - `mozSystemGroup`: boolean indicating that the listener should be added to the system group. Available only in code running in XBL or in the chrome of the Firefox browser.
    - `useCapture` (Optional) - boolean indicating whether events of this type will be dispatched to the registered listener before being dispatched to any EventTarget beneath it in the DOM tree. Events that are bubbling upward through the tree will not trigger a listener designated to use capture. Event bubbling and capturing are two ways of propagating events that occur in an element that is nested within another element, when both elements have registered a handle for that event. The event propagation mode determines the order in which elements receive the event. See DOM Level 3 Events and JavaScript Event order for a detailed explanation. If not specified, useCapture defaults to false.
  
  <pre>
    function handleClick(e){
      conole.log(this);  //this refers to elem
    }
    const elem = document.querySelector('.click');
    elem.addEventListener('click', handleClick, false);
  </pre>                           

### Try-catch-finally
- The `try` `catch` semantics allows us to catch errors and handle them gracefully. Be aware that anything in the `finally` block will always run
  
  <pre>
    const user = {email: 'jdoe@gmail.com'};
    
    try {
      if(!user.name) {
        throw new SyntaxError('User has no name');
      }
    } catch(e) {
      console.log(`User Error: ${e.message}`);
    } finally {
      console.log('Finally runs reguardless of result...');
    }
    
    console.log('Execution continues...');
  </pre>

### Regex
- JS has standard [regular expressions](https://en.wikipedia.org/wiki/Regular_expression) and can be tested at [Regex101](https://regex101.com/)

  - `exec()` executes a search for a match and returns a result array or null
  - `match()` / `matchAll()` works the other way around to exec in so far as it is called on the string being tested abd the regex is passed in to the function 
  - `test()` tests the expression for a match returning a boolean
  - `search()` returns the index of the first match or -1 if not found
  - `replace()` will return new srtring replacing all occurences of the match (pass in the regex and the replacment)   
  - `source` property returns a String containing the source text of the regexp object, and it doesn't contain the two forward slashes on both sides and any flags.
  - `compile()` recompiles the expression

  <pre>
      let re1 = /hello/;
      let re2 = /hello/i; // i =  case insensitive
      let re3 = /hello/g; // Global search
        
      // exec() - Return result in an array or null
      const result1 = re.exec('hello world');
      
      // test() - Returns true or false
      const result2 = re.test('Hello');
     
      // match() - Return result array or null
      const str = 'Hello There';
      const result = str.match(re);
      
      // search() - Returns index of the first match if not found returns -1
      const str = 'Brad Hello There';
      const result = str.search(re);  
  </pre>
  
  
- **Regex: Metasymbols**
 
  - `^` must *start* with e.g. `/^h/i`  = must start with h
  - `$` must *end* with e.g. `/world$/i` = must end with
  - `.` match any *one* character e.g. `/^h.llo/i`
  - `*` match any *any* character 0 or more times  e.g. `/^h*llo/i` (which would match with 'heexllo')  
  - `?` match an *optional* character e.g. /`^gr?a?ey/i` (which would match either spelling of gray or gry)
  - `\` escape characters

- **Regex: Character sets**

- `[]` matches *anything* contained in characters in the bracketed set e.g. `/gr[ae]y/i` (which would match either spelling of gray or gry)
- `[^]` matches *anything except* characters in the bracketed set e.g. `/[^G]ray/i` (which would match with Xray but not Gray)      
- `[A-Z]` matches *anything in the range* defined by the bracketed (including case) set e.g. `/[^A-Z]ray/i`(which would match with Xray, Gray and Fray)
- `[A-z]` matches *any letter* (ignoring case) set e.g. `/[^A-Z]ray/i`(which would match with Xray, Gray and Fray)
- `[0-9]` matches any digit

- **Regex: Quantifiers and Grouping**

  - `{x}` matches a specified number of occurences e.g. `l{2}` specifies 2 l's so `/H?l{2}o/i` matches hello but not halo
  - `{x,y}` matches a  specified range of number of occurences
  - `()` matches a group of characters e.g. `/([0-9]x{3})/` matches 2x1x5x or 2x2x2x and 1x2x3x4x but not 1x2x whereas `/^([0-9]x{3})/` matches exactly 3 times

- **Regex: Shorthand Character Classes**

  - `/\w/` any alphanumeric character (letter,number or underscore)
  - `/\w+/` all of the word characters (letter,number or underscore)
  - `/\W+/` all of the non-word characters (anything but letter,number or underscore)
  - `/\d/` any digit
  - `/\D/` any non-digit
  - `/\s/` any whitespace (tab, cr and space)
  - `/\S/` any non-whitespace (any but tab, cr and space)
  - `/\b/` word boundary e.g. `/Hell\b/i` finds the word hell not hello  
  - `/\x(?=y)/` conditional assertion (match only x if followed by) 
  - `/\x(?!y)/` conditional assertion (match only x if *not* followed by)
  
- Example regex function for validating email: 
 
  <pre>
    function validateEmail() {
      const email = document.getElementById('email');
      const re = /^([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})$/;
    
      if(!re.test(email.value)){
        email.classList.add('is-invalid');
      } else {
        email.classList.remove('is-invalid');
      }
    }
  </pre>

### Symbol (ES6)

- A `Symbol` is a JS pritmitive type introduced in ES6. The main feature of a `Symbol` is *uniqueness* so no two symbols can ever be same
- The main purpose of symbols is unique object keys and they are *not inumerable* in `for..in`
- Symbols are also are ignored by JSON.stringify
- Symbols can be used for [metaprogramming](https://www.keithcirkel.co.uk/metaprogramming-in-es6-symbols/) 

  <pre>
    const KEY1 = Symbol();
    const KEY2 = Symbol('sym2');
    
    const myObj = {};
    
    myObj[KEY1] = 'Prop1';
    myObj[KEY2] = 'Prop2';
    myObj.key3 = 'Prop3';
    myObj.key4 = 'Prop4';
    
    // Symbols are ignored by JSON.stringify
    console.log(JSON.stringify({key: 'prop'}));
    console.log(JSON.stringify({[Symbol('sym1')]: 'prop'}));
  </pre>


### Iterables
- An object is iterable if it defines its iteration behavior, such as what values are looped over in a `for...of` construct. 
- Some built-in types, such as `Array` or `Map`, have a default iteration behavior, while other types (such as `Object`) do not. 
- In order to be iterable, an object must implement the `@@iterator` method. This simply means that the object (or one of the objects up its prototype chain) must have a property with a `Symbol.iterator` key. 

  <pre>
    function* createIds() {    //Simple iterator example
      let index = 1;
    
      while(true) {
        yield index++;
      }
    }
    
    const gen = createIds();
    console.log(gen.next().value)
  </pre>
  
- It may be possible to iterate over an iterable more than once, or only once. (It is up to the programmer to know which is the case.) Iterables which can iterate only once (such as a `Generator`) customarily return this from their `@@iterator` method, whereas iterables which can be iterated many times must return a new iterator on each invocation of `@`@iterator`.

<pre>
  function* makeIterator() {
    yield 1;
    yield 2;
  }
    
  const it = makeIterator();
    
  for (const itItem of it) {
     console.log(itItem);
  }
    
  console.log(it[Symbol.iterator]() === it) // true;
    
  // This example show us generator(iterator) is iterable object, which has the @@iterator method return the it (itself), and consequently, the it object can iterate only _once_.
  // If we change it's @@iterator method to a function/generator which returns a new iterator/generator object, (it)can iterate many times
    
  it[Symbol.iterator] = function* () {
    yield 2;
    yield 1;
   };
    //Output is 1, 2, true
</pre>

- For example of an iterator used for iterating through user profiles then see [ProfilesScroller](./js_basics/profilescroller)

### Generators
The `function*` declaration (function keyword followed by asterisk) defines a generator function, which returns a `Generator` object. Generators compute their yielded values on demand, which allows them to efficiently represent sequences that are expensive to compute (or even infinite sequences). The `next()` method also accepts a value, which can be used to modify the internal state of the generator. A value passed to `next()` will be received by `yield` .(A value passed to the first invocation of `next()` is always ignored.) Here is the fibonacci generator using `next(x)` to restart the sequence:
<pre>
   function* fibonacci() {
     let current = 0;
     let next = 1;
     while (true) {
       let reset = yield current;
       [current, next] = [next, next + current];
       if (reset) {
         current = 0;
         next = 1;
       }
    }
  }
</pre>

### Arrow Functions (ES6)
-  Difference between arrow function and normal functions is that they are [**anonymous**](#https://en.wikipedia.org/wiki/Anonymous_function). To write an arrow function, simply omit the function keyword and add =&gt; between the arguments and fn body.
-  If arrow function is returning a **single line of code,** you can omit statement brackets and return
-  Arrow functions follow normal scoping rules, with the exception of the `this` scope. (In basic JavaScript, each function is assigned a scope, that is, the `this` scope.) Arrow functions are not assigned a `this`scope - they inherit their *parent's* `this` scope and cannot have a new `this` scope bound to them*! 
-  Arrow functions have access to the scope of the parent function (i.e. the variables in that scope) but the scope of this cannot be changed in an arrow function. Using the `apply()`, `call()`, or `bind()` function modifiers will NOT change the scope of an arrow function's `this` property.

<pre>
    const fn1 = function( a, b ) { return a + b; }; 
    const fn2 = ( a, b ) => { return a + b; };
    
    // Single argument arrow function 
    arg1 => { /* Do function stuff here */ } 
    
    // Non simple identifier function argument 
    ( arg1 = 10 ) => { /* Do function stuff here */ }
    
    // No arguments passed into the function 
    ( ) => { /* Do fn stuff here */ }
    
    // Arrow function with an object literal in the body 
    ( num1, num2 ) => ( { prop1: num1, prop2: num2 } )
</pre>

### Computed Property Notation (ES6)
- ES6 provides new, efficient way to create property names from variables.  In ES5,  only one way to create a dynamic property whose name is specified by a variable; this is through bracket notation e.g  `obj[ expression ] = 'value'` 
- In ES6, we can use this same type of notation during the object literal's declaration:

  <pre>
     const varName = 'firstName'; 
     const person = { [ varName ] = 'John', lastName: 'Smith' }; 
     console.log( person.firstName ); // Expected output: John
  </pre>

### Destructuring (ES6)
- **Destructuring assignment** is syntax in JavaScript that allows you to unpack values from arrays or properties from objects, and save them into variables.
- **Array Destructuring** allows us to extract multiple array elements and save them into variables. We create an array containing the variable to assign data into, and set it equal to the data array being destructured and values in the array are unpacked and assigned to the variables in the left-hand side array from left to right, one variable per array value. If there's more array items than vars, then remaining items will be discarded and not be destructured. Conversely, if there are more variables than the total number of array elements in the data array, some of the variables will be set to undefined. So *don't unintentionally assume that a variable will contain a value!*

  <pre>
    let names = [ 'John', 'Michael' ]; 
    let [ name1, name2 ] = names; 
    console.log( name1 ); // Expected output: 'John' 
    console.log( name2 ); // Expected output: 'Michael'
  </pre>

- Example of **destructuring assignment**:

  <pre>
    // Destructuring Assignment
    let a, b;
    [a, b] = [100, 200];
    // Rest pattern
    [a, b, c, ...rest] = [100, 200, 300, 400, 500];
    
    ({ a, b } = { a: 100, b: 200, c: 300, d: 400, e: 500 });
    ({ a, b, ...rest} = { a: 100, b: 200, c: 300, d: 400, e: 500 });
  </pre> 

- Example of **array destructuring**:

  <pre>   
    // Array Destructuring
    const people = ['John', 'Beth', 'Mike'];
    const [person1, person2, person3] = people;
    console.log(person1, person2, person3);
    
    // Parse array returned from function
    function getPeople() {
       return ['John', 'Beth', 'Mike'];
    }
    
    let person4, person5, person6;
    [person4, person5, person6] = getPeople();
  </pre> 
     
- Example of **object destructuring** (most common use of destructuring):

  <pre>
    const person = {
      name: 'John Doe',
      age: 32,
      city: 'Miami',
      gender: 'Male'
    }
    
    // Old ES5
    // const name = person.name,
    //       age = person.age,
    //       city = person.city;
    
    // New ES6 Destructuring
    const { name, age, city } = person;
    console.log(name, age, city);

  </pre>

### Rest and Spread Operator (… or 'elipses') for Deep Copy (ES6)
- The operator is used to represent an infinite number of arguments as an array; it is used to allow an iterable object to be expanded into multiple arguments. To identify which is being used, we must look at the item that the argument is being applied to.

  - If applied to an **iterable object** (array, object, and so on), then it is the **spread operator**
  - If applied to **function arguments**, then it is the **rest operator**.

* **Rest Operator**
  - Like the arguments object of a fn (which is array-like object that contains each argument passed into the fn), the rest operator contains a list of fn arguments but has three distinct differences from the arguments object.
  - Rest operator contains only the input parameters that have *not been given a separate formal declaration* in the function expression
  - The arguments object is not an instance of an Array object. The *rest parameter is an instance of an array* so functions like `sort()`, `map()`, and `forEach()` can be applied
  - The arguments object has special functionality that the rest parameter does not have (e.g. the caller property exists on the arguments object.) The rest parameter can be destructured similar to how we destructure an array. Instead of putting a single variable name inside before the ellipses, we can replace it with an

  <pre>
    function fn( num1, num2, ...args ) //rest operator used for args
  </pre>

  - Rest parameter can be destructured (just like an array.) Instead of a single variable name inside before the ellipses, we can replace it with an array of variables to fill:

  <pre>
    function fn( ...[ n1, n2, n3 ] ) { 
    	//destructures indefinite #of function parameters into array args 	
    	//then destructured into 3 vars 
    	console.log( n1, n2, n3 ); 
    }   
    fn( 1, 2 ); // Expected output: 1, 2, undefined
    console.log( n1, n2, n3 );
  </pre>

* **Spread Operator** 
  - The spread operator is typically used to **merge two arrays** without having to use `concat()`. Instead it takes a copy (so **not** passed by reference) and **immutability** is preserved
  - Allows an iterable object such (e.g. an array or string to be expanded into multiple arguments (for function calls), array elements (for array literals), or key-value pairs (for object expressions) so we can expand an array into arguments for creating another array, object, or calling function:

  <pre>
    function fn( n1, n2, n3 ) {
       console.log( n1, n2, n3 );
    }
    const values = \[ 1, 2, 3 \];
    fn( ...values ); // Expected output: 1, 2, 3
    const obj = { firstName: 'Bob', lastName: 'Smith' };
    const { firstName, lastName } = obj;
    console.log( firstName ); // Expected output: 'Bob'
    console.log( lastName ); // Expected output: 'Smith'
  </pre>

  ...the exception to previous rule is if there's a **default value**:

  <pre>
    const obj = { firstName: 'Bob', lastName: 'Smith' }; 
    const { firstName = 'Samantha', middleName = 'Chris' } = obj; 
    console.log( firstName ); // Expected output: 'Bob' 
    console.log( middleName ); // Expected output: 'Chris'
  </pre>

- We can also save the key that's extracted into a **var with a different name** by a*dding a colon and the new variable name after the key name* in the destructuring notation:

  <pre>
    const obj = { firstName: 'Bob', lastName: 'Smith' }; 
    const { firstName: first, lastName } = obj; c
    console.log( first ); // Expected output: 'Bob' 
    console.log( lastName ); // Expected output: 'Smith'
  </pre>
  

### ES6: Classes
- **Classes** were introduced in ES6 as means to expand on prototype-based inheritance by adding some OO concepts; it is syntactic sugar to expand on the existing prototype-based inheritance. Classes can have function constructors; subclasses must call super constructor:
  <pre>
    class House{ 
        constructor(address, garage = false) {
            this.address = address; 
            this.garage = garage;
        } 
    }
    
    
    class Mansion extends House { 
        constructor( address, floors = 3 ) { 
                super( address ); 
                this.floors = floors; 
         }
    }
  </pre>


### Modules ES6
- We use modules to break up javascript into more manageable chucks. We usually use webpack to then bundle up all these modules into a single js file
- To make any module accessible outside that module we must use `export`
  <pre>
    export const PI = 3.1415;                           //export constant
    export function convertDegToRad( degrees ) {        //export function 
        return degrees * PI / (360/2); 
    } 
    export { PI, DEGREES_IN_CIRCLE, convertDegToRad }; 	//export via object
  </pre>
  
- Note that a module can be anything: an object, a function, an object containing functions and even just a string.
- **Pre-ES6** we use `require` to import module (including NPM) 
  <pre>
    require('./mymodule') // bring in a local module which has been export 
    require('express') //bring in an NPM module (so no ./) 
  </pre>

- Modules were officially introduced in ES6 via [import]([import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)) and [export](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export) keywords allowing the contained code to be quickly and easily shared without any code duplication. Use export keyword to expose variables and functions contained in a file. Everything inside an ES6 module is private by default so only way to make anything public is to use the export keyword. Modules can export properties in two ways, via named exports or *default exports*.
-   **Named exports** allow for multiple exports per module. Multiple exports may be useful if you are building a math module that exports many functions and constants.
-   **Default exports** allow for just a single export per model. A single export may be useful if you are building a module that contains a single class.

 - Use the `default` keyword, to **export** the contents of module as a default export. When we default export a module, we can also omit the identifier name of the class, function, or variable we are exporting. Here we export a class and the other exports a function. When we export a default class, the export is not named. When we are importing default export modules, the name of the object we are importing is derived via the module's name.
  <pre>
    //HouseClass.js 
    export default class() { /* Class body goes here */ }   // export class
    
    // myFunction.js export 
    default function() { /* Function body goes here */ }    //export fn
  </pre>

- The `import` keyword allows you to import a module, allowing you to pull any items from that module into the current code file. When we import a module, we start the expression with the import keyword, identify what parts of the module we are going to import then follow that with the `from` keyword, and finally we finish with the path to the module file.

  <pre>
    import { http } from './http';
    import { ui } from './ui';
    
    //now we can use our imported http object
    function getPosts() {
      http.get('http://localhost:3000/posts')
        .then(data => ui.showPosts(data))
        .catch(err => console.log(err));
    }
  </pre>

- The major difference between `require` and `import` is that `require` will automatically scan `node_modules` to find modules, but `import` which comes from ES6 won't
-  **Note:** ES6 modules may not have full support from all browsers versions. You must use a transpiler (e.g. Babel) to run your code on certain platforms. To use an import in the browser, we must use the script tag and set type to module and the src to the file. (If the browser does not support modules, there's a fallback option with the nomodule attribute.) Finally, be careful of **circular dependencies** which cause lots of errors in transpilation!
- For more detail on [using import and export](https://blog.alexdevero.com/import-and-export-statements-javascript)
### Package Managers: NPM vs Yarn
- There are a huge number of javascript libraries which have been packaged for easy download and use via a package manager. (NPM being the first and probably still the most popular package mamager with Yarn arriving later and arguably offering [improvements](https://waverleysoftware.com/blog/yarn-vs-npm/))
- Benefits of Yarn: 
  - Yarn caches all installed packages. Yarn is installing the packages simultaneously, and that is why Yarn is faster than NPM. They both download packages from npm repository. 
  - Yarn generates yarn.lock to lock down the versions of package’s dependencies by default. On the contrary, npm for this purpose offers shrinkwrap CLI command.
  - Yarn won’t work on node.js version 5.10.1
  - Summary: Yarn offers stability, providing lock down versions of installed packages. The speed of modules installing is higher.
  
### Transpilation with Babel
- [Babel](https://en.wikipedia.org/wiki/Babel_(transcompiler)) is the most common transpiler for javascript and is mainly used to convert ECMAScript 2015+ (ES6+) code into a backwards compatible version of JavaScript that can be run by older JavaScript engines. Babel is a popular tool for using the newest features of the JavaScript programming language providing [polyfills](https://en.wikipedia.org/wiki/Polyfill_(programming)0) to provide support for features that are missing entirely from JavaScript environments.
- For a quick start look at [Babel/Webpack Starter](https://github.com/bradtraversy/babel_webpack_starter)  
- To install the Babel cuse the following: 
  - `npm install --save-dev babel-cli`
- After that, the `babel-cli` field will have been added to the `devDependencies` object in the `package.json` file (although this only installed base Babel with no plugins for transpiling):

<pre>
    "devDependencies": {
        "babel-cli": "^6.26.0"
    
    }
</pre>

- To install the plugin to transpile to ECMAScript 2015, use
  - `npm install --save-dev babel-preset-es2015`
- Once this finishes, our `package.json` `file will contain another dependency:

  <pre>
    "devDependencies": {
        "babel-cli": "^6.26.0",
        "babel-preset-es2015": "^6.24.1"
    }
  </pre>

- This installs the ES6 presets. To use these, we must tell Babel to configure itself with these presets. Create a file called `.babelrc` which is Babel's configuration. This is where we tell Babel what presets, plugins etc. Once created, add the following contents to the file:

  <pre>
    { "presets": ["es2015"] }
  </pre>

- Now that Babel has been configured to transpile we need to update our `package.json` file to add a **transpile script** for npm. Add the following lines to your `package.json` file:
  <pre>
    "scripts": {
        "transpile": "babel app.js --out-file app.transpiled.js --source-maps"
    }
  </pre>

- The `scripts` object allows us to run these commands from npm.
- We name the npm script transpile and it will run the command chain babel `app.js --out-file app.transpiled.js --source-maps` where `app.js` is our input file
- The `--out-file` command specifies the output file for compilation. The `app.transpiled.js` is our output file.
- Lastly, `--source-maps` creates a source map file. This file tells the browser which line of transpiled code corresponds to which lines of the original source. This allows us to debug directly in the original source file, that is, `app.js`.
- Now we can transpile by typing `npm run` transpile into the terminal window.
- Use `npm run build` to bundle all the assets 

### Using JSON Sever for Mocking APIs
- The [JSON Server](https://www.npmjs.com/package/json-server) module allows us to create a mock/fake JSON api
- You can add this to npm 'scripts' config in `package.json`
  - e.g. json `json-sever --watch api/mydb.json` will run the json server serving up the file api/mydb.json when we run `npm run json:server`
- If you `POST` to the json server it will also add it to the json!


