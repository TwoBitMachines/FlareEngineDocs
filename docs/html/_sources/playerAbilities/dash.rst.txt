Dash
+++++

Increase the speed of the player to quickly cover distance.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Buttons  
     - The buttons that need to be tapped in order to trigger a dash.

   * - Extra Button 
     - If pressed, this will immediately initiate a dash, bypassing the button tap settings.

   * - Dash Direction
     - If Horizontal Axis is enabled, the dash will occur along the x axis. In this state, only the left and right buttons are used. It is also possible
       to use only one button and leave the other empty. If Multi Directional is enabled, all the buttons that are set will be utilized to move the player in one of
       eight directions along the x and y axis.

   * - Button Taps 
     - If Single Tap is enabled, pressing the button only once will trigger a dash. If Double Tap is enabled, pressing the button twice is required 
       to trigger a dash.

   * - Tap Threshold
     - If Double Tap is enabled, the threshold is the time interval in which the double tap must occur for the dash to trigger successfully.

   * - On Dash
     - The Unity Event invoked when the player is dashing. You can call a world effect from this event. The name of the effect 
       and the rate at which the event executes are required.

   * - On Start
     - The Unity Event invoked when the player starts dashing. You can call a world effect from this event. 
  
   * - On End
     - The Unity Event invoked when the player ends dashing. You can call a world effect from this event.

   * - Duration
     - If Instant is enabled, the player will traverse the dash distance in one frame. If Incremental is enabled, the player will traverse the dash distance
       according to the dash time. 

   * - Dash Time
     - The time it will take to traverse the dash distance;

   * - Dash Distance
     - The total distance traversed while dashing.

   * - Cool Down
     - The time interval before the next dash can be triggered.

   * - Crouch
     - If enabled, the player will change to a lower height while dashing. If the player is below a platform when the dash completes, the crouch signal will be set.

   * - Can Take Damage
     - If disabled, the player will not take damage while dashing. This assumes the player has a Health component.

   * - On Ground Only
     - If enabled, the player must be on the ground in order to begin a dash.

   * - Nullify Gravity
     - If enabled, the force of gravity will not affect a dash.

  
**Signals: dashing, dashX, dashY, dashDiagonal, crouch**