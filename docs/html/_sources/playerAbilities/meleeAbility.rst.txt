Melee
+++++

All melee attacks that are children of the player object will be registered automatically on scene start. 
Unlike firearms, only one melee attack can be active at at a time. 

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Cool Down 
     - The wait period before the next melee attack can begin. Note, this is the cool down between different melee attacks. Combo 
       attacks within a melee attack have a separate cool down option.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Method

   * - CompleteAttack()
     - Call this when the attack animation is complete to stop the melee attack.

   * - ChangeMeleeAttack (string meleeName)
     - If more than one melee attack is registered, call this method to change to a different one by moving it to the top of the list.

   * - MeleeAttackIsActive()
     - Returns true if the first melee attack is active.