#Cpp #Programming

---
### Hash Map/Table/Set
Hash maps are a type of unordered map, with almost instant data retrieval capabilities. They are often called dictionaries or, in `C++`'s case, `std::unordered_map` and are composed of a `key` and a `value`.
```cpp
#include <iostream>
#include <string>
#include <unordered_map>

int main() {
	std::unordered_map<string, int> hash_map;

	return 0;
}
```
They're perfect for situations where you may want to quickly find an item on a ever increasing data set 