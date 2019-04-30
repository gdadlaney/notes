## Compiling in c++11
g++ -std=c++11

## Reverse iterators
- for (map<int, int>::**reverse**_iterator = m.**r**begin(); it != m.**r**end(); it<b>++</b> )
- I used this when using maps for their sorted order

## 2D vector
- [2d vectors](https://www.geeksforgeeks.org/2d-vector-in-cpp-with-user-defined-size/)
- can also create a vector for a column & pass to push_back()
- [iterators for 2d vectors](https://stackoverflow.com/questions/1784573/iterator-for-2d-vector)

## Passing stl DS to a function, by reference
- void func(vector<int> v) passes the vector by value, i.e creates a copy.
- void func(vector<int>& v) // use a const before vector if you don't want it to change.
- iterators can also be passed to a function, which are refernces, so can modify the orignal DS.

# Cool features
## 1. Range loops
- for (char c: str) // also for vectors
- for (auto item: my_map)

## 2. Python like reverse addressing (check)
- An arr[-2] equivalent in cpp would be
- *(arr.back()-1) or *(map.rbegin()+1) (since maps don't have .back() )

# Conversions
## 1.a. string to number in C++11
- stoi("45") is 45
- stoi("3.14159") is 3
- stoi("31337 geek") is 31337
- stof(), stod(), stoll() also exist

## 1.b. number to string
- using std::to_string()        // long long or double
- OR sprintf() for a formatted string

## 2.a. Iterator to index (in vectors and strings)
- std::distance(v.begin(), it)  // arg2-arg1
- try `it - v.begin()`

## 2.b. Index to interator (in vectors and strings)
- it = v.begin() + 2

### Others
1. Exceptions
- Throw exceptions using - throw "My new exception"
- Useful to check where the code failed in a test case.


### Other great standard functions -
- std::find()
- replace()

### Not understood -
- for_each()
