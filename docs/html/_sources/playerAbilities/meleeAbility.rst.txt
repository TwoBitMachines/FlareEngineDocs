Melee
+++++

Register the melee attacks so they can be properly executed. Unlike firearms, only one melee attack 
can be active at at a time. The melee attack that will be executed will always be the first one in the list.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Method

   * - CompleteAttack
     - Call this when the attack animation is complete to stop the melee attack.

   * - ChangeMeleeAttack (string meleeName)
     - If more than one melee attack is registered, call this method to change to a different one by moving it to the top of the list.

   * - MeleeAttackIsActive
     - Returns true if the first melee attack is active.