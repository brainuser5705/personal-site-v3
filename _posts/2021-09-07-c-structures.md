---
title: "c: Structures"
layout: post
tag: c
categories: programming
---

## **Initialization**
```c
// initalize in a variable list
struct point{
    float x;
    float y;
} x, y = {10, 10};

// separate variable declaration and intialization
struct point a;
a.x = 0;
a.y = 0;

// declaration and initalization
struct point b = {0, 0};
struct point c = {.y=20, .x=20};
// in this case, since x was not initialize, its value is set to 0
struct point d = {.y=20};
```

## **Arrays of Structs**
```c
// use any of the array initialization methods
struct person{
    char * name;
    int age;
} people[5] = { [0].name = "Bob", [1].age = 5 };

struct person more_people[2] = {
    {"test", 4},
    {"hello", 5}
};

struct person even_more_people[2] = {"bye", 3, "tim", 5}; 
// this will produce a warning however
```

## **Other Notes**
```c
// You can assign struct to another struct of the same type
struct peeps[2] = even_more_people;
```

```c
// You cannot initalize the structure members inside a struct!
// This is invalid:
struct test{
    int x = 0;
    int y;
    y = 0;
}
```

```c
// You can have unnamed structs:
struct {
    int value;
} test;
```









