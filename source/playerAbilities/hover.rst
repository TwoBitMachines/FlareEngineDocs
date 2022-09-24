Hover
+++++

Escape gravity by letting the player hover in the air.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Thrust  
     - The forced used to propel the player upward. This force will be proportional to the jump force.

   * - Maintain
     - The tendency for the player to remain in the air. A value of one will prevent the player from descending downward, unless
       the descend button is pressed.

   * - Thrust Button
     - Press this button to create thrust.

   * - Descend
     - The force that will drive the player downward. The descend button is optional. If it's not used,
       the player will descend on its own, according to the maintain value.

   * - Descend Button
     - Press this button to create downward thrust.

   * - Exit
     - If On Ground Hit is enabled, the player will exit the hover state when the player touches the ground. If Button is enabled,
       the player will exit the hover state when the specified button is pressed.

   * - Air Friction X
     - The air resistance applied to the player while hovering in the x direction.

   * - On Thrust
     - The Unity Event invoked when the thrust button is pressed.

   * - On Descend
     - The Unity Event invoked when the descend button is pressed.

**Signals: hover**