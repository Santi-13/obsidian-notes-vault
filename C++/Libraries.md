#Cpp #Programming

--- 
### Chrono 
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
