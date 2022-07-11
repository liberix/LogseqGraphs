- {{query (todo todo now later doing)}}
  query-sort-by:: block
  query-table:: true
  query-sort-desc:: true
# Type
	- Explicit types are always denoted with the first letter in capital case
	- ## Common Types
	  collapsed:: true
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
	  collapsed:: true
		- In Haskell, lists are a **homogenous** data structure.
		- `++` concatenate 2 lists
			- ``` haskell
			  ghci> [1,2,3,4] ++ [9,10,11,12]  
			  [1,2,3,4,9,10,11,12]  
			  ghci> "hello" ++ " " ++ "world"  
			  "hello world"  
			  ghci> ['w','o'] ++ ['o','t']  
			  "woot"  
			  ```
		- `:` put sth at the beginning of the list
			- ``` haskell
			  ghci> [1,2,3,4] ++ [9,10,11,12]  
			  [1,2,3,4,9,10,11,12]  
			  ghci> "hello" ++ " " ++ "world"  
			  "hello world"  
			  ghci> ['w','o'] ++ ['o','t']  
			  "woot"  
			  ```
		- `!!` get element by index
			- ``` haskell
			  ghci> "Steve Buscemi" !! 6  
			  'B'  
			  ghci> [9.4,33.2,96.2,11.2,23.25] !! 1  
			  33.2  
			  ```
		- ### Operations
			- `head`
			- `tail`
			- `last`
			- `init`
			- `length`
			- `null`
			- `reverse`
			- `take`
				- ``` haskell
				  ghci> take 10 [2, 4..]
				  [2,4,6,8,10,12,14,16,18,20]
				  ```
			- `drop`
			- `maximum` `minimum`
			- `sum` `product`
			- `elem`
		- ranges
		  collapsed:: true
			- ``` haskell
			  ghci> [1..20]  
			  [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]  
			  ghci> ['a'..'z']  
			  "abcdefghijklmnopqrstuvwxyz"  
			  ghci> ['K'..'Z']  
			  "KLMNOPQRSTUVWXYZ"  
			  ```
			- range with step
				- ``` haskell
				  ghci> [2,4..20]  
				  [2,4,6,8,10,12,14,16,18,20]  
				  ghci> [3,6..20]  
				  [3,6,9,12,15,18]
				  ```
			- reverse range
				- To make a list with all the numbers from 20 to 1, you can't just do`[20..1]` , you have to do`[20,19..1]` .
			- not use float in ranges, they are not precise
				- ``` haskell
				  ghci> [0.1, 0.3 .. 1]  
				  [0.1,0.3,0.5,0.7,0.8999999999999999,1.0999999999999999]  
				  ```
			- infinite range
			- `cycle`  takes a list and cycles it into an infinite list. If you just try to display the result, it will go on forever so you have to slice it off somewhere.
				- ``` haskell
				  ghci> take 10 (cycle [1,2,3])  
				  [1,2,3,1,2,3,1,2,3,1]  
				  ghci> take 12 (cycle "LOL ")  
				  "LOL LOL LOL "  
				  ```
			- `repeat` takes an element and produces an infinite list of just that element. It's like cycling a list with only one element.
				- ``` haskell
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
				- ``` haskell
				  length' xs = sum [1 | _ <- xs]   
				  ```
			- `removeNonUppercase`
				- ``` haskell
				  removeNonUppercase st = [ c | c <- st, c `elem` ['A'..'Z']]   
				  ```
	- ## Tuple
	  collapsed:: true
		- use `()` to store several values together no matter what their types are
			- ``` haskell
			  [(1, 2), (3, 4), (5, 6)]
			  ```
		- `(1, 2)` is a **type** that carries 2 int tuple.
		- ### functions
			- `fst`takes a **pair** and returns its first component.
			- `snd` takes a **pair** and returns its second component.
			- `zip`, merge two lists into one by making elements to tuples
				- ``` haskell
				  ghci> zip [5,3,2,6,2,7,2,5,4,6,6] ["im","a","turtle"]  
				  [(5,"im"),(3,"a"),(2,"turtle")]  
				  ```
			-
# Operator
	- ## `::`
	  collapsed:: true
		- means "has the type of"
	- ## `->`
	  collapsed:: true
		-
			- ``` haskell
			  addThree :: Int -> Int -> Int -> Int  
			  addThree x y z = x + y + z  
			  ```
				- TODO Later on we'll see why they're all just separated with`->`  instead of having some more explicit distinction between the return types and the parameters like
	- ## `=>`
	  collapsed:: true
		- ``` haskell
		  ghci> :t (==)  
		  (==) :: (Eq a) => a -> a -> Bool 
		  ```
		- Everything before the `=>` symbol is called a class constraint.
		- We can read the previous type declaration like this: the equality function takes any two values that are of the same type and returns a `Bool`. The type of those two values must be a member of the `Eq` class (this was the class constraint).
	- ## TODO <-
	- ## `|` guard
	  collapsed:: true
		- like `switch` and `if...else`
			- Guards are indicated by pipes that follow a function's name and its parameters.
		- A guard is basically a boolean expression. If it evaluates to True, then the corresponding function body is used. If it evaluates to False, checking drops through to the next guard and so on.
		- ```haskell
		  bmiTell :: (RealFloat a) => a -> String  
		  bmiTell bmi  
		  | bmi <= 18.5 = "You're underweight, you emo, you!"  
		  | bmi <= 25.0 = "You're supposedly normal. Pffft, I bet you're ugly!"  
		  | bmi <= 30.0 = "You're fat! Lose some weight, fatty!"  
		  | otherwise   = "You're a whale, congratulations!"
		  ```
		- Many times, the last guard is otherwise. otherwise is defined simply as otherwise = True and catches everything.
	- ## `where` bindings
	  collapsed:: true
		- We put the keyword `where` after the guards (usually it's best to indent it as much as the pipes are indented) and then we define several names or functions. These names are visible across the guards and give us the advantage of not having to repeat ourselves.
			- ```haskell
			  bmiTell :: (RealFloat a) => a -> a -> String  
			  bmiTell weight height  
			  | bmi <= skinny = "You're underweight, you emo, you!"  
			  | bmi <= normal = "You're supposedly normal. Pffft, I bet you're ugly!"  
			  | bmi <= fat    = "You're fat! Lose some weight, fatty!"  
			  | otherwise     = "You're a whale, congratulations!"  
			  where bmi = weight / height ^ 2  
			  skinny = 18.5  
			  normal = 25.0  
			  fat = 30.0
			  ```
		- Use `where` bindings to ((627bc823-aff6-4468-9cae-d364ededeb63)) !
			- ```haskell
			  initials :: String -> String -> String  
			  initials firstname lastname = [f] ++ ". " ++ [l] ++ "."  
			  where (f:_) = firstname  
			  (l:_) = lastname
			  ```
		- Define functions in `where`
			- ```haskell
			  calcBmis :: (RealFloat a) => [(a, a)] -> [a]  
			  calcBmis xs = [bmi w h | (w, h) <- xs]  
			  where bmi weight height = weight / height ^ 2  
			  ```
	- ## `let` bindings
		- `let <bindings> in <expression>`
		- very local
			- ```haskell
			  calcBmis :: (RealFloat a) => [(a, a)] -> [a]  
			  calcBmis xs = [bmi | (w, h) <- xs, let bmi = w / h ^ 2, bmi >= 25.0]  
			  ```
			- We can't use the `bmi` name in the `(w, h) <- xs` part because it's defined prior to the let binding.
		- The difference is that let bindings are expressions themselves. where bindings are just syntactic constructs.
		- as expression:
			- ```haskell
			  ghci> 4 * (let a = 9 in a + 1) + 2  
			  42  
			  ```
		- introduce function in local space
			- ```haskell
			  ghci> [let square x = x * x in (square 5, square 3, square 2)]  
			  [(25,9,4)]  
			  ```
		- use `;` to seperate
			- ```haskell
			  ghci> (let a = 100; b = 200; c = 300 in a*b*c, let foo="Hey "; bar = "there!" in foo ++ bar)  
			  (6000000,"Hey there!")  
			  ```
		- pattern matching
	- `case` expression
		- ```haskell
		  case expression of 	pattern -> result  
		  pattern -> result  
		  pattern -> result  
		  ...
		  ```
	- ## Type Variable
		- ``` haskell
		  ghci> :t head  
		  head :: [a] -> a  
		  ```
		- That means that `a` can be of any type. This is much like generics in other languages, only in Haskell it's much more powerful because it allows us to easily write very general functions if they don't use any specific behavior of the types in them.
		- Functions that have type variables are called **polymorphic** functions.
	- ## Type Class
	  collapsed:: true
		- A typeclass is a sort of interface that defines some behavior. If a *type* is a part of a typeclass, that means that **it supports and implements the behavior the typeclass describes**.
			- You can think of them kind of as Java interfaces, only better.
		- The `Eq` typeclass provides an interface for testing for equality. Any type where it makes sense to test for equality between two values of that type should be a member of the `Eq` class. All standard Haskell types except for `IO` (the type for dealing with input and output) and functions are a part of the `Eq` typeclass.
		- ### Basic Type Classes
			- `Eq`
			- `Ord`
				- The compare function takes two `Ord` members of the same type and returns an ordering. Ordering is a type that can be `GT`, `LT` or `EQ`, meaning greater than, lesser than and equal, respectively.
			- `Show` can be presented as strings
			- `Read`
				- we can use explicit **type annotations**. Type annotations are a way of explicitly saying what the type of an expression should be.
					- ``` haskell
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
		- `removeNonUppercase` has a type of`[Char] -> [Char]`
			- ```haskell
			  removeNonUppercase :: [Char] -> [Char]  
			  removeNonUppercase st = [ c | c <- st, c `elem` ['A'..'Z']]   
			  ```
	- ## Pattern Match
	  id:: 627bc823-aff6-4468-9cae-d364ededeb63
		- You can pattern match on any data type — numbers, characters, lists, tuples, etc. Let's make a really trivial function that checks if the number we supplied to it is a seven or not.
		  collapsed:: true
			- ```haskell
			  lucky :: (Integral a) => a -> String  
			  lucky 7 = "LUCKY NUMBER SEVEN!"  
			  lucky x = "Sorry, you're out of luck, pal!"   
			  ```
			- Pattern Matching v.s. Non-Pattern Matching
				- ```haskell
				  '' Non-Pattern Matching
				  addVectors :: (Num a) => (a, a) -> (a, a) -> (a, a)  
				  addVectors a b = (fst a + fst b, snd a + snd b)
				  ```
				- ```haskell
				  '' Pattern Matching
				  addVectors :: (Num a) => (a, a) -> (a, a) -> (a, a)  
				  addVectors (x1, y1) (x2, y2) = (x1 + x2, y1 + y2)
				  ```
		- Order Matters
		  collapsed:: true
			- ```haskell
			  factorial :: (Integral a) => a -> a  
			  factorial 0 = 1  
			  factorial n = n * factorial (n - 1)  
			  ```
			- if `factorial n = n * factorial (n - 1)` is on the front, the function will never exit.
		- Pattern Match will fail
		  collapsed:: true
			- so called: "Non-exhaustive patterns "
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
		- ### `@`Pattern Reference
			- Put a name and `@` in front of a pattern, this will keep a reference to the whole thing.
			- `xs@(x:y:ys)`
				- This pattern will match exactly the same thing as `x:y:ys` but you can easily get the whole list via `xs` instead of repeating yourself by typing out `x:y:ys`
		-
- # Experssion
  collapsed:: true
	- expression must return sth
	- `if then else`
		- `else` is mandatory