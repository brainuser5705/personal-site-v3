---
layout: post
title: Installing a C compiler
tags: C 
categories: programming
---

Right now I am starting my C journey. Last month, I spent around 2 to 3 weeks going through *Kochan's Programming in C* book but haven't touch the language since then.

My first step is installing C. I am using Windows as my default operating system. Although I do have Ubuntu installed as a dual boot system, I chose Windows because I am more familiar with it (I will learn how to use Linux in the future). That means instead of having the C compiler and other tools all readily available for me, I will have to do some research.

**Here is what I did with some additional notes for each step:**
1. Install Mingw64 for the gcc compiler and gdb debugger. [Tutorial](https://azrael.digipen.edu/~mmead/www/public/mingw/) 
2. Add it to my PATH so I can execute the gcc command via Command Prompt. [Tutorial](https://www.computerhope.com/issues/ch000549.htm)
    -  Add the file directory path of the `bin` folder. In my case, it was `C:\Program Files\mingw\mingw64\bin`.
3. Configure C/C++ compilation and debugging on Visual Studio Code.
    - `tasks.json` for compilation
        - Go to *Terminal > Configure Default Build Task* and select *g++*.
        - the `args` property is the commands the terminal will run to build the `.exe` file
        - you can change the destination path of the `.exe` file by changing `"${fileDirname}\\${fileBasenameNoExtension}.exe"`
    - `launch.json` for debugging configuration
        - Go to *Run > Add Configurations* and select *g++*.
        - change `"stopAtEntry"` to true so the debugger will stop at the first line of the main method
    - `c_cpp_properties.json` for setting which compiler to use, etc. 
    - the [tutorial](https://code.visualstudio.com/docs/cpp/config-mingw#_debug-helloworldcpp) contains a more detailed walkthrough

Now I am able to create C/C++ programs and compile them with the `gcc` command in the Command Prompt and also with Visual Studio Code. 

---
**When researching, I came upon different methods of installing a C compiler.** 

You can either:

1) Install a UNIX emulator like Cygwin or MSYS2.
- You are able to run Unix applications with these emulators/ports on Windows.
- It will also come with a Bash shell.
- Along with everything else, you will also get gcc and gdb.

2) Install MinGW, a port for GNU development tools (gcc, gdb, etc.) to Windows.
- This will include the tools, along with the header files for the C language (and other languages associated with gcc). 
- It will compile the C code into a Windows executable so it can be natively run.

*Note:* I did not look too intensively into this topic. This is what I have gathered and interpreted from reading various websites. You can read [this StackOverflow thread](https://stackoverflow.com/questions/771756/what-is-the-difference-between-cygwin-and-mingw) for more information.