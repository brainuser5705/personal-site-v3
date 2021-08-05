---
title: Pointers Basics in C
layout: post
tag: c
categories: programming
---

*I am currently learning pointers in my C journey. It was a bit hard to grasp at first, especially when tutorials omit key concepts. I did more studying and looked at other references, so here is my best attempt at explaining how pointers work in C.*

*If you find any errors, please leave an issue of the Github repository.*

---
Pointers are **variables that reference other variables by storing their memory address**. 

## Declaring a pointer
```c
int *x; // a pointer called 'x' that will point to an integer value
```
---
## Allocating a pointee (or memory) to the pointer.
```c
x = (int*) malloc(sizeof(*int)) 
// dynamically allocates byte size of integer type to pointer 'x'
```
- `malloc()` from `stdlib.h` will return a pointer to the memory allocated.
- pointee and memory are interchangeable, I will be using both terms synonymously
- view a similar example in Java [below](#java-analogy)

---
## Deferencing  
The *deference operation* can be used for 
1. looking at the pointee's state/value
2. setting the pointee's state/value

You are accessing the actual state/value at the memory address the pointer stores. The deference operation will start at the pointer, get the memory address, and finally get the state/value.  
**To deference, you put an asterisk (*) in front of the pointer.**

*You can only deference a pointer if it has a pointee!!!* Otherwise, there will be a [segmentation fault](https://en.wikipedia.org/wiki/Segmentation_fault) error.

```c
*x = 42; // setting pointer to a constant value
print("Deferencing pointer x will give us %i", *x);
```
```
>> Deferencing pointer x will give us 42
```

<br>
**You can also deference a pointer to a variable value**.  
In this case, you would need to use the *`&` (address of) operator*. Putting this in front of a variable will return its memory adress. This can then be stored into the pointer. 

```c
int v; // variable
int *y; // pointer

y = &v; // assigning the memory address to pointer
v = 69;

print("Deferencing pointer y will give us %i", *y);
```
```
>> Deferencing pointer y will give us 69
```

There are a couple important things to note:  
1. We don't need to put an asterisk in `y = &v;` because we are not deferencing the pointer. Instead we are storing the memory address in the pointer itself.   
**In other words, using `*y` would refer to the actual state/value after deferencing whereas `y` would refer to the memory address stored.**
2. You can assign the value of the variable after assigning the memory address. Value is separate from address.
3. You do not need to allocate memory with `malloc()` for `y` because the memory comes from the variable `v`. 

---
## Pointer Assignment 
```c
y = x // now y will point to the same pointee as x

print("Deferencing pointer x will give us %i", *x);
print("Deferencing pointer y will give us %i", *y);
```
```
>> Deferencing pointer x will give us 42
>> Deferencing pointer y will give us 42
```

Again, there is no need to use the `*` because we are assigning memory addresses not values. Nor do we need to use `&`, we are getting the address the pointer is storing not getting the address of the pointer itself.

---
## Java Analogy
For anyone who is familiar with Java, I think this example from [Stanford's CS Library](http://cslibrary.stanford.edu/106/) will make the concept of allocating a pointee clearer. 
Java doesn't have pointers explicitly like C/C++ and other languages, but pointers take from a concept well known in Java called *referencing*. 

When working with classes and objects, you need to make variables that store the object. Or more technically, variables that stores a *reference* to the object. This is the same with pointers: pointers are variables that store references.

```java
/**
    This class represents a pointee (or memory space).
*/
class IntPointee(){
    int value;

    public IntPointee(int value){
        this.value = value;
    }
}

/**
    Main class
*/
class Main(){
    public static void main(String[] args){
        IntPointee x; // the pointer

        x.value = 42; // INVALID! - pointer has no reference to any pointee object

        x = new IntPointee(); // allocate pointee to pointer

        x.value = 42; // VALID!

        IntPointee y;
        y = x; // y and x will now refer to the same IntPointee object
        // this is similar to pointer assignment
        
    }
}
```

**Notes on References VS Pointers**

- Stanford CS Library says 
    >"reference" implies a more high-level discussion, while "pointer" implies the traditional compiled language implementation of pointers as addresses

    essentially saying that pointers are the implementation of the concept of references.
- [Geeks for Geeks article](https://www.geeksforgeeks.org/is-there-any-concept-of-pointers-in-java/)

---

I will updating this blog with more information as I read and experiment more with pointers.