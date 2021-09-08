---
title: "c: typedefs"
layout: post
tag: c
categories: programming
---

Typedefs are used for *assigning an alternate name to existing types*. 

**How to make a typedef:**
1. Write the declaration as normal.
2. Substitute in the new type name where the variable name would have been.
3. Put `typedef` in front of the declaration.

## **Initialization**
```c
typedef int Counter;

//this is equivalent to:
#define Counter int
```

```c
typedef char * Linebuf[81];

//now you can do this:
// text will now be a character array with length of 81.
Linebuf text = {...};
```
