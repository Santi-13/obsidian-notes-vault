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
They're perfect for situations where you may want to quickly find an item on a ever increasing data set —like finding if a user has already watched a video with millions of views—. They work via a ***hash function***, which computes an *index* to the item being saved based on the `key`. This way, when a user searches for certain value, the input `key` passes through this function, and the result tells the program *where* to look. This allows almost instantaneous response `O(1)` time.

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
		Coffe Cows: 7
		Milkshake Moose: 1
		*/
	}
	return 0;
}
```

### Ordered Maps
Ordered maps are a type of dictionary, but that is organized from the get-go, facilitating search algorithms, like ***binary tree search***. They have similar methods to **[[#Hash Map/Table/Set|Hash Maps]]**. A simple implementation may look like:
```cpp
#include <iostream>
#include <string>
#include <map>

using std::cout;
using std::endl;
using std::string;
using std::map;

void printGradebook(const map<string, int>& gradebook) {
    for (const auto& student : gradebook) {
        cout << student.first << ": " << student.second << endl;
    }
}

int main() {
    // 1. Create the map
    map<string, int> gradebook;

    // 2. Add students and scores
    gradebook["Charlie"] = 88;
    gradebook["Alice"] = 95;
    gradebook["Bob"] = 72;

    // 3. Update a score if the student exists
    if (gradebook.count("Bob")) {
	    gradebook["Bob"] += 8;
    }

    // 4. Print the final gradebook
    std::cout << "Final Gradebook (Alphabetical):" << std::endl;
    printGradebook(gradebook);

    return 0;
}
```

### Heaps
Heaps are `priority queues`, basically they are an ordered list that follows a simple algorithm according to its type: a `max-heap` has its biggest value at the top of the list; while a `min-heap` has its lowest value at the top.  `C++` heaps are by default `max-heap`.
```cpp
#include <iostream>
#include <queue>

using std::cout;
using std::endl;
using std::priority_queue;

int main() {
    // 1. Create the priority_queue
    priority_queue<int> tasks;

    // 2. Add tasks with different priorities
    tasks.push(10);
    tasks.push(50);
    tasks.push(20);
    tasks.push(40);
    tasks.push(30);

    // 3. Process all tasks in priority order
    std::cout << "Processing tasks:" << std::endl;
    while (!tasks.empty()) {
        cout << tasks.top() << endl;
        tasks.pop(); // Erases from list
    }
    
    return 0;
}
```
The way heaps work in, for example, `max-heaps` is via **nodes**, each node being an item in the queue, then the structure follows a simple rule, all parent **nodes** must be bigger than their children. Whenever we add an item to the queue, we add it to the lowest available child in the hierarchy and we start comparing.
```

      20
    /    \
   10
```