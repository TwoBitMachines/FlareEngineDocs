Pick And Throw
++++++++++++++
.. complete!
The player can pickup and throw a block.

Use the block in Demo2 as a template. To create one from scratch, add a AIFSM to an empty gameobject. 
Set the Tag to Block. Set Layer to Platform. Set AI type to MovingPlatform. Enable has Gravity. Enable Collide With World 
Only in the Collision settings. Create one empty state Called Wait. Another called Throw, and the Throw node. Set the throw velocity.
Enable OnSuccess and OnFailure to jump to the Slide State. Add the Slide state and the Slide node. Set the slide speed. 
Enable OnSuccess and OnFailure to jump to the Wait sate. This player ability will be in charge of using these states.
Make sure this has a BoxCollider2D and a sprite renderer.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Button 
     - If pressed, the player will pickup a block if it's touching it.
 
   * - Hold Position
     - This hold position of the block relative to the player once it's being held by the player.

   * - Throw Time
     - This is the extra time the player will remain in the throw state in which the throwingBlock signal 
       will go true in order to play a throwing animation. Set to zero if not needed.

**Signals: pickedBlock, throwingBlock*