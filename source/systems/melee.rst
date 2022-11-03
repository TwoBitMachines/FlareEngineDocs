Melee
+++++++

Create a melee attack for the player to use against enemies. Each melee attack consists of a collider that will be used 
to detect targets and an attack animation. It is possible to chain attacks based on user timing and hit success. 
It is also possible to add velocity to each attack.

However, the attack animation has to be setup and executed elsewhere. If using Sprite Engine, set the attack animation 
to loop once, and add a collider2D property to control the size and position of the collider on a per frame basis. 
The Melee system will be in charge of enabling the collider, and setting the animation signal active. Once the attack 
animation is complete, the **CompleteAttack** method must be called on the **Melee** class.

To create a melee, create a gameobject and set it as a child of the player transform. Add the collider that will 
be used to deal damage. Then add the Melee component. The player must also have the Melee ability enabled. Once enabled, register 
the newly created melee attack. Since more than one melee attack can be registered, it is thus possible to change between melee attacks.

The melee component also has the ability to execute a block to defend against enemy attacks. If blocking is enabled, 
add a RigidBody2D to this gameobject and set Body Type to kinematic. You will also need to change the 
layer to  World or Player. If set to World, this melee block will have the ability to block walking enemies. 
The block animation should be set up in similar fashion to an attack animation. Configure the collider, but setting 
the animation to loop will not be necessary. During runtime, this component will add the Health component to be able 
to sense enemy attacks.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Melee
     - 

   * - Melee Name
     - Name the melee for identification purposes.

   * - Melee Collider
     - The reference to the collider2D.

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
     - 
 
   * - Hit Layer
     - The layer the collider2D will check for collisions.

   * - Attack Button
     - The input button that will start a melee attack.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Combos
     - Some fields are only enabled if Combos has more than one attack.

   * - Hit To Continue
     - If enabled, in order to move on to the next attack in the combo, the current attack must have made contact with a target.

   * - Early timer
     - How soon after the attack started can the user press the button in order to successfully begin the next attack in the combo.   
   
   * - Delay timer
     - How much time after the attack finished can the user still press the button in order to successfully begin the next attack in the combo.

   * - Cool Down
     - The wait period before the next combo can begin.

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
  
   * - Force
     - The forced applied in the direction of damage.

   * - Velocity x
     - The velocity applied to the combo in the x-direction. Additive Velocity will be added to player movement. Absolute Velocity will override player movement. Event Velocity 
       works like Absolute Velocity, but the BeginVelX (bool value) method must be called on the Melee component to active Event Velocity. 
       This is usually called from the animation controller in a specific frame of the animation.

   * - Velocity y
     - The velocity applied to the combo in the y-direction. This has the same options as Velocity x and an extra one. If Jump Velocity is enabled, the velocity will be treated as a jump force.

   * - Attack
     - If Anytime is set, the combo sequence will proceed. If MustBeOnGround is set, the player must be on the ground to proceed, or else the combo will exit the combo or skip
       to the next combo in the sequence. The same rules apply if MustBeOnAir is set.

   * - Go To Next
     - This works like Early Timer. However, if the user presses the button after the specified time has expired, the system will immediately jump
       to the next combo before the current one finishes.

   * - On Combo Begin
     - The event invoked when the Combo begins.

**Signals:  meleeCombo**