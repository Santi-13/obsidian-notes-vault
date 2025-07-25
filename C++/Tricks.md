#Cpp #Programming 

---
### scope resolution operator `::`
In `C++`, different libraries can contain similar `names` between them, so to avoid collisions, we use the **scope resolution operator** to differentiate between them.
### `using`
1. **Type aliasing:** Similar to the traditional typedef but offers a more intuitive syntax.
```cpp
using IntPtr = int*; 
using doble = double; 

doble a = 2.4;
```
2. **Importing namespace:** In C++, libraries can contain similar *names* between them, for thatYou can use `using` to bring specific names from a namespace into the current scope, which helps avoid typing the full namespace each time.