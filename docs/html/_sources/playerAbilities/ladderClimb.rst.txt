Ladder
++++++
.. complete!
The player can climb ladders.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Latch    
     - If Automatic is enabled, the player will automatically latch to the ladder on contact, provided the player has a negative y velocity and a zero x velocity. 
       If Enter Button is enabled, specify the button that must be pressed in order for the player to latch onto the ladder.
 
   * - Climb  
     - If Manual is enabled, specify the buttons (Up, Down) for climbing the ladder. If Automatic is enabled, the player will climb
       the ladder automatically.

   * - Climb Speed
     - How quickly the player climbs the ladder.
  
   * - Stand On Top
     - If enabled, the player can stand on top of the ladder.

   * - Align To Center
     - If enabled, the player's x position will align with the center of the ladder.

**Signals: ladderClimb**