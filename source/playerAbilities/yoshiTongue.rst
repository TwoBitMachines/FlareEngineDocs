Yoshi's Tongue
++++++++++++++

This will allow Yoshi to extend and retract its tongue to eat enemies. And if Yoshi is equipped with any weapons, 
it will be able to shoot projectiles after eating an enemy. 

Enemies that can be eaten by Yoshi must contain the CapturedByYoshi AI node. When captured, the system will change 
the AI to the Captured state, allowing the enemy to change animation signal in this state (please note, enemy sprites 
must be set to the bottom pivot point). And once completely eaten, the system will change the AI state to Killed. If you want 
to make use of these states, make sure they exist.

Yoshi's tongue will require two child transforms. The tongue and the tongue tip. The tongue should be thought of as the 
fire point and the tongue tip as the end point of the tongue. Both are required, and they can contain sprites. The tongue 
will be stretched to the specified length, stretching its sprite.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Target Layer
     - The layer the enemies belong to.

   * - Button
     - The button that must be pressed to extend Yoshi's tongue.

   * - Animation Timer
     - The duration of each animation along the sequence. Yoshi will bend down, sit up right, and then shoot. Each animation 
       should take roughly the same amount of time. The exact time is not required.

   * - Stop Vel X
     - If enabled, it will prevent Yoshi from moving while it's extending or retracting its tongue.

   * - Tongue Tip
     - The transform reference to the tongue tip.

   * - Tongue
     - The transform reference to the tongue.

   * - Tongue  Speed
     - The speed at which the tongue extends and retracts.

   * - Tongue  Length
     - The length of the tongue.

   * - Closing Length
     - If an enemy is captured, the tongue length at which the enemy is officially disabled or killed. This moment should occur before 
       the enemy overlaps with Yoshi.

   * - Target Offset
     - If an enemy is captured, the offset position of the enemy relative to the tongue tip.

   * - Deactivate Target
     - If enabled, the capture enemy's gameobject will be deactivated during closing length.

   * - Weapon
     - A list of Firearms Yoshi can use to shoot projectiles after eating an enemy. The CapturedByYoshi node will contain a weapon index. 
       This index will dictate which Firearm Yoshi uses.

   * - Events
     - The Unity Events invoked during the sequence. On Fail is only called if the enemy Yoshi touched does not contain a CapturedByYoshi node.

These signals will be set internally, but they will need to be created in SpriteEngine.

**Signals: yoshiExtend, yoshiRetract, yoshiFull, yoshiShoot**