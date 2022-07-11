- Unlike most programming languages, the JavaScript language **has no concept of input or output.** It is designed to run as a scripting  language in a host environment, and it is up to the host environment to provide mechanisms for communicating with the outside world.
- # Types
  collapsed:: true
	- Numbers
	  collapsed:: true
		- BigInt
		- Number
			- The Number type is a [double-precision 64-bit binary format IEEE 754 value](https://en.wikipedia.org/wiki/Double_precision_floating-point_format) 
			  (numbers between $-(2^{53} − 1)$ and $2^{53} − 1$ )
			  So the integers usually are not real integers
			  So an _apparent integer_ is in fact _implicitly a float_
				- ```js
				  0.1 + 0.2 == 0.30000000000000004;
				  ```
			- Arithmetic Operators
			- built-in `Math`
			- `parseInt` & `parseFloat`
			- `NaN`
				- `isNaN()`
			- `Infinity`
	- Strings
	  collapsed:: true
		- Strings in JavaScript are sequences of [Unicode characters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#unicode).
		  More accurately, they are sequences of UTF-16 code units; each code unit is represented by a 16-bit number. Each Unicode character is represented by either 1 or 2 code units.
		- `somestring.length`
		- ```js
		  'hello'.charAt(0); // "h"
		  'hello, world'.replace('world', 'mars'); // "hello, mars"
		  'hello'.toUpperCase(); // "HELLO"
		  ```
	- null & undefined
	  collapsed:: true
		- `null`
			- a value that indicates a deliberate non-value (and is only accessible through the  `null`  keyword)
		- `undefined`
			- indicates an uninitialized variable — that is, a value hasn't even been assigned yet.
			  in JavaScript it is possible to declare a variable without assigning a value to it. 
			  If you do this, the variable's type is  `undefined` .  `undefined`  is actually a constant.
	- Boolean
		- `false`
		  collapsed:: true
			- `false`
			- 0
			- `""`
			- `NaN`
			- `null`
			- `undefined`
		- `true`
	- [Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#objects)
	  collapsed:: true
		- [ `Function` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function)
		- [ `Array` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
		- [ `Date` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)
		- [ `RegExp` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp)
- # Variables
  collapsed:: true
	- ## Declaration
		- ### `let`
		  collapsed:: true
			- scope
			  collapsed:: true
				- block-level variables
				  The declared variable is available from the _block_ it is enclosed in.
				- Example:
					- ```js
					  // myLetVariable is *not* visible out here
					  
					  for (let myLetVariable = 0; myLetVariable < 5; myLetVariable++) {
					    // myLetVariable is only visible in here
					  }
					  
					  // myLetVariable is *not* visible out here
					  ```
		- ### `const`
		  collapsed:: true
			- immutability
				- ```js
				  const Pi = 3.14; // variable Pi is set
				  Pi = 1; // will throw an error because you cannot change a constant variable.
				  ```
			- scope:
				- available from the _block_ it is declared in
				-
		- ### `var`
		  collapsed:: true
			- scope
			  available from the _function_ it is declared in.
			- Example
				- ```js
				  // myVarVariable *is* visible out here
				  
				  for (var myVarVariable = 0; myVarVariable < 5; myVarVariable++) {
				    // myVarVariable is visible to the whole function
				  }
				  
				  // myVarVariable *is* visible out here
				  ```
		- If you declare a variable without assigning any value to it, its type is  `undefined` .
	-
- # Operators
  collapsed:: true
	- Logic Operators
		- `&&`
		- `||`
		- `!`
		- Comparison
		  collapsed:: true
			- `==` & `===`
				- `==` with type coercion
					- ```js
					  123 == '123'; // true
					  1 == true; // true
					  ```
				- `===` without type coercion
					- ```js
					  123 === '123'; // false
					  1 === true;    // false
					  ```
				-
		- short-circuit logic
			- for `&&` and `||`,  whether they will execute their second operand is dependent on the first.
- # Control Structure
  collapsed:: true
	- `for...of`
	- `for...in`
- # Objects
  collapsed:: true
	- JavaScript objects can be thought of as simple collections of name-value pairs.
	  Everything (bar core types) in JavaScript is an object
	  The "name" part is a JavaScript string, while the value can be any JavaScript value — including more objects.
	- ## Construction
	  collapsed:: true
		- 1
			- ```js
			  const obj = new Object();
			  ```
		- 2
		- ```js
		  const obj = {};
		  ```
	- ## Attribute Accessing
	  collapsed:: true
		- ```js
		  obj.details.color; // orange
		  obj['details']['size']; // 12
		  ```
	- ## Prototype and Prototype chain
	  collapsed:: true
		- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object
		- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain
		-
- # Array
  collapsed:: true
	-
- # Functions
  collapsed:: true
	- ## Tradtional Function
	  collapsed:: true
		- `return`
		  collapsed:: true
			- no `return`, the function will return a `undefined`
		- Parameters
		  collapsed:: true
			- pass in more arguments than the function is expecting
				- Example:
				  collapsed:: true
					- add
					  ```js
					  function add(x, y) {
					    const total = x + y;
					    return total;
					  }
					  ```
					- more args:
					  ```js
					  add(2, 3, 4); // 5
					  // added the first two; 4 was ignored
					  ```
			- but functions have access to an additional variable inside their body called [ `arguments` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments), which is an array-like object holding all of the values passed to the function.
			  collapsed:: true
				- ```js
				  function add() {
				    let sum = 0;
				    for (const item of arguments) {
				      sum += item;
				    }
				    return sum;
				  }
				  
				  add(2, 3, 4, 5); // 14
				  
				  ```
			- rest parameters `...args`
		- ### Anonymous functions
		  collapsed:: true
			- ```js
			  // Note that there's no function name before the parentheses
			  let avg = function() {
			    let sum = 0;
			    for (const item of arguments) {
			      sum += item;
			    }
			    return sum / arguments.length;
			  };
			  ```
	- ## Closure
	  collapsed:: true
		- A **closure** is the combination of a function and the scope object in which it was created.
			- Explain:
				- Whenever JavaScript executes a function, a 'scope' object is created to hold the local variables created within that function. It is initialized with any variables passed in as function parameters.
				- This is similar to the global object that all global variables and functions live in, but with a couple of important differences:
				  collapsed:: true
					- 1. a brand new scope object is created every time a function starts executing
					  2. these scope objects cannot be directly accessed from your JavaScript code , unlike the global object (which is accessible as  `this`  and in browsers as  `window` ) . 
					  3. There is no mechanism for iterating over the properties of the current scope object, for example.
			- Example:
			  collapsed:: true
				- ```js
				  function makeAdder(a) {
				    return function(b) {
				      return a + b;
				    };
				  }
				  const add5 = makeAdder(5);
				  const add20 = makeAdder(20);
				  add5(6); // ?
				  add20(7); // ?
				  ```
					- 1. So when  `makeAdder()`  is called, a scope object is created with one property:  `a` , which is the argument passed to the  `makeAdder()`  function.  
					  2. `makeAdder()`  then returns a newly created function. 
					  3. Normally JavaScript's garbage collector would clean up the scope object created for `makeAdder()` at this point, but the returned function maintains a reference back to that scope object.
					  4. As a result, the scope object will not be garbage-collected until there are no more references to the function  object that  `makeAdder()`  returned.
		- https://stackoverflow.com/questions/111102/how-do-javascript-closures-work
		- Other Languages Have Function Closures:
			- [[Golang]]
	- ## Arrow Function
		- An **arrow function expression** is a compact alternative to a traditional [function expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/function), but is limited and can't be used in all situations.
		- Differences with traditional functions
			- Arrow functions don't have their own bindings to [ `this` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this), [ `arguments` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments) or [ `super` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super), and should not be used as [methods](https://developer.mozilla.org/en-US/docs/Glossary/Method).
			- Arrow functions don't have access to the [ `new.target` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new.target) keyword.
			- Arrow functions aren't suitable for [ `call` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call), [ `apply` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) and [ `bind` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) methods, which generally rely on establishing a [scope](https://developer.mozilla.org/en-US/docs/Glossary/Scope).
			- Arrow functions cannot be used as [constructors](https://developer.mozilla.org/en-US/docs/Glossary/Constructor).
			- Arrow functions cannot use [ `yield` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield), within its body.
		- Syntax
			- Basic
			  collapsed:: true
				- One Param & One Statement
				  collapsed:: true
					- ```js
					  param => expression
					  ```
				- Multiple Params
				  collapsed:: true
					- ```js
					  (p1, p2) => expression
					  ```
				- Multiple Statements
				  collapsed:: true
					- ```js
					  param => {
					  	let a = 1;
					    	return a + param;
					  }
					  ```
				- Multiple Params & Multiple Statements
				  collapsed:: true
					- ```javascript
					  (param1, param2) => {
					  	let a = 1;
					    	return a + param1;
					  }
					  ```
			- Advanced
				- [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#advanced_syntax)
- # Class
	- Classes are a template for creating objects.
	  Classes in JS are built on prototypes but also have some syntax and semantics that are not shared with ES5 class-like semantics.
	- Define a class
	  collapsed:: true
		- Class declarations
		  collapsed:: true
			- ```js
			  class Rectangle {
			    constructor(height, width) {
			      this.height = height;
			      this.width = width;
			    }
			  }
			  ```
		- Class expressions
		  collapsed:: true
			- ```js
			  // unnamed
			  let Rectangle = class {
			    constructor(height, width) {
			      this.height = height;
			      this.width = width;
			    }
			  };
			  console.log(Rectangle.name);
			  // output: "Rectangle"
			  
			  // named
			  let Rectangle = class Rectangle2 {
			    constructor(height, width) {
			      this.height = height;
			      this.width = width;
			    }
			  };
			  console.log(Rectangle.name);
			  // output: "Rectangle2"
			  ```
	- [Sub classing with  `extends` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#sub_classing_with_extends)
	- [Species](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#species)
	- [Super class calls with  `super` ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#super_class_calls_with_super)
	- [Mix-ins](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#mix-ins)
	- [Re-running a class definition](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#re-running_a_class_definition)
	- [Specifications](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#specifications)
	- [Browser compatibility](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#browser_compatibility)
	-
- # Promise
- # Async
  collapsed:: true
	- Callback
		- 很少使用
			- 回调地狱
				- https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Asynchronous/Introducing#%E5%9B%9E%E8%B0%83