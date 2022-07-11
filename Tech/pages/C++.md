- # STL
	- ## `<string>`
		- you can use `s.push_back()`
		- you can use `s[i]`
		- check whether a string contains a char
			- < C++ 20: `s.find('#') < s.length()`
			- C++ 23: `s.contains('#')`
		- `string` to `int`
			- ``` C++
			  string s;
			  int i = std::stoi(s);
			  ```
	- ## `std::vector`
		- ### vector 与 数组区别
			- array定义后的空间是固定的了，不能改变；而vector要灵活得多，可再加或减.且只能包含整型字面值常量，枚举常量或者用常量 表达式初始化的整型const对象，非const变量以及需要到运行阶段才知道其值的const变量都不能用来定义数组的维度.
			- 数组和vector不同，一个数组不能用另一个数组初始化，也不能将一个数组赋值给另一个数组；
			- 在用下标访问元素时，vector 使用 vector::size_type 作为下标的类型，而数组下标的正确类型则是 size_t；
			- vector 是STL中的容器类，包含多种通用算法,长度可变，使用灵活，但效率稍低.
			- vector有一系列的函数操作，非常方便使用.和vector不同，数组不提供push——back或者其他的操作在数组中添加新元素，数组一经定义就不允许添加新元素； 若需要则要充许分配新的内存空间，再将员数组的元素赋值到新的内存空间。
			- 和vector不同，数组不提供 push——back或者其他的操作在数组中添加新元素，数组一经定义就不允许添加新元素； 若需要则要充许分配新的内存空间，再将员数组的元素赋值到新的内存空间。
		- ### vector 的初始化
			- ### init 2D vecotr
				- ``` C++
				  vector<vector<int>> dist(m, vector<int>(n, INT32_MAX));
				  ```
		- ### `std::vector.pop_back()`
			- Remove and destory the last ele in the vec, change the vec's size.
		- ### extract a subvector
			- ```C++
			  vector<T>::const_iterator first = myVec.begin() + 100000;
			  vector<T>::const_iterator last = myVec.begin() + 101000;
			  vector<T> newVec(first, last);
			  ```
	- ## `std::map`
		- Entries in `std::map` are ordered by the key
		- insert `std::pair` into map
		- contains
			- ```C++
			      map<int, int> m;
			      vector<int> v = {1, 1, 1, 2, 2, 3, 3, 4, 4};
			      for (auto i : v) {
			          if (m.count(i) == 0) {
			              m.insert(pair<int, int>(i, 1));
			          } else {
			              m[i] += 1;
			          }
			      }
			      for (auto i : m) {
			          cout << "K: " << i.first << " V: " << i.second << endl;
			      }
			  
			  	// 也可以直接：
			   	for (auto i: arr)   m[i] += 1;
			  ```
		- What happened when using `operator[]` access a element doesnot exist in map?
			- https://stackoverflow.com/questions/10124679/what-happens-if-i-read-a-maps-value-where-the-key-does-not-exist
			- ```C++
			  class UndergroundSystem {
			  private:
			      // key: id, val: { start, time }
			      map<int, pair<string,int>> checkInTable;
			      // key: { fir: start, sec: end} , { fir: times, sec: total time }
			      map<pair<string, string>, pair<int, int>> checkOutTable;
			  public:
			      UndergroundSystem() {
			      }
			  
			      void checkIn(int id, string stationName, int t) {
			          checkInTable[id] = pair<string,int>(stationName, t);
			      }
			  
			      void checkOut(int id, string stationName, int t) {
			          int duration = t - checkInTable[id].second;
			          // check this one
			        	checkOutTable[{checkInTable[id].first, stationName}].first += 1;
			          checkOutTable[{checkInTable[id].first, stationName}].second += duration;
			      }
			  
			      double getAverageTime(string startStation, string endStation) {
			          return (double)checkOutTable[{startStation, endStation}].second / (double)checkOutTable[{startStation, endStation}].first;
			      }
			  };
			  ```
				- As shown above,
	- ## `std::priority_queue`
		- 1. 默认创建最大堆
		  2. 如何创建最小堆？
		- ```C++
		  #include <queue>
		  
		  priority_queue<int> pq;
		  ```
		- custom comparator
			- ``` C++
			  class CompareByPairsSecond {
			  public:
			      bool operator()(pair<int, int>& p1, pair<int, int>& p2) {
			          return p1.second < p2.second;
			      }
			  };
			  
			  class Solution {
			  public:
			      int minSetSize(vector<int>& arr) {
			          priority_queue<pair<int, int>, vector<pair<int, int>>, CompareByPairsSecond> pq;
			  ...
			  ```
	- ## `std::sort()`
		- ```C++
		  // sort algorithm example
		  #include <iostream>     // std::cout
		  #include <algorithm>    // std::sort
		  #include <vector>       // std::vector
		  
		  bool myfunction (int i,int j) { return (i<j); }
		  
		  struct myclass {
		    bool operator() (int i,int j) { return (i<j);}
		  } myobject;
		  
		  int main () {
		    int myints[] = {32,71,12,45,26,80,53,33};
		    std::vector<int> myvector (myints, myints+8);               // 32 71 12 45 26 80 53 33
		  
		    // using default comparison (operator <):
		    std::sort (myvector.begin(), myvector.begin()+4);           //(12 32 45 71)26 80 53 33
		  
		    // using function as comp
		    std::sort (myvector.begin()+4, myvector.end(), myfunction); // 12 32 45 71(26 33 53 80)
		  
		    // using object as comp
		    std::sort (myvector.begin(), myvector.end(), myobject);     //(12 26 32 33 45 53 71 80)
		  
		    // print out content:
		    std::cout << "myvector contains:";
		    for (std::vector<int>::iterator it=myvector.begin(); it!=myvector.end(); ++it)
		      std::cout << ' ' << *it;
		    std::cout << '\n';
		  
		    return 0;
		  }
		  ```
		- ``` C++
		  bool cmp(pair<int, int>& a, pair<int, int>& b) {
		      return a.second > b.second;
		  };
		  
		  class Solution {
		  public:
		      vector<int> topKFrequent(vector<int>& nums, int k) {
		          map<int, int> m;
		          for (int i : nums) m[i] += 1;
		          vector<pair<int, int>> v;
		          for (auto i : m) v.push_back(i);
		          sort(v.begin(), v.end(), cmp);
		          vector<int> res;
		          for (int i = 0; i < k; i++) {
		              res.push_back(v[i].first);
		          }
		          return res;
		      }
		  };
		  ```
	- ## `std::find`
		- `include <algorithm>`
		- You get an iterator
			- ```C++
			  auto val_in = find(inorder.begin(), inorder.end(), val);
			  ```
		- ### `find_if()`
			- You can use lamda in `find_if`
				- ``` C++
				  list<pair<int, int>>::iterator find(int key) {
				    int hashed = hash(key);
				    return find_if(table[hashed].begin(), table[hashed].end(), [&](pair<int, int> const & ref) {
				      return ref.first == key;
				    });
				  }
				  ```
				- As the definition is:
				  src:: https://en.cppreference.com/w/cpp/algorithm/find
					- ``` C++
					  template< class InputIt, class UnaryPredicate >
					  InputIt find_if( InputIt first, InputIt last, UnaryPredicate p );
					  ```
					- Check ((6262bf58-5ffe-48be-b6eb-acb88f378a43)) for UnaryPredicate
	- ## contains
		- ```C++
		  #include <algorithm>
		  
		  if(std::find(v.begin(), v.end(), x) != v.end()) {
		      /* v contains x */
		  } else {
		      /* v does not contain x */
		  }
		  ```
- # `auto`
- # Bit Manipulation
	- ## XOR
		- ^=
	- & 按位与 	如果两个相应的二进制位都为1，则该位的结果值为1，否则为0
	  I 按位或 	两个相应的二进制位中只要有一个为1，该位的结果值为1
	  ^ 按位异或 	若参加运算的两个二进制位值相同则为0，否则为1
	  ~ 取反 	~是一元运算符，用来对一个二进制数按位取反，即将0变1，将1变0
	  << 左移 	用来将一个数的各二进制位全部左移N位，右补0
	  >> 右移 	将一个数的各二进制位右移N位，移到右端的低位被舍弃，对于无符号数，高位补0
- # Lambda
	- Predicate
	  id:: 6262bf58-5ffe-48be-b6eb-acb88f378a43
		- src:: https://en.cppreference.com/w/cpp/named_req/Predicate
		  The **_Predicate_** requirements describe a callable that returns a value testable as a `bool`.
	- ` [ captures ] ( params ) specs requires(optional) { body } `
		- `[captures]`
			- `[]` , capture nothing
			- `[&]` means all variables that you refer to are captured by reference
			- `[=]`  means they're captured by value.