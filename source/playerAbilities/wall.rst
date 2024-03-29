Wall
+++++

The player can slide, climb, corner hang, corner grab, and jump on walls. If a particular wall is not meant to be climbable, add a Unity tag "NoClimb"
to this gameobject.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
 
   * - Type
     - The type of wall interaction.

   * - Start On Ground
     - If enabled, the player will be able to start climbing a wall even if it's still touching the ground.

   * - On Enter
     - The Unity Event invoked when the player latches unto a wall.
 
   * - On Exit
     - The Unity Event invoked when the player gets off a wall.
     
Slide
=====

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Slide When    
     - If Pressing Input is enabled, the player will slide on a wall only if it's pushing against it.
       If Automatic is enabled, the player will latch onto the wall and slide automatically.
 
   * - Slide Speed 
     - How quickly the player slides down. This can be applied as a velocity or an acceleration.

   * - Slide Timer
     - If enabled, limit how long the player can slide before falling.
  
   * - Climb Up
     - If Slide is automatic, this option will appear. The player has the option to climb up the wall if moving up.

   * - Jump Up
     - The force that pushes the player up the wall. The X force will push the player away and then towards the wall.

   * - Jump Away
     - The force that pushes the player away from the wall.

   * - Jump Limit
     - Limits the amount of wall jumps before the player falls down.

   * - Block Jump Climb
     - This will prevent the player from jumping up the wall.

   * - On Slide
     - The Unity Event invoked when the player is sliding down a wall. This event will pass the player's position. Typically any gameobjects
       enabled for particle effects should have a way to disable themselves. You can use the class Basic Timer for this.

**Signals: wall,  wallLeft, wallRight, wallSlide, wallClimb, wallSlideJump, autoCornerJump**

Climb
=====

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Buttons   
     - If Button is enabled, specify the up and down climb buttons. If Player Direction is enabled, the player will climb the wall
       in the direction of its horizontal movement. If None is enabled, the player will only be able to hold the wall.
 
   * - Hold Wall 
     - If Automatic is enabled, the player will hold the wall automatically. If Hold Button is enabled, specify the button that must be
       pressed in order to hold the wall.

   * - Speed
     - How quickly the player climbs the up and down the wall.
  
   * - Climb Limit
     - If enabled, limit how long the player can climb the wall before falling. If Fall amount is greater than zero, the player will hold the wall
       for this time period before finally falling. During the Fall period, the player will not be able to climb the wall.

   * - Slide Down
     - If enabled, the player will slide down the wall instead of climbing down.

   * - Climb Up Only
     - If enabled, the player will only be able to climb up the wall.

   * - Jump Up
     - The force that pushes the player up the wall.

   * - Jump Away
     - The force that pushes the player away from the wall.

   * - Jump Limit
     - Limits the amount of wall jumps before the player falls down.

   * - Jump On X Input
     - If climbing a wall, the user can jump automatically by pressing the left or right movement inputs.

   * - On Climb
     - The Unity Event invoked when the player is climbing a wall. You can call a world effect from this event. The name of the effect 
       and the rate at which the event executes are required.

**Signals:  wall, wallLeft, wallRight, wallHold, wallClimb, wallSlide**

.. note:: 
   Once the player is near the top of a wall, it will automatically jump on top of the platform. If Corner Grab is enabled, this setting will be ignored.

Corner Hang
===========
.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Offset  
     - Determines the point at which the Corner Hang becomes active. A value of 0.5f will check for a corner 0.5f units below the player's head.
 
   * - Exit Hang 
     - When to exit a Corner Hang. If Button is enabled, the up and down buttons will unlatch the player from the corner. If Player Direction is enabled,
       the player's movement will unlatch it from the corner. If None is enabled, only a jump action can unlatch a Corner Hang.

**Signals: wall, wallLeft, wallRight, wallHang**

Corner Grab
===========
.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Type
     - How will the player grab the corner? If Jump is enabled, the player will simply hold the corner until the jump button is pressed.
       If Pull Up or Pull Up Auto is enabled, a corner climb animation will play. If Pull Up Auto is enabled, the player 
       will start the corner climb animation immediately. Press the blue button to add each sprite in the animation.
 
   * - Exit Grab
     - Once the Corner Grab state has been entered, the player can exit this state either by the specified button press or by player movement. 

   * - Final Position
     - When the corner climb animation is over, this will set the player's position on top of the platform. Sometimes its convenient to do this 
       on the second to the last sprite or at the very last sprite. This will depend on how the sprites in the animation are set up.

   * - Grab Offset
     - This will offset the player's position while initially grabbing the corner

   * - Animation Time
     - The total duration of the corner climb animation. 

   * - Sprite
     - A sprite in the corner climb animation.

   * - Offset
     - The offset will displace the player's position for the current sprite that is playing. 
       This might take a little trial and error to get correct.

   * - On Animation Start
     - The Unity Event invoked when the animation starts.

   * - On Animation End
     - The Unity Event invoked when the animation ends.

**Signals: wall, wallLeft, wallRight, wallHold,  wallCornerGrab**

.. important:: 
   If Corner Grab is playing an animation, it will use the Sprite Renderer attached to the player. If Sprite Engine is being used, it will be paused, allowing
   the animation to play freely. If using another system for playing sprites, the signal wallCornerGrab will be set True, which will let you know when to pause
   this other system.