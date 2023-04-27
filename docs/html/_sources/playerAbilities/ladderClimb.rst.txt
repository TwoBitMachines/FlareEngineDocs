Ladder
++++++

The player can climb ladders.
       

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
 
   * - Climb  
     - For Manual mode, use Up and Down buttons to climb ladder; for Automatic mode, ladder climbing is automatic.

   * - Up, Down
     - Climbing buttons.

   * - Climb Speed
     - How quickly the player climbs the ladder.
 
   * - Auto Latch
     - Player latches to ladder at zero velocity.

   * - Jump
     - Jump force from ladder.

   * - Jump Fall Point
     - If non-zero, it determines the distance from the jump point where the
       player can land back on the ladder. This feature allows the player to jump within 
       the ladder and still fall down if necessary.

   * - Fence Flip
     - If the ladder has fence flip enabled, the button the player must press to enter a fence flip.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Events
     - 

   * - On Enter
     - The Unity Event invoked when the player latches unto the ladder.
 
   * - On Exit
     - The Unity Event invoked when the player gets off the ladder.

**Signals: ladderClimb**