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
They're perfect for situations where you may want to quickly find an item on a ever increasing data set —like finding if a user has already watched a video with millions of views—. They work via a ***hash function***, which assigns a value to the item being saved based on the `key`. This way, when a user searches for certain value, the input `key` passes through this function, and the result tells the program *where* to look. This allows almost instantaneous response `O(1)` time.

They are called `hash sets` when you only use the `key` and not the `value`. A simple `hash map` may look like this:

