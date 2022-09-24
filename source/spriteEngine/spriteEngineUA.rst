Sprite Engine UA
++++++++++++++++

**SpriteEngineUA** allows you to use the functionality of Sprite Engine with Unity Animations.
Since the animations are no longer being created and configured by Sprite Engine, it's assumed the frame rate, events, and looping 
are all handled by the animation. 

SpriteEngineUA only requires a reference to the gameobject containing the animator and the names of the animations. 
You will need to click the add button to start appending animation names. 

The animator component should not exist on the same gameobject as the Player or AI components. 
The animator and all its contents must exist as child objects of the character. This is important since the localScale will 
be flipped to change the direction of the animation. Also, any weapons attached to the character should not be 
children of the animation objects.

The animator will still need to reference all the animations. However, you no longer have to create a state machine for them since SpriteEngineUA 
will be in charge of the signals and state. After everything is set up, you can proceed to use Signals and the Animation State 
just like you would with Sprite Engine.

.. important::
 All your animations must be created facing to the right to work correctly with the animation flip.
