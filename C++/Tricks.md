#Cpp #Programming 

---
### scope resolution operator `::`
In `C++`, different libraries can contain similar `names` between them, so to avoid collisions, we use the **scope resolution operator** to differentiate between them.
```cpp
// audio_library.h 
namespace audio { 
	class Player { /* ... */ }; 
} 
// video_library.h 
namespace video { 
	class Player { /* ... */ }; 
}
```

```cpp
#include "audio_library.h" 
#include "video_library.h" 
int main() { 
	audio::Player my_mp3_player; // Clearly the audio player 
	video::Player my_mp4_player; // Clearly the video player 
}
```
### `using`
1. **Type aliasing:** Similar to the traditional typedef but offers a more intuitive syntax.
```cpp
using IntPtr = int*; 
using doble = double; 

doble a = 2.4;
```
2. **Importing namespace:** You can use `using` to bring specific names from a namespace into the current scope, which helps avoid typing the full namespace each time.
```cpp
int a = 1;
std::cout << a;

using std::cout;
cout << a;
```
It is important to note that `using` only targets names, to import all `names` in a `namespace` into the scope, we use `using namespace`.
```cpp
#include <chrono>

auto start = std::chrono::high_resolution_clock::now();

using namespace std::chrono;

auto end = high_resolution_clock::now();
```
3. The `using` keyword allows derived classes to inherit base class members, including constructors. This is useful for exposing protected members as public in derived classes.
```cpp
class Base {
protected:
void foo() { /*...*/ }
};
class Derived : public Base {
public:
using Base::foo; // Makes Base::foo accessible in Derived
};
```
