Dash
+++++

Increase the speed of the player to quickly cover distance.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Dash Direction
     - Enabling Horizontal Axis initiates a dash along the x-axis using left and right buttons, 
       with the option of assigning only one button. With Multi Directional enabled, the player can dash
       in any of eight directions using assigned buttons.

   * - Button Taps 
     - If Single Tap is enabled, pressing the button once will initiate a dash. If Double Tap is enabled, pressing the button twice 
       within the specified time frame is required to initiate a dash.

   * - Buttons  
     - The buttons that need to be tapped in order to trigger a dash.

   * - Extra Button 
     - If pressed, this will immediately initiate a dash, bypassing the button tap settings.

   * - On Dashing
     - The Unity Event invoked when the player is dashing, and can be used to call a world effect. 
       You will need to specify the name of the effect and the frequency at which the event should execute.

   * - On Start
     - The Unity Event invoked when the player starts dashing. You can call a world effect from this event. 
  
   * - On End
     - The Unity Event invoked when the player ends dashing. You can call a world effect from this event.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Duration
     - With Instant enabled, the dash distance is covered in one frame; with Incremental enabled, 
       the dash distance is covered gradually according to the Dash Time.

   * - Dash Distance
     - The total distance traversed while dashing.

   * - Cool Down
     - The time interval before the next dash can be triggered.

   * - Crouch
     - If enabled, the player will change to a lower height while dashing. If the player 
       is below a platform when the dash completes, the crouch signal will be set.

   * - Air Dash Limit
     - This determines the number of times the player can dash while in mid-air.
       Consecutive air dashes are only allowed if the player performs an air jump in between.

   * - Can Take Damage
     - If disabled, the player will not take damage while dashing. This assumes the player has a Health component.

   * - On Ground Only
     - If enabled, the player must be on the ground in order to begin a dash.

   * - Nullify Gravity
     - If enabled, the force of gravity will not affect a dash.

**Signals: dashing, dashX, dashY, dashDiagonal, crouch**