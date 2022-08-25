Push Block
++++++++++
.. complete!
The player can push and pull a block.

Use the push block in Demo2 as a template. To create one from scratch, add a AIFSM to an empty gameobject. 
Set AI type to Regular. Set Collide With World Only to True in the Collision settings. Create one empty state. 
Set the Tag to PushBlock. Set the Layer to Platform. And finally, add a Sprite Renderer.

You can also enable Climb Slopes on the AI to push the block up and down slopes. Rotate To Slope is not
a supported function for push block, however.

The previous push block from version 1.1.0 is greyed out and still in Demo2 for reference. This previous push 
block iteration was constructed purely with AI and does not require this ability to work. Feel free 
to use it if need be. The major advantage of this Push Block ability is that it works with the 
ability priority system and can pull the block.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Button 
     - If set to Automatic, the player will immediately push the block upon contact, but it will not be able to pull it.
       If set to Button, specify the push and pull button.
 
   * - Push Speed
     - This will scale the player's velocity when pushing the block. Ideally, this value should be less than 1.

   * - Pull Speed
     - This will scale the player's velocity when pulling the block. Ideally, this value should be less than 1.

**Signals: pushBlock, pullBlock*