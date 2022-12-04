Ziplining
+++++++++

Enable this to allow the player to interact with Ziplines.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Zip Speed
     - The force applied to the x velocity of the player while ziplining. A value below 1 will feel like friction, and a value above 1 will be a speed boost.

   * - Jump Force
     - The exit jump force.

   * - Y Offset
     - The offset applied to the player's y position. This can be useful to align the animation.

   * - Exit Button
     - The player will exit the zipline if the exit button is pressed.

   * - Relatch
     - If enabled, the player will be able to land on the same zipline again after jumping.

   * - Apply Gravity
     - If enabled, the player will slide automatically towards the lowest point of the zipline if it's facing towards it.

   * - On Start
     - The Unity Event invoked when the player starts ziplining. You can call a world effect from this event. 
  
   * - On End
     - The Unity Event invoked when the player ends ziplining. You can call a world effect from this event.

**Signals: zipline**
