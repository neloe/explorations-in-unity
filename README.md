# explorations-in-unity

## A set of notes during my messing with Unity while prepping for Game Dev

---

### Editors

* VS Community seems to suck; VS Code better/lighter?  Maybve not; need the .NET core 3.1 SDK and suggested extensions; let's see if that's nicer
 * I cannot stress this enough; VS Community is laggy (on faculty laptop), will try vs code next with the appropriate sdk and extensions.


### Scripting

* `GetComponent<T>` gets object that script is attached to
  * Script attached to many objects; script run independent on all objects?
* public member variables are exposed to the object in unity's editor; ***THE UPDATE IS NOT BIDIRECTIONAL, whatever is set in unity's inspector wins***
* Can do `entity.velocity += blah`, but not `entity.velocity.x += blah`; because `Rigidbody2D.velocity` is not a variable?

### Components

* Constant Force 2D is a lie?  (seems to not be ma, but constant downward movement)

### Animation

* Drag animations to sprite
  * Create animation by selecting required sprites and dragging them to scene (simple animation, no keyframe)
  
### Tile Maps

* Adding box colliders to tilemaps dont seem to act like I want them to act
* Can't find rule tile yet in unity 2019
  * Rule tiles can be added with [`2d-extras`](https://github.com/Unity-Technologies/2d-extras); should we introduce these extra tools?
  
### Recording

* OBS seems smoother/easier than VidGrid, even with windows updates doing the windows updates.

### Code Snippets

* Rigidbody2D has an option for gravity; that's obnoxious to find
 * Gravity STILL doesn't accellerate? is my scale too small?

Gravity and jumping; why not
```cs
entity.velocity += Vector2.down*Time.deltaTime*gravity;
Debug.Log(Vector2.down*Time.deltaTime*gravity);

if (Input.GetKeyDown(KeyCode.UpArrow))
    entity.velocity += Vector2.up * moveSpeed;
```

Better/working?
```cs
movement.x = Input.GetAxisRaw("Horizontal");
        movement.y = 0;
        movement.Normalize();
        movement *= moveSpeed;
        movement.y = entity.velocity.y;
        movement += Vector2.down*Time.deltaTime*gravity;


        if (Input.GetKeyDown(KeyCode.UpArrow))
            movement += Vector2.up * moveSpeed;
        entity.velocity = movement;
```

Welp, this can and will clip you straight through a sprite collider.  Well done.

---
## TODO

- [ ] Install instructions
  - [ ] VS Code
  - [ ] .NET SDK 
  - [ ] Unity Hub
- [ ] Investigate Unity + GitHub

