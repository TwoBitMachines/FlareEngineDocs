Ceiling
+++++++
.. complete!
The player will latch onto a ceiling and move in the x direction. This is not meant to work on sloped ceilings.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Friction
     - The friction applied to the player's x direction while moving and holding a ceiling.

   * - Auto Grip
     - If enabled, the player will automatically latch onto a ceiling upon contact. To dismount, the jump 
       button must be pressed. If not enabled, the user has to hold the jump button to ceiling climb.

   * - Edge Jump
     - If enabled and if the ceiling is an EdgeCollider2D, the player will jump up through the platform. Scale the 
       jump force if necessary.

.. tip::
   If the ceiling is an EdgeCollider2D, auto grip will need to be enabled for proper function.