- # Types
	- dictionary `{}`
	- tuple `()`
		- immutable
		- $a = (1, )$ meaning a tuple with length 1
		  $a = (1)$ meaning an int $a$
		-
	-
-
- algorithic operation
  collapsed:: true
	- `**` power
		- ```python
		  >>> 3 ** 2
		  9
		  ```
	-
- `range` function
  collapsed:: true
	- Python range() Function
	- range(n)
	    reversed()
	    range(start, stop)
	    range(start, stop, step)
	- 左开右闭
- ## `list`
  collapsed:: true
	- Init
		- `list = [value] * size`
			- ```python
			  >>> a = [2] * 10
			  >>> a
			  [2, 2, 2, 2, 2, 2, 2, 2, 2, 2]
			  ```
	-
	- `list comprehension` (列表解析/列表推导)
	- operation
		- `list.append()`
			- Modify the original list, no need to re-assign like golang
		- `+`
			- Create new list, need to be re-assigned
			- ```python
			  >>> l + [3]
			  [1, 2, 3]
			  >>> l
			  [1, 2]
			  >>> l = l + [3]
			  >>> l
			  [1, 2, 3]
			  ```
		- `extend`
			-