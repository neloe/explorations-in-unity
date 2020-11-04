# explorations-in-unity

## A set of notes during my messing with Unity while prepping for Game Dev

---

### Editors

* VS Community seems to suck; VS Code better/lighter?  Maybve not; need the .NET core 3.1 SDK and suggested extensions; let's see if that's nicer


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
  
  
### Code Snippets

Gravity and jumping; why not
```cs
entity.velocity += Vector2.down*Time.deltaTime*gravity;
Debug.Log(Vector2.down*Time.deltaTime*gravity);

if (Input.GetKeyDown(KeyCode.UpArrow))
    entity.velocity += Vector2.up * moveSpeed;
```

Welp, this can and will clip you straight through a sprite collider.  Well done.
