---
title: Wrapping the screen
---

In some games, when the player or certain objects move off one edge of the screen, they re-emerge on the opposite edge.
This can be achieved using the following block of code, placed inside the `Update()` method of an object's script.

The `margin` property can be tuned according to preference. The object must go past the edge of the margin, not just the screen,
to be teleported to the other edge.

![margin around the edge of the screen](../screenWithMargin.svg)

```cs
        //Handle screen wrapping
        //Find out where we are on the screen
        int margin = 50;
        Vector2 screenPos = Camera.main.WorldToScreenPoint(transform.position);
        //See if we've moved off any of the four edges
        if( screenPos.x > Screen.width+margin ){
            //off right, move to left
            screenPos.x = -margin;
        }else if( screenPos.x < -margin ){
            //off left, move to right
            screenPos.x = Screen.width+margin;
        }
        if( screenPos.y > Screen.height+margin ){
            //off bottom, move to top
            screenPos.y = -margin;
        }else if( screenPos.y < -margin ){
            //off top, move to bottom
            screenPos.y = Screen.height+margin;
        }
        //Update our world position based on our new screen position
        Vector3 newPos = Camera.main.ScreenToWorldPoint(screenPos);
        transform.position = new Vector2(newPos.x, newPos.y);
```
