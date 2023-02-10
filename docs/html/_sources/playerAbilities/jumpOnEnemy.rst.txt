Jump On Enemy
+++++++++++++

Jump on an enemy to deal damage.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Layer
     - The layer where damage is dealt, usually the Enemy.
 
   * - Damage 
     - The amount of damage dealt.

   * - Damage Force
     - The forced applied in the direction of damage.

   * - Bounce Force
     - The jump force applied to the player after contact. If the jump button is being held, the jump force will be multiplied by the boost.

   * - On Bounce
     - The Unity Event invoked when the player jumps on an enemy. Call a World Effect with the dynamic Activate method.
 