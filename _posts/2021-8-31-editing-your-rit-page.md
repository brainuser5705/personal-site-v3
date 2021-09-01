---
title: Editing your RIT page
layout: post
categories: other
---

Most students at RIT don't know that they have their own personal website domain at https://people.rit.edu/~your-rit-id.  

I was on that boat until yesterday. Here's a quick rundown on how I discovered it:
I went to one of the ICLs and found out that, in your CS account user directory (every CS student gets a cs.rit.edu account), there is a subdirectory labelled `public_html`. Having some experience with making a LAMP stack, I had an inkling that it would hold some sort of website. Familiar with the domains for various RIT CS webpages, I confirmed it by typing out https://cs.rit.edu/~my-rit-id. It loaded, but because of permissions, I was forbidden to see it. So I did some googling (as one always does when one encounters problems), and found out about the *people.rit.edu* domain. Consequently, I tried out https://people.rit.edu/~rit-id and it worked, but it was an empty directory.

RIT Web Services provides documentation for using your people.rit.edu domain which specifically used WINScp. I had recently "learned" to use ssh in MOPS (short for Mechanics of Programming which is a course for computer science majors at RIT), I decided to log in through the terminal instead. And it worked. 

**Something interesting though**
You are actually in the machine, not in some user directory (I am not well versed with Linux so this might be a wrong insight). That means I can move back to the root directory of the machine. And virtually, access every other student's personal directory (not edit however). 

You can then enter your `www` directory and add your HTML files to make your website!

