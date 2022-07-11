- # Array
	- ```
	  int[] arr = {1, 2, 3};
	  ```
- # Method Parameters – *call by value*
	- # How parameters can be passed to a method
	- *call by value*: the method gets just the value provided.
	- *call by reference*: the method gets the *location* of the variable (or variable itself)
	- # Java uses *call by value*
		- ## for *primitive* variable:
			- `void method (boolean x)`
			- 1. Copy the value and pass it to the method to initialize `x`.
			  2. Computation in the method.
			  3. Method ends. The parameter variable `x` is **abandoned**.
		- ## for *object* variable:
			- `void method (Object x)`
			- 1. `x` is initialized with a copy of *object reference*. Both original and copy refer to the object
			  2. Computation in the method. You can **change the state** of the object via reference.
			  3. Method ends. The parameter variable `x` is **abandoned**.
	- # What you can do and cannot do with parameter method in Java:
		- A method cannot modify a parameter of a *primitive* type.
		- A method can change the *state* of an object parameter.
		- A method cannot make an object parameter refer to a new object.