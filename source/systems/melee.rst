Melee
+++++++
.. complete!
Create a melee attack for the player to use against enemies. Each melee attack consists of a collider that will be used 
to detect targets and an attack animation. It is possible to chain attacks based on user timing and hit success. 
It is also possible to add velocity to each attack.

However, the attack animation has to be setup and executed elsewhere. If using Sprite Engine, set the attack animation 
to loop once, and add a collider2D property to control the size and position of the collider on a per frame basis. 
The Melee system will be in charge of enabling the collider, and setting the animation signal active. Once the attack 
animation is complete, the **CompleteAttack** method must be called on the **Melee** class.

To create a melee, create a gameobject and set it as a child of the player transform. Add the collider that will 
be used to deal damage. Then add the Melee component. The player must have the Melee ability enabled. Once enabled, register 
the newly created melee attack. Since more than one melee attack can be registered, it is thus possible to change between melee attacks.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Melee
     - 

   * - Melee Name
     - Name the melee for identification purposes.
 
   * - Hit Layer
     - The layer the collider2D will check for collisions.

   * - Melee Collider
     - The reference to the collider2D.

   * - Button
     - The input button that will start a melee attack.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Properties
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

   * - Sprite Name
     - The animation signal the system will set true when performing a combo.

   * - Damage
     - The amount of damage dealt to the target hit. 
   
   * - Velocity x
     - The velocity applied to the combo in the x-direction.

   * - Velocity y
     - The velocity applied to the combo in the y-direction. If Jump Velocity is enabled,the velocity will be treated as a jump force.

   * - On Combo Begin
     - The event invoked when the Combo begins.

**Signals:  meleeCombo**