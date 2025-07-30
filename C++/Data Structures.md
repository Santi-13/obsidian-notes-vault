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
```cpp
#include <iostream>
#include <string>
#include <unordered_map>

using std::cout;
using std::cin;
using std::endl;
using std::string;

void printMap(const std::unordered_map<string, int>& map) {
    for(const auto item: map) {
        cout << item.first << ": " << item.second << endl;
    }
}

int main() {
	std::unordered_map<string, int> hash_map;
	hash_map["Coffe Cows"] = 2;
	hash_map["Milkshake Moose"] = 1;

	printMap(hash_map);
	/* output:
	Coffe Cows: 2
	Milkshake Moose: 1
	*/

	hash_map["Coffe Cows"] += 5;
	// Checks if item exists in set
	if (hash_map.count("Coffe Cows")) {
		printMap(hash_map);
		/* output:
		Coffe Cows: 2
		Milkshake Moose: 1
		*/
	}
	return 0;
}
```
