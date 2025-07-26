#Cpp #Programming

--- 
### `<chrono>` 
```cpp
#include<chrono>
using namespace std::chrono;
using std::cout;

int sum(int a, int b) {
	return a + b;
}

int main() {
	auto start = high_resolution_clock::now();
	c = sum(2,2);
	auto end = high_resolution_clock::now();
	auto duration = duration_cast<milliseconds>(end - start);

	cout << "Execution time was " << duration.count() << "ms"
	
	return 0;
}
```
### `<vector>`
```cpp
#include<vector>
vector<int> a = {1,2,3};
vector<double> b = {1.1,2.2,3.3};

template <typename T>
void printVector(const vector<T>& a) {
	std::cout << "[ ";
	for (const auto& element : a) {
		std::cout << element << " ";
	}
	std::cout << "]" << endl;
}

printVector(a)
//prints [ 1 2 3 ]
b.insert(0.1)
b.push_back(4.4)
printVector(b)
//prints [ 0.1 1.1 2.2 3.3 4.4 ]
```

### `<utility>`
```cpp
#include<utility>
using std::swap;

vector<int> a = {1,2,3};
swap(a[0],a[1])
printVector(a)
//prints [ 2 1 3 ]
```

### `<deque>`
```cpp
#include <iostream> 
#include <deque> 
int main() { 
	// Efficiently remove the first element
	std::deque<int> numbers = {10, 20, 30, 40};  
	numbers.pop_front(); 
	// The deque is now [ 20 30 40 ] return 0; 
}
```

