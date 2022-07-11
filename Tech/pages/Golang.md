- # `string` & `byte`
  collapsed:: true
	- string is immutable
		- ```go
		  # build will fail
		  s := "hello"
		  s[0:2] = "bn"
		  ```
	- string 可以转化为 字节数组操作
	- https://golangbyexample.com/double-single-back-quotes-go/
- # Data Structure
  collapsed:: true
	- ## slice `[]any`
		- `[]any` and `*[]any` as function arguments
			- The thing passed into the function is actually a **copy** of
				- ```go
				  type SliceHeader struct {
				       Length        int
				       Capacity    int
				       ZerothElement *byte
				  }
				  ```
				- the change to the `ZerothElement` will make effect to the slice out of the function, but the Length and Capacity remains unchanged.
			- ref: https://medium.com/swlh/golang-tips-why-pointers-to-slices-are-useful-and-how-ignoring-them-can-lead-to-tricky-bugs-cac90f72e77b
- # Method & Interface
	- ## value receiver & pointer receiver
		- ```go
		  func (s *MyStruct) pointerMethod() { } // method on pointer
		  func (s MyStruct)  valueMethod()   { } // method on value
		  ```
		- Diff:
		  src:: https://go.dev/doc/faq#methods_on_values_or_pointers
			- 1. Do you need to modify receiver?
			  2. Efficiency: value receiver passes the whole copy of struct. If the receiver is large, a big struct for instance, it will be much cheaper to use a pointer receiver.
			  3. Consistency: If some of the methods of the type must have pointer receivers, the rest should too, so the [method set](https://go.dev/doc/faq#different_method_sets) is consistent regardless of how the type is used. See the section on method sets for details.
	-