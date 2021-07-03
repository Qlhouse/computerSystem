Stack and heap are both stored in the computer's RAM.

# Threads interact with stack and heap

In a multi-thread application, each thread have its own stack. But, all the different threads will share the heap. Because the different threads share the heap in a multi-threaded application, this also means that there has to be some coordination between the threads so that they don't try to access and manipulate the same piece(s) of memory in the heap at the same time.

# Can an object be stored on the stack instead of the heap?

An object can be stored on the stack. If you create an object inside a function without using the `new` operator then this will create and store the object on the stack, and not on the heap.

## Create an object on the stack 

```c++
void somefunction( )
{
/* create an object "m" of class Member
    this will be put on the stack since the 
    "new" keyword is not used, and we are 
   creating the object inside a function
*/
  
  Member m;

} //the object "m" is destroyed once the function ends
```

The object `m` is destroyed once the function has run to completion --- or in other words, when it "goes out of scope". The memory being used for the object `m` on the stack will be removed once the function is done running.

## Create an object on the heap

```c++
void somefunction( )
{
/* create an object "m" of class Member
    this will be put on the heap since the 
    "new" keyword is used, and we are 
   creating the object inside a function
*/
  
  Member* m = new Member( ) ;
  
  /* the object "m" must be deleted
      otherwise a memory leak occurs
  */

  delete m; 
} 
```

The `m` object is created inside a function using the `new` keyword. This means that `m` will be created on the heap. But since `m` is created using the `new` keyword, that also means that we must delete the `m` object on our own as well --- otherwise we will end up with a `memory leak`.

# How long does memory on the stack last versus memory on the heap?

Once a function call runs to completion, any data on the stack created specifically for the function call will automatically be deleted. Any data on the heap will remain there until it's manually deleted by the programmer.

# Can the stack grow in size? Can the heap grow in size?

The stack is set to a fixed size, and can not grow past its fixed size (although some languages have extensions that do allow this). So, if there is **not** enough room on the stack to handle the memory being assigned to it, a ***stack overflow*** occurs. This often happens when a lot of nested functions are being called, or if there is an infinite recusive call.

If the current size of the heap is too small to accommodate new memory, then more memory can be added to the heap by the operating system. This is one of the big differences between the heap and the stack.

# How are the stack and heap implemented?

The implementation really depends on the language, compiler, and run-time --- the ***small*** details of the implementation for a stack and a heap will always be different depending on what language and compiler are being used.

# Which is faster - the stack or the heap? And why?

The stack is much faster than the heap. This because of the way that memory is allocated on the stack. Allocating memory on the stack is as simple as moving the stack pointer up.

# How is memory deallocated on the stack and heap?

Data on the stack is ***automatically*** deallocated when variables go out of scope. However, in languages like C and C++, data stored on the heap has to be deleted manually by the programmer using one of the built-in keywords like **free, delete, or delete[]**. Other languages like Jave and Python use garbage collection to automatically delete memory from the heap, without the programmer having to do anything.

# What can go wrong with the stack and the heap?

If the stack runs out of memory, then this is called a *stack overflow* - and could cause the program to crash. The heap could have the problem of *fragmentation*, which occurs when the available memory on the heap is being stored as noncontiguous (or disconnected) blocks - because *used* blocks of memory are in between the unused memory blocks. When excessive fragmentation occurs, allocating new memory may be impossible because of the fact that even though there is enough momory for the desired allocation, there may not be enough memory in one big block for the desired amount of memory.

# Which one should I use - the stack or the heap?

For people new to programming, it's probably a goog idea to use the stack since it's easier. Because the stack is small, you would want to use it when you know exactly how much memory you will need for your data, or if you know the size of your data is very small. It's better to use the heap when you know that you will need a lot of memory for your data, or you just are not sure how much memory you will need (like with a dynamic array)