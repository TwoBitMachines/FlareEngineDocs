Melee
+++++++

Use a melee to attack enemies. You'll need a collider to deal damage and
an attack animation. You'll be able to chain attacks and add velocity to
each attack based on timing and hit success. 

However, the attack animation needs to be set up and executed elsewhere.
If you're using Sprite Engine, set the attack animation to loop once, and 
add a collider2D property to control the size and position of the collider on 
a per-frame basis. Once the animation is complete, use the OnLoopOnce 
event to call the **CompleteAttack** method on the **Melee** class.

To create a melee attack, add a collider to a gameobject and set it as a child of 
the player transform. Then, add the Melee component and make sure the player has 
the Melee ability enabled. The Melee system is in charge of enabling the collider
and setting the animation signal active.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Melee
     - 

   * - Melee Name
     - Name the melee for identification purposes.

   * - Melee Collider
     - The reference to the collider2D.

   * - Hit Layer
     - The layer the collider2D will check for collisions to deal damage to.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Input
     - 

   * - Buttons
     - The button combination that will trigger the melee attack. If only one button is desired, then make sure the second button is empty.

   * - Attack From Sleep
     - If enabled, the system will check if the button inputs are triggered even if the melee is deactivated. If so, the system will activate the melee attack.

   * - Cancel Others
     - If enabled, this melee attack will be able to cancel any active melee attack. This will only occur if Attack From Sleep is enabled.

To enable blocking, add a RigidBody2D component to the melee gameobject and set the 
Body Type to kinematic. Change the layer to World or Player. If set to World,
the melee block will be able to block walking enemies. Set up the block animation
in a similar fashion to the attack animation, but you don't need to set it to loop. 
Configure the collider as necessary. At runtime, the component will add the 
Health component to sense enemy attacks.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Blocking
     - 

   * - Block signal
     - The animation signal that will be set True during blocking.

   * - Block Button
     - The input that must be held in order to block.

   * - Must Hold
     - You can choose two buttons that must be active in order to block. In the demo, button down is used.

   * - Cancel Combo
     - If enabled, the block input can stop an active melee combo from progressing in order to block.

   * - Stop Vel X
     - If enabled, the player will not be able to move in the x direction while blocking.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Combos
     - Some fields are only enabled if Combos has more than one attack.
     
   * - Early timer
     - How soon after the attack started can the user press the button in order to successfully begin the next attack in the combo.   
   
   * - Delay timer
     - How much time after the attack finished can the user still press the button in order to successfully begin the next attack in the combo.

   * - Cool Down
     - The wait period before the next combo can begin.

   * - Hit To Continue
     - If enabled, in order to move on to the next attack in the combo, the current attack must have made contact with a target.

   * - On Cool Down
     - This event will be invoked with a percentage of the cool down time.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Combos
     - 

   * - Signal Name
     - The animation signal the system will set true when performing a combo.

   * - Damage
     - The amount of damage dealt to the target hit. 
  
   * - Direction
     - The direction in which the damage will be applied.

   * - Velocity x
     - The velocity applied to the combo in the x-direction. Additive Velocity will be added to player movement. Absolute Velocity will override player movement. Event Velocity 
       works like Absolute Velocity, but the BeginVelX (bool value) method must be called on the Melee component to active Event Velocity. 
       This is usually called from the animation controller in a specific frame of the animation.

   * - Velocity y
     - The velocity applied to the combo in the y-direction. This almost has the same options as Velocity x. If Jump Velocity is enabled, the velocity will be treated as a jump force.

   * - Attack
     - If Anytime is set, the combo sequence will proceed. If MustBeOnGround is set, the player must be on the ground for the combo to proceed. If not, the player has the option to exit 
       the combo or skip to the next combo in the sequence. The same rules apply if MustBeOnAir is set.

   * - Go To Next
     - This works like Early Timer. However, if the user presses the button after the specified time has expired, the system will immediately jump
       to the next combo before the current one finishes.

   * - Recoil
     - After an attack, apply a recoil force to the player in the specified direction.

   * - Is Locked
     - If enabled, this attack will be disabled until the UnlockAll or Unlock methods are called.

   * - On Combo Begin
     - The Unity Event invoked when the Combo begins.
     
.. list-table::
   :widths: 50 200
   :header-rows: 1

   * - Method
     - 

   * - Pause(bool value)
     - Pausing will prevent the player from using this melee attack.
 
   * - CompleteAttack()
     - Call this method once the attack animation is complete.

   * - UnlockAll()
     - This will unlock all melee attacks that are currently locked.
 
   * - Unlock(int index)
     - This will unlock the melee attack at the specified index.

**Signals:  meleeCombo, meleeLeft, meleeRight**