---
title: "c: Preprocessor Directives"
layout: post
tag: c
categories: programming
---

## #define
**literal text substitution of tokens** *(except in character strings because it is a single token itself)*

```c
#define NAME    value

// use case: variables
//notice no semicolon in definition
#define VARIABLE    x 
int x = 10;
printf("%i", VARIABLE);

// order does not matter as long as everything is defined before use
// also the expression is not computed during preprocessor time, just substituted
#define TWO_PI  2*PI 
#define PI      3.1415927

// multiline definition
#define GREETING Hello there! \
How are you?
```

## #define with arguments
```c
// don't need to define types of argument
#define ADD_TWO(x)  (x) + 2

// variable number of arguments
// string concatentation: "a" "b" == "a" + "b"
#define debugPrintf(...)    printf("DEBUG:" __VA_ARGS__);
int x = 100, z = 200;
debugPrintf("x = %i, z = %i\n", x, z)
```

## # and \##
```c
// #
// will wrap quotations marks around the argument
// use case:
#define PRINTVAR(var)   printf("%s: %i", #var, var)
int count = 10;
PRINTVAR(count);

// ##
// concatenate two token together
// note definitions take the arguments as literal, so passing in variables will not work
// use case:
#define PRINTVAR(var)   printf("%s: %i", "x" #var, x ## var)
int x1 = 0, x2 = 1;
PRINTVAR(1); // print out x1
PRINTVAR(2);
```
## #include
Looks for specified file and copies content at the precise point of the directive

- **"file.h"** : looks for file starting in the same directory as the source file  
- **<file.h>** : looks for file in special system include file directories (system-dependent, *Linux: `\usr\include\`*)

## #ifdef, ifndef

```c
// include guard: do this to avoid multiple inclusion when nesting include files
#ifndef FILE_H
#   define FILE_H
#   define NAME     value
#endif
```

You can define the macro in the file:
```c
#define FILE_H
#ifndef FILE_H
...
```
OR during in the compilation process:
```bash
gcc ... -D FILE_H ...
#OR
gcc ... -D FILE_H=1 ...
```
## #if, #elif, #else
```c
#if define(FILE_H)
#define NAME    value   // notice there is no space
#elif VARIABLE == 1
#define NAME2   value2
#endif
```

## #undef
```
// use this to undefine a macro
#undef FILE_H
```