---
title: The update/draw cycle
weight: 40
---
In Pygame Zero, as with most game engines, the code that manages the game state is separate from the code that handles the display. In Pygame Zero, there are two main functions:
- `update()`, which responds to inputs and manages the game state, and
- `draw()`, which coordinates updating the screen to match the game state.

{{< mermaid stateDiagram-v2 >}}
  stateDiagram-v2
  direction LR
    [*] --> update()
    update() --> draw()
    draw() --> update()
{{< /mermaid >}}

Where possible, these two functions will be run, update then draw, update then draw, 60 times per second. Sometimes, however, the computer gets busy running another task in the background, or the code involved in drawing the screen takes longer than usual, and it isn't possible to run `draw()` sixty times per second. If it only runs 58 times, or 51 times, it won't make a particular difference, as anything faster than about 25 times per second will look smooth and continuous. The objects on the screen will still move smoothly, you just mightn't get as many updates in a second as planned.

But humans are very good at anticipating timing, so if the game engine runs irregularly, it will affect the behaviour of moving objects, and the player will more likely notice. Consider what would happen if a person were to walk at a consistent pace from one side of the oval to the other, and you had your eyes closed, but opened them once every couple of seconds. You'll quickly form an idea of their path in your mind, and will be able to accurately predict where they'll be next time you open your eyes, whether you wait two seconds or four. So it is when the `draw()` function is run irregularly. But now imagine the person walking changes their speed, sometimes pacing faster, other times slower, perhaps pausing for just a fraction of a second here and there. You will now find it extremely hard to predict their motion, no matter how much of the time you have your eyes open. This is what it would be like if `update()` ran irregularly, and is much more disruptive to the user.

You can imagine, too, that if you were to design a simple multiplayer game, the server would be the one to `update()` the game state, but if it were a dedicated server it would have no screen to draw on. And each of the player computers would receive the game state from the server, and use it to `draw()` to their screens, but wouldn't have to ever run the update function.