Rope
++++

The player can interact with ropes in the game. In recent updates, it is now 
possible to climb a rope. As a result, there are a few signals you
should be aware of when interacting with ropes.

- **rope**: true when the player is on the rope.
- **ropeSwinging**: true when the player's x input is not zero.
- **ropeHanging**: true when the player is at the end of the rope.
- **ropeHolding**: true when the player is not at the end of the rope.
- **ropeClimbing**: true when the player is actively climbing the rope.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Swing Strength    
     - The force added to the swing motion.
 
   * - Jump   
     - If latched, the force used to jump away from the rope.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Events
     - 

   * - On Enter
     - The Unity Event invoked when the player latches unto the rope.
 
   * - On Exit
     - The Unity Event invoked when the player jumps off the rope.

**Signals: rope, ropeClimbing, ropeHanging, ropeHolding, ropeSwinging**