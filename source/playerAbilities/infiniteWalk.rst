Infinite Walk
+++++++++++++

The player will automatically walk infinitely and change direction upon wall contact.

.. tip:: 
   Don't forget to add the Jump ability as an exception to this ability, if you want the player to jump!

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
     
   * - Button
     - Press this button to enter and exit the infinite walking state.

   * - Auto Wall climb
     - Enabling this allows the player to climb walls automatically when jumping onto
       them. Prioritize InfiniteWalk and add Wall ability as an exception to it.

   * - Change On Input
     - If enabled, the user can change the direction of the infinite walk with the x input.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Event
     - 
     
   * - InfiniteWalkActivate (bool value)
     - Call this method to active or stop infinite walking.