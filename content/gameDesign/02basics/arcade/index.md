---
title: Arcade games
weight: 40
---
*adapted from [Coding Games with Pygame Zero & Python, by Richard Smith](https://electronstudio.github.io/pygame-zero-book/index.html)*
## Keyboard input
The alien moves when you press the cursor keys.

Program 4.5 Keyboard input
```python {linenos=table}
alien = Actor('alien')
alien.pos = (0, 50)

def draw():
    screen.clear()
    alien.draw()

def update():
    if keyboard.right:
        alien.x = alien.x + 2
    elif keyboard.left:
        alien.x = alien.x - 2
```
### Exercise

Make the alien move up and down as well as left and right.

### Exercise

Use the more concise += operator to change the alien.x value.

### Exercise

Use the or operator to allow WASD keys to move the alien in addition to the cursor keys.

## 5.1. Collisions
Arcade games need to know when one Actor sprite has hit another Actor sprite. Most of this code is copied from Program 4.2 and Program 4.5.

Program 5.1 Collisions
```python {linenos=table}
WIDTH = 500
HEIGHT = 500

alien = Actor("alien")
alien.pos = (400, 50)
box = Rect((20, 20), (100, 100))

def draw():
    screen.clear()
    screen.draw.filled_rect(box, "red")
    alien.draw()

def update():
    if keyboard.right:
        alien.x = alien.x + 2
    elif keyboard.left:
        alien.x = alien.x - 2
    box.x = box.x + 2
    if box.x > WIDTH:
        box.x = 0
    if alien.colliderect(box):
        print("hit")
```
### Exercise

Add vertical movement (as you did in Exercise Program 4.5).

### Exercise

Make the box chase the alien.

### Exercise

Print number of times the box hits the alien (i.e. the score).

5.2. Chase
Instead of moving constantly to the right we can make the movement conditional with an if statement so the box chases the alien. Most of this code is copied from Program 5.1. New lines are highlighted. We have also changed what happens when the box catches the alien: the program now exits and you must run it again to play again. This may not be what you want in your game!

Program 5.2 Alien chase
{{< highlight python "lineNos=table,lineNoStart=1,hl_lines=18-23" >}}
WIDTH = 500
HEIGHT = 500

alien = Actor("alien")
alien.pos = (400, 50)
box = Rect((20, 20), (100, 100))

def draw():
    screen.clear()
    screen.draw.filled_rect(box, "red")
    alien.draw()

def update():
    if keyboard.right:
        alien.x = alien.x + 2
    elif keyboard.left:
        alien.x = alien.x - 2
    if box.x < alien.x:
        box.x = box.x + 1
    if box.x > alien.x:
        box.x = box.x - 1
    if alien.colliderect(box):
        exit()
{{< /highlight >}}
### Exercise

Add vertical movement (as you did in previous exercise).

### Exercise

Draw a new enemy image. Save it as enemy.png in your mu_code/images folder. Load it as an Actor(‘enemy’) instead of the Rect().

## 5.3. Powerup
Instead of an enemy the box here is a powerup that the player must collect. When he does it disappears and moves to a new location.

Program 5.3 Collect the powerups
```python {linenos=table}
WIDTH = 500
HEIGHT = 500
import random

alien = Actor("alien")
alien.pos = (400, 50)
box = Rect((20, 20), (100, 100))
score = 0

def draw():
    screen.clear()
    screen.draw.filled_rect(box, "green")
    alien.draw()

def update():
    global score
    if keyboard.right:
        alien.x = alien.x + 2
    elif keyboard.left:
        alien.x = alien.x - 2
    if alien.colliderect(box):
        box.x = random.randint(0, WIDTH)
        box.y = random.randint(0, HEIGHT)
        score = score + 1
        print("Score:", score)
```
### Exercise

Add vertical movement (as you did in Exercise ref{exercise:updown}).

### Exercise

Draw a new powerup image. Save it as powerup.png in your mu_code/images folder. Load it as an Actor(‘powerup’) instead of the Rect().

### Advanced

Combine this program with the enemy from Program Program 5.2 and the background from Program 4.4 and whatever else you want to make your own game.


## 5.4. Sound and animation
Pygame Zero comes with one other image alien_hurt.png and one sound eep.wav. If you want more you will have to add them to the sounds and images folders.

Most of this code is copied from Program 5.1

Program 5.4 Sound and animation upon collision
{{< highlight python "lineNos=table,lineNoStart=1,hl_lines=19-24" >}}
WIDTH = 500
HEIGHT = 500
alien = Actor("alien")
alien.pos = (0, 50)
box = Rect((20, 20), (100, 100))

def draw():
    screen.clear()
    screen.draw.filled_rect(box, "red")
    alien.draw()
def update():
    if keyboard.right:
        alien.x = alien.x + 2
    elif keyboard.left:
        alien.x = alien.x - 2
    box.x = box.x + 2
    if box.x > WIDTH:
        box.x = 0
# PLAY SOUND AND SHOW IMAGE WHEN HIT
    if alien.colliderect(box):
        alien.image = 'alien_hurt'
        sounds.eep.play()
    else:
        alien.image = 'alien'

{{< /highlight >}}
### Exercise

Record your own sound effect and add it to the game.

### Advanced

Add more boxes or sprites that move in different ways for the player to avoid.

### Advanced

Add a second alien controlled by different keys or gamepad for player 2.


## 5.5. Mouse clicks
This uses a function call-back for event-based input. It is similar to Program 5.4 but:

The box has been removed.

There is an on_mouse_down() special function that is called automatically when the player click the mouse.

The score is displayed.

See Program 2.17 for more about functions.

Program 5.5 Getting input from mouse clicks
```python {linenos=table}
alien = Actor("alien")
alien.pos = (0, 50)
score = 0

def draw():
    screen.clear()
    alien.draw()
    screen.draw.text("Score "+str(score), (0,0))

def update():
    if keyboard.right:
        alien.x = alien.x + 2
    elif keyboard.left:
        alien.x = alien.x - 2
    alien.image = 'alien'

def on_mouse_down(pos, button):
    global score
    if button == mouse.LEFT and alien.collidepoint(pos):
        alien.image = 'alien_hurt'
        sounds.eep.play()
        score = score + 1
```

## 5.6. Mouse movement
Program 5.6 Getting input from mouse movement
# wiggle your mouse around the screen!
```python {linenos=table}
alien = Actor("alien")

def draw():
    screen.clear()
    alien.draw()

def on_mouse_move(pos):
    alien.pos = pos
```
### Exercise

What happens if you delete line 8 and replace it with this:

animate(alien, pos=pos, duration=1, tween='bounce_end')

### Exercise

What happens if you change on_mouse_move to on_mouse_down?

### Advanced

Make a game with one alien controlled by mouse and another controlled by keyboard




