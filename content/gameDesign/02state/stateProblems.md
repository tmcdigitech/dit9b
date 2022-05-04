---
title: Problems with state
weight: 30
---
## Keep it simple
Broadly speaking, the more state your program has, the more complex it is, and thus the more opportunities there are for mistakes. This should encourage us to look for a solution with as little state information as possible. As a simple example, in a fighting game, it is important to know whether a character is alive or dead, and how much health they have. So you might think to have an integer to keep track of health, and a couple of boolean flags to keep track of the character's life status:
```python
    health: int
    isAlive: bool
    isDead: bool
```
But on inspection, you don't need all this. First of all, a character in a game is usually either alive or dead, but not both or neither, so you could just have one of the boolean values, and look for `isAlive` or `not isAlive`. But actually, since you also have a `health` variable, it will likely work if you just check to see whether or not `health > 0`, and not need either of the boolean flags. It will depend on your specific project what things you can and can't do, but this is a general thing to think about, as it is easy to over-complicate your project by accident, allowing bugs to creep in!

## What wrong looks like
If you've spent much time playing computer games, you've probably seen the side-effects of problems with a game's state.

If you've ever played a first person shooter (FPS) or a role-playing game (RPG) and found yourself "stuck" in a wall, or a rock, or with your feet below the floor level, then you've entered a state that shouldn't be possible.

RPGs such as those from the Elder Scrolls, Mass Effect or Fallout series have a lot of state tied up in whether or not you've completed a certain mission, made a particular decision, or spoken to, saved or killed a certain character. So there are often dozens, even hundreds, of boolean flags keeping track of all this. Under these circumstances it is easy for the programmers to forget, when one checkpoint is cleared, to enable or disable one of the flags, which will lead to things like a subsequent mission not being available even though the previous one has been completed, or a character refusing to offer a conversation option, or being hostile when they shouldn't, or a thousand other ways this could play out.

## Multiplayer challenges
Multiplayer games played on the one computer, such as split-screen console games, are not much more complicated than single player games; there are just more input devices to work through. Multi-system games, such as games played over LAN or the Internet, are *much* nastier to manage, however.

In a multi-system game, there is almost always a *server*, which manages the game, and then a series of *clients*, which are the player computers. The server can be either:
- a dedicated machine for running the game, which is the case for most games played over the internet, or
- one of the player computers, which "hosts" the game, and fulfils the role of the server as well as being a client for one of the players. This arrangement is more common for computers played over a local network.

Many games, such as Minecraft, can be set up in either way. In both cases it is the server which is in charge of maintaining and updating the state of the game, which it then distributes to the other machines. The more game state there is, the longer it will take to send to the other players. Large games will typically find ways to reduce the amount of game state that is required to be sent at a time, and minimise the people who need it.

In World of Warcraft, for example, breaking the world up into smaller regions means that a player in one area doesn't need updates on anything happening in another area, so they need relatively little information, and there will be relatively few players in each region, compared with the world overall, so that information only needs to go to a few players. This is one of the reasons that game performance in the big cities of WoW can take a noticable dive: there are now far more people in the one place, meaning there is much more game state to distribute, and far more people to distribute it to, and handle moves from.

In an online game of something like chess or Uno, a delay of even several seconds between moves wouldn't make any significant difference to the success of the game. Moves take quite a while anyway, a little transmission delay is no big thing. But in a first person shooter, delays in transmission cause big problems.

If an update hasn't come from the server in time, the player computer can choose either to wait until it gets one, creating stutters and freezes in the game, or it can run the simulation locally with only the input it is getting, leading to other players running at walls or standing around awkwardly. The latter is usually better for dealing with small delays, as it keeps the game smooth for the player, and hopefully the game can get everything back on track before anything weird happens. 

The longer the delay between state updates, the more likely the local copy of the state is to be wrong, and the greater the difference is likely to be. You can see the effects of this if, often after a brief stutter, either you or another player suddenly "teleports" to a slightly different location.

From the server's perspective, in a FPS it has a tight window to get the move data from the clients, update the game state, and distribute the new game state, if it wants to keep the game running smoothly. If an update doesn't arrive from a client in time, rather than waiting indefinitely and causing a freeze, the server will probably assume there is no new information from the client and proceed. If it continues to have substantial problems repeatedly with the same client, a server sometimes is programmed to give up and "kick" the client from the game, in the hope that the game can continue to run smoothly for everyone else.