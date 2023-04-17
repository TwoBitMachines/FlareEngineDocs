Jump
+++++

The most fundamental ability of any platformer. 

.. note::
   Jump height and jump time are set in the Collision settings in order to
   calculate the force of gravity. However, this ability must still be enabled
   if the player is required to jump.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Button Trigger   
     - Choose the button trigger for jumping.
 
   * - Jump Height  
     - The maximum and minimum jump heights. For min height, if this value is greater than zero, the player will 
       have a variable jump height, and min jump will be the lowest jump height possible.

   * - Jump Time 
     - The total time required to jump.

   * - Jump Buffers
     - Jump Buffer: the time window the jump button can be pressed before the player hits the ground to execute a jump. 
       Coyote Time: the time window the jump button can still be pressed after the player walks off a platform to execute a jump.

   * - Momentum
     - This will maintain momentum in the direction the player is jumping, even if the user is not pressing input. This value must be greater than 
       zero to be active, and any value above zero will scale the x velocity.

   * - Air Jumps
     - The number of extra jumps the player can perform in the air. The second field will scale the jump force.

   * - Air Glide
     - If holding the glide button, the player will gently glide down instead of falling when jumping. Air Glide can only occur after all the air jumps (if any) 
       have occurred. The glide value must be between 0 and 1f.

   * - Glide Boost
     - The jump boost added to the air glide.

   * - Glide From Fall
     - If the player walks off a platform (without jumping), the player can still execute Air Glide or Air Jumps if enabled.

   * - Glide Immediately
     - If enabled, the player will bypass the air jump check and glide once the glide button is pressed. 

.. list-table::
   :widths: 75 200
   :header-rows: 1

   * - Event
     - 

   * - Jump
     - The Unity Event invoked when the player jumps. Call a World Effect with the dynamic Activate method.
 
   * - Air Jump
     - The Unity Event invoked when the player air jumps. Call a World Effect with the dynamic Activate method.

.. list-table::
   :widths: 75 200
   :header-rows: 1

   * - Method
     - 

   * - Set Air Jumps
     - Set the number of air jumps.
 
   * - Set Air Glide
     - Set the value for air glide.

.. important::
   If an ability already contains a jump force, do not add the Jump ability as an exception to it. For instance, the Wall ability
   contains a few jumping options that it will execute internally. The Jump ability is only geared for jumping on ground.
  
**Signals: airGlide, airJump,  airJump1,  airJump2, airJump3**