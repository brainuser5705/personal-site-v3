---
layout: post
title: "makes: Making Pong with Pygame"
categories: programming
---

**This is not a tutorial on how to make Pong.**

Today I follow through [Real Python's "A Primer to Pygame"](https://realpython.com/pygame-a-primer/) and decided to make Pong to exercise my newfound skills. There is a plethora of Pygame Pong tutorials on the Interweb, so maybe my implementation is inefficient. But anyways, I didn't stray much from the functions and classes the tutorial showed. The result program is pretty simple, no fancy features: two pong players, the ball and tally score keeping.

![](https://i.imgur.com/QdbACZv.png)

I am writing this blog mainly for myself. This was a one day project (more of an exercise actually) and I know I will forget how to use the library in short time. So as a way to slow that forgetting curve, I thought I'll make a quick rundown of Pygame and my program so I can read back if I ever need to use Pygame again.

---

*The following pictures do not represent the entire program. You can view the Github repository [here](https://github.com/brainuser5705/py-game-pong)*.

## Game Loop
<div style="float: left;">
<img src="https://i.imgur.com/aSGL5Qn.png" height="150px" style="float: left; margin-right: 10px">
This keeps the Pygame window open. It looks for events in the event queue and checks if the window is quit.
</div>

## Sprite Classes
<div style="float: left;">
<img src="https://i.imgur.com/FHWnE1C.png" height="200px" style="float: left; margin-right: 10px">
Custom classes that extend from <code>pygame.sprite.Sprite</code> class. In the <code>__init__</code> constructor, you create a <code>Surface</code> object and get the <code>rect</code> which you can then move.
</div>

## Updating
<div style="float: left;">
<img src="https://i.imgur.com/nMHXQlB.png" height="200px" style="float: left; margin-right: 10px">
Like Processing, the game loops through frames. You need to clear the screen with <code>screen.fill()</code> and use the <code>update()</code> functions of the sprite classes. Theses functions move the sprite's <code>rect</code> depending on key events. You can then use the <code>blit()</code> function to "transfer" the sprite's surface onto the screen (which is also a Surface object).
</div>


## Sprite Group
<div style="float: left;">
<img src="https://i.imgur.com/eOoEk0S.png" height="200px" style="float: left; margin-right: 10px">
<img src="https://i.imgur.com/7s9EnBs.png" height="140px" style="float: left; margin-right: 10px">
You can put sprites into sprite groups. You can then access the sprites through these groups for different reasons such as exclusively for rendering, moving, or collisions.
</div>
 

## Collision
<div style="clear: right;">
<img src="https://i.imgur.com/yiY2nXH.png" height="90px" style="float: left; margin-right: 10px;">
Pygame provides functions for collisions.
</div>
<br>

## Other features
- <code>pygame.mixer</code>  for sound effects
- You can also load images as the sprite's surface.

---   
### Additional notes:

This was also a life exercise. I am trying to overcome perfectionsim especially when programming. Instead of waiting for the "right time", I delve into this project straight in. And to avoid stressing out efficiency, I approach it in the "hacker mentality" where you're aiming for MVP (minimum viable product) and the goal is "do now, fix later". I ended up with working code; it's not perfect but it works as intended.



