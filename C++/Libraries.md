#Cpp #Programming

--- 
### `<chrono>` 
Time library.
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
b.
```