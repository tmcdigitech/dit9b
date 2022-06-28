---
title: Drawing graphics (slides)
weight: 31
outputs: ['Reveal']
layout: list
reveal_hugo:
    theme: sky
    transition_speed: fast
    highlight_theme: monokai
    reveal_cdn: https://cdnjs.cloudflare.com/ajax/libs/reveal.js/3.9.2
    # highlight_cdn: https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.5.1/
---

## Drawing graphics

*adapted from [Coding Games with Pygame Zero & Python, by Richard Smith](https://electronstudio.github.io/pygame-zero-book/chapters/graphics.html)*

---

The smallest square that can be displayed on a monitor is called a pixel. This diagram shows a close-up view of a window that is 40 pixels wide and 40 pixels high. At normal size you will not see the grid lines.

{{< figure src="/dit9a/gameDesign/02basics/graphics/grid.png" height="300" >}}

---

We can refer to any pixel by giving two co-ordinates,

`(x, y)`

Make sure you understand co-ordinates before moving on because everything we do in Pygame Zero will use it. (In maths this called a *Cartesian coordinate system*).

---

## Lines and circles
If are using the Mu editor, Pygame Zero is built-in, **but you must remember to click ‘Mode’ and select ‘Pygame Zero’ before running your program**!

If you are using a different editor, [instructions are online](https://pygame-zero.readthedocs.io/en/stable/ide-mode.html).

---

Copy the following code into a new file, and see what it creates.

```python
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

---

#### Exercise

Using these three functions, now draw your own picture.

---

## Moving rectangles
To make things move we need to add the special `update()` function. We don’t need to write our own loop because *Pygame Zero calls this function for us in its own loop*, over and over, many times per second.

---

Copy the following code into a new file, and see what it creates.

```python
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

---

#### Exercise

Make the box move faster.

---

#### Exercise

Make the box move in different directions.

---

#### Exercise

Make two boxes with different colours.
