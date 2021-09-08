---
title: Working with the cs.rit.edu Machines
layout: post
categories: other
---

## **Background**
I am currently a second year computer science student at the Rochester Institute of Technology and one of the major courses I have to take is [Mechanics of Programming](https://www.rit.edu/study/curriculum/c9e1894b-50fa-4753-9918-dfbe7e7cdfe6). As part of the course, we do all our work in C with the `cs.rit.edu` servers via SSH. Here is a list of some "tips and tricks" that I have discovered while working in these machines.

## **Tips and Tricks**
1. The machines have some weird [names](https://pastebin.com/G6SCmVc7). You can stick with the popular `glados.cs.rit.edu` or avoid wait time with a lesser known one like `wallofvoodoo.cs.rit.edu`

2. You are not limited to your user directory! Keep typing `cd ..` and eventually you'll reach the root directory of the server. On the same note, the C library include files are stored in `/usr/include`.

3. In the first assignment, you must create an organization structure for all your homeworks and such. Instead of typing in `cd Courses/CS243/Homeworks` every time, you can **set an alias**. In the root of your user directory, edit your `.bashrc` file and add this line: `alias <alias_name>='<homework_directory>'`, replacing the `<>` with your own values.

4. Also in the first assignment, you had to set up your `.vimrc` file to configure Vim. Later on when you want to make Makefiles with Vim, it will produce a *missing separator* error because of some whitespace issue. To get rid of this problem, comment out the `expandtab` setting in your `.vimrc` file.

---

*This post will be continually updated as I learn and discover more about these machines, the C languages and the UNIX environment.*