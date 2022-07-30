Swim
+++++
.. complete!
Allow the player to swim or float on any body of water. The body of water will determine 
if the player either floats or swims. If floating, the player will remain above the water line. If swimming, the player 
will swim inside the body of water.

.. note::
 The player must have the Swim ability enabled to interact with water.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Spring     
     - If floating, when the player enters the water, it will oscillate on the water line before coming to a rest.
       This force dictates how quickly the oscillations occur.
 
   * - Damping   
     - How quickly the spring force dissipates.

   * - Weight
     - How quickly the player sinks while swimming.
  
   * - Water Impact
     - The force exerted on the water upon entry. The force exerted while the player moves in the water will be proportional to this value and the player's velocity.

   * - Water Friction X
     - Water resistance applied to the player in the x direction.

   * - Water Friction Y
     - Water resistance applied to the player in the y direction.

   * - Jump
     - The force used to jump out of the water.

   * - Switch Button
     - If water Switch Type is set to Yes, holding this button will transition the player from a floating state to a swimming state. To return to a floating state, the player 
       must reach the top of the water.

   * - On Enter Water
     - On water entry, a Unity Event containing the entry position is invoked. This could be useful for adding particle effects.

   * - On Exit Water
     - On water exit, a Unity Event containing the exit position is invoked.

.. note::
 A prefab called Bubbles emits bubble particles as the player swims. Make it a child of the Player. Feel free to change 
 the particle settings, too!

**Signals: inWater, swimming, floating**
