---
title: Drawing graphics
weight: 30
---
*adapted from [Coding Games with Pygame Zero & Python, by Richard Smith](https://electronstudio.github.io/pygame-zero-book/chapters/graphics.html)*

To create graphics for our games we will use the [Pygame Zero library](https://pygame-zero.readthedocs.io/en/stable/). You will find the documentation on the website useful!

The smallest square that can be displayed on a monitor is called a pixel. This diagram shows a close-up view of a window that is 40 pixels wide and 40 pixels high. At normal size you will not see the grid lines.

{{< figure src="grid.png" title="Pixel grid" >}}

We can refer to any pixel by giving two co-ordinates, `(x, y)`. Make sure you understand co-ordinates before moving on because everything we do in Pygame Zero will use it. (In maths this called a *Cartesian coordinate system*).

## 4.1. Lines and circles
If are using the Mu editor, Pygame Zero is built-in, **but you must remember to click ‘Mode’ and select ‘Pygame Zero’ before running your program**!

If you are using a different editor, [instructions are online](https://pygame-zero.readthedocs.io/en/stable/ide-mode.html).

*Program 4.1 Lines and circles*
```python {linenos=table}
WIDTH = 500  # What are these units? What if we change them?
HEIGHT = 500  # What if we delete this line?


def draw():
    screen.clear()
    screen.draw.circle((250, 250), 50, "white")
    screen.draw.filled_circle((250, 100), 50, "red")
    screen.draw.line((150, 20), (150, 450), "purple")
    screen.draw.line((150, 20), (350, 20), "purple")
```
#### Exercise

Finish drawing this picture.

#### Exercise

Draw your own picture.


## 4.2. Moving rectangles
To make things move we need to add the special `update()` function. We don’t need to write our own loop because *Pygame Zero calls this function for us in its own loop*, over and over, many times per second.

Program 4.2 Moving rectangles
```python {linenos=table}
WIDTH = 500
HEIGHT = 500

box = Rect((20, 20), (50, 50))

def draw():
    screen.clear()
    screen.draw.filled_rect(box, "red")


def update():
    box.x = box.x + 2
    if box.x > WIDTH:
        box.x = 0
```
#### Exercise

Make the box move faster.

#### Exercise

Make the box move in different directions.

#### Exercise

Make two boxes with different colours.

## 4.3. Actor sprites
Actor sprites are very similar to boxes! Click `Images` to see the folder of image files available. `alien.png` should already be there, but for other images you must add the files yourself.

You could use Microsoft Paint which comes with Windows but I recommend you download and install [Krita](https://krita.org/).

*Program 4.3 Actor sprites*
```python {linenos=table}
WIDTH = 500
HEIGHT = 500

alien = Actor('alien')
alien.x = 0
alien.y = 50


def draw():
    screen.clear()
    alien.draw()


def update():
    alien.x += 2
    if alien.x > WIDTH:
        alien.x = 0
```
#### Exercise

Draw or download your own image to use instead of alien.


## 4.4. Background image
We are going to add a background image to Program 4.3.

Click `Images` to see the folder of image files available.

**You must create or download a picture to use a background**. Save it as `background.png` in the directory that opens when you click `Images`. It should be the same size as the window, 500×500 pixels and it must be in `.png` format.

*Program 4.4 Background*
```python {linenos=table}
WIDTH = 500
HEIGHT = 500

alien = Actor('alien')
alien.x = 0
alien.y = 50

background = Actor('background')

def draw():
    screen.clear()
    background.draw()
    alien.draw()


def update():
    alien.x += 2
    if alien.x > WIDTH:
        alien.x = 0
```
#### Exercise

Create a picture to use a background. Save it as `background.png`. Run the program.

