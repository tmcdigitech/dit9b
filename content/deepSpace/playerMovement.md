---
title: Player Movement
weight: 20
---
As this is a top-down, space game, we want the x-axis of the player's controls
to rotate the ship, and the y-axis to control the thrusters forward and back.

You might want to limit the controls so the player cannot move backwards, 
meaning they have to turn the ship around to move forwards. We won't worry
about that here.

We set up a script and attach it to the player ship. The complete code is below,
with the added lines highlighted.

Lines 7-9 set up some variables:
- `rotSpeed` (rotation speed) affects how quickly we can turn, while
- `linSpeed` (linear speed) affects how quickly we can accelerate. 
- `rb` is a Rigidbody2D component.

On line 13, we set `rb` to the attached Rigidbody2D component. As this
script is attached to the player object, it will be the player's Rigidbody2D component.

Inside the `update()` function, there are three separate chunks of code:
- line 20 modifies the rotation of the ship according to the controller's x-axis (L+R arrows, W+D keys, left stick on Xbox or PS controller);
- line 23-28 changes the velocity by creating a vector facing up (nominally forwards) scaled to the controller's y-axis, and then rotating it to match the player's current direction;
- line 31-50 handles wrapping the screen so when the player flies off one edge of the screen they re-emerge on the opposite side.

{{< highlight cs "linenos=table,hl_lines=7-9 13 19-50" >}}
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{
    public float rotSpeed;
    public float linSpeed;
    private Rigidbody2D rb;
    // Start is called before the first frame update
    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    // Update is called once per frame
    void Update()
    {
        //Update rotation
        rb.MoveRotation(rb.rotation - Input.GetAxis("Horizontal") * rotSpeed * Time.deltaTime);

        //Update velocity
        Vector3 pos = transform.position;
        float y = Input.GetAxis("Vertical") * linSpeed * Time.deltaTime;

        Vector2 vChange = new Vector2(0, y);
        vChange = transform.rotation * vChange;
        rb.velocity += vChange;

        //Handle screen wrapping
        int margin = 50;
        Vector2 screenPos = Camera.main.WorldToScreenPoint(transform.position);
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

        Vector3 newPos = Camera.main.ScreenToWorldPoint(screenPos);
        transform.position = new Vector2(newPos.x, newPos.y);
    }
}
{{< /highlight >}}