# Storage Duration

- In C++ there are four types of storage durations.

> **automatic storage duration**

- It is allocated at the beginning of the enclosing code block and deallocated at the end.
- All local objects have this storage duration, except those declared static, extern or thread_local.

> **static storage duration**

- It is allocated when the program begins and deallocated when the program ends.
- Only one instance of the object exists.

> **thread stroage duration**

- It is allocated when the thread begins and deallocated when the thread ends.
- Each thread has its own instance of the object.
- Only objects declared thread_local have this storage duration.
- thread_local can appear together with static or extern to adjust linkage.

> **dynamic storage duration**

- It is allocated and deallocated upon request by using dynamic memory allocation functions such as new, delete etc.

# Linkage

- When you write an implementation file, compiler generates a translation unit. This is the source file from your implementation plus all the headers you #included in it.
- A translation unit refers to an implementation (.c/.cpp) file and all header (.h/.hpp) files it includes. 
- In general, linkage will refer to the visibility of symbols to the linker when processing files. Linkage can be either internal or external.

> **no linkage**

- Identifiers can only be seen in the scope in which they are defined. 
- Linkage does not affect scoping.

> **internal linkage**

- Identifiers can only be seen within a translation unit.
- static, const, constexpr objects have internal linkage by default

> **external linkage**

- Identifiers can be seen (and referred to) in other translation units.
- Functions, non-const global variables have external linkage by default or use extern keyword