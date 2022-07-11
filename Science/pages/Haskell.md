# Type
	- Explicit types are always denoted with the first letter in capital case
	- ## Common Types
		- ## Bool
			- `True` & `False`
			- `==` & `/=` (not equal)
		- `Num`
		- `Int`
		- `Integer`
		- `Float`
		- `Double`
		- ## String & Character
			- strings are a list of characters
	- ## List
		- In Haskell, lists are a **homogenous** data structure.
		- `++` concatenate 2 lists
		  collapsed:: true
			- ```haskell
			  ghci> [1,2,3,4] ++ [9,10,11,12]  
			  [1,2,3,4,9,10,11,12]  
			  ghci> "hello" ++ " " ++ "world"  
			  "hello world"  
			  ghci> ['w','o'] ++ ['o','t']  
			  "woot"  
			  ```
		- `:` put sth at the beginning of the list
		  collapsed:: true
			- ```haskell
			  ghci> [1,2,3,4] ++ [9,10,11,12]  
			  [1,2,3,4,9,10,11,12]  
			  ghci> "hello" ++ " " ++ "world"  
			  "hello world"  
			  ghci> ['w','o'] ++ ['o','t']  
			  "woot"  
			  ```
		- `!!` get element by index
		  collapsed:: true
			- ```haskell
			  ghci> "Steve Buscemi" !! 6  
			  'B'  
			  ghci> [9.4,33.2,96.2,11.2,23.25] !! 1  
			  33.2  
			  ```
		- ### Operations
		  collapsed:: true
			- `head`
			- `tail`
			- `last`
			- `init`
			- `length`
			- `null`
			- `reverse`
			- `take`
				- id:: 6270c009-3dd6-4f1b-9ba0-5344ab9c2109
				  ```haskell
				  ghci> take 10 [2, 4..]
				  [2,4,6,8,10,12,14,16,18,20]
				  ```
			- `drop`
			- `maximum` `minimum`
			- `sum` `product`
			- `elem`
		- ranges
		  collapsed:: true
			- ```haskell
			  ghci> [1..20]  
			  [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]  
			  ghci> ['a'..'z']  
			  "abcdefghijklmnopqrstuvwxyz"  
			  ghci> ['K'..'Z']  
			  "KLMNOPQRSTUVWXYZ"  
			  ```
			- range with step
				- ```haskell
				  ghci> [2,4..20]  
				  [2,4,6,8,10,12,14,16,18,20]  
				  ghci> [3,6..20]  
				  [3,6,9,12,15,18]
				  ```
			- reverse range
				- To make a list with all the numbers from 20 to 1, you can't just do`[20..1]` , you have to do`[20,19..1]` .
			- not use float in ranges, they are not precise
				- ```haskell
				  ghci> [0.1, 0.3 .. 1]  
				  [0.1,0.3,0.5,0.7,0.8999999999999999,1.0999999999999999]  
				  ```
			- infinite range
			- `cycle`  takes a list and cycles it into an infinite list. If you just try to display the result, it will go on forever so you have to slice it off somewhere.
				- ```haskell
				  ghci> take 10 (cycle [1,2,3])  
				  [1,2,3,1,2,3,1,2,3,1]  
				  ghci> take 12 (cycle "LOL ")  
				  "LOL LOL LOL "  
				  ```
			- `repeat` takes an element and produces an infinite list of just that element. It's like cycling a list with only one element.
				- ```haskell
				  ghci> take 10 (repeat 5)  
				  [5,5,5,5,5,5,5,5,5,5]  
				  ```
			-
		- ### List Comprehension
			- ```
			  ghci> [x*2 | x <- [1..10]]  
			  [2,4,6,8,10,12,14,16,18,20]  
			  ```
			- `length'`
				- ```haskell
				  length' xs = sum [1 | _ <- xs]   
				  ```
			- `removeNonUppercase`
				- ```haskell
				  removeNonUppercase st = [ c | c <- st, c `elem` ['A'..'Z']]   
				  ```
	- ## Tuple
	  collapsed:: true
		- use `()` to store several values together no matter what their types are
			- ```haskell
			  [(1, 2), (3, 4), (5, 6)]
			  ```
		- `(1, 2)` is a **type** that carries 2 int tuple.
		- ### functions
			- `fst`takes a **pair** and returns its first component.
			  id:: 6270cbcb-ae0d-41ef-89dd-e5b0d73a5075
			- `snd` takes a **pair** and returns its second component.
			- `zip`, merge two lists into one by making elements to tuples
				- ```haskell
				  ghci> zip [5,3,2,6,2,7,2,5,4,6,6] ["im","a","turtle"]  
				  [(5,"im"),(3,"a"),(2,"turtle")]  
				  ```
			-
	- ## `::`
		- means "has the type of"
	- ## `->`
		-
			- ```haskell
			  addThree :: Int -> Int -> Int -> Int  
			  addThree x y z = x + y + z  
			  ```
				- TODO Later on we'll see why they're all just separated with`->`  instead of having some more explicit distinction between the return types and the parameters like
	- ## `=>`
		- ```haskell
		  ghci> :t (==)  
		  (==) :: (Eq a) => a -> a -> Bool 
		  ```
		- Everything before the `=>` symbol is called a class constraint.
		- We can read the previous type declaration like this: the equality function takes any two values that are of the same type and returns a `Bool`. The type of those two values must be a member of the `Eq` class (this was the class constraint).
	- ## Type Variable
		- ```haskell
		  ghci> :t head  
		  head :: [a] -> a  
		  ```
		- That means that `a` can be of any type. This is much like generics in other languages, only in Haskell it's much more powerful because it allows us to easily write very general functions if they don't use any specific behavior of the types in them.
		- Functions that have type variables are called **polymorphic** functions.
	- ## Type Class
	  collapsed:: true
		- A typeclass is a sort of interface that defines some behavior. If a _type_ is a part of a typeclass, that means that **it supports and implements the behavior the typeclass describes**.
			- You can think of them kind of as Java interfaces, only better.
			  id:: 62713889-9f95-428c-a58c-1ff029f3aa0f
		- The `Eq` typeclass provides an interface for testing for equality. Any type where it makes sense to test for equality between two values of that type should be a member of the `Eq` class. All standard Haskell types except for `IO` (the type for dealing with input and output) and functions are a part of the `Eq` typeclass.
		- ### Basic Type Classes
			- `Eq`
			- `Ord`
				- The compare function takes two `Ord` members of the same type and returns an ordering. Ordering is a type that can be `GT`, `LT` or `EQ`, meaning greater than, lesser than and equal, respectively.
			- `Show` can be presented as strings
			- `Read`
				- we can use explicit **type annotations**. Type annotations are a way of explicitly saying what the type of an expression should be.
					- ```haskell
					  ghci> read "5" :: Int  
					  5  
					  ghci> read "5" :: Float  
					  5.0  
					  ghci> (read "5" :: Float) * 4  
					  20.0  
					  ghci> read "[1,2,3,4]" :: [Int]  
					  [1,2,3,4]  
					  ghci> read "(3, 'a')" :: (Int, Char)  
					  (3, 'a')  
					  ```
			- `Enum` we can use its types in list ranges.
			- `Num`
			- `Integral`
			- `Floating`
# Function
	- `infix` function, like `*`, `+`
		- a function takes 2 parameters can be invoked in `infix` form like
			- ```haskell
			  1 `max` 2
			  ```
	- `prefix`function, like `succ {parameter}`, a ` ` space and parameters
	- `(func paramerts)` use `()` to wrap funcs and execute it in precedence
	- a func takes no parameter is a definition
		- ```haskell
		  a = "Hello"
		  ```
	- ## Function Type
	  collapsed:: true
		- `removeNonUppercase` has a type of`[Char] -> [Char]`
			- ```haskell
			  removeNonUppercase :: [Char] -> [Char]  
			  removeNonUppercase st = [ c | c <- st, c `elem` ['A'..'Z']]   
			  ```
	- ## Pattern Match
		- You can pattern match on any data type — numbers, characters, lists, tuples, etc. Let's make a really trivial function that checks if the number we supplied to it is a seven or not.
			- ```haskell
			  lucky :: (Integral a) => a -> String  
			  lucky 7 = "LUCKY NUMBER SEVEN!"  
			  lucky x = "Sorry, you're out of luck, pal!"   
			  ```
		- Order Matters
			- ```haskell
			  factorial :: (Integral a) => a -> a  
			  factorial 0 = 1  
			  factorial n = n * factorial (n - 1)  
			  ```
			- if `factorial n = n * factorial (n - 1)` is on the front, the function will never exit.
		- Pattern Match will fail
			- ```haskell
			  charName :: Char -> String  
			  charName 'a' = "Albert"  
			  charName 'b' = "Broseph"  
			  charName 'c' = "Cecil"  
			  ```
			- ```haskell
			  ghci> charName 'a'  
			  "Albert"  
			  ghci> charName 'b'  
			  "Broseph"  
			  ghci> charName 'h'  
			  "*** Exception: tut.hs:(53,0)-(55,21): Non-exhaustive patterns in function charName  
			  ```
		-
# Experssion
	- expression must return sth
	- `if then else`
		- `else` is mandatory