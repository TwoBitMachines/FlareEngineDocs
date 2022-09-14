Firearm
+++++++
.. complete!
The Firearm shoots projectiles. The purpose of this component is to control the behavior of the weapon as 
it relates to the character. It is not concerned about how projectiles operate. You will
specify its fire point, the projectile it uses, shooting direction, how it rotates, recoil,
and other features. It's possible to create many variations of a firearm with these properties.

To set up, create an empty gameobject and add the Firearm component. Add a Sprite to this gameobject if the weapon 
should be visible (and set Sprite Pivot to Left). Make this gameobject a child of the character that will be using the firearm.
The player must have the Firearms ability enabled (for recoil to work and for applying ability exceptions).

.. note::
   More than one firearm can be active at a time, and the Item class offers a convenient way for picking up tools.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Name
     - Give the firearm a unique name for identification purposes.
 
   * - Fire Point 
     - The spawn point for projectiles. Create a transform for the fire point and make it a child 
       of the firearm. Set the reference here. The fire point is typically 
       placed at the end of the muzzle.

   * - Button
     - This the shoot button. Choose the button and its trigger event.
  
   * - Local Position
     - The local position of the firearm.

   * - Off Near Wall
     - If the character is next to a wall and the weapon is inside the wall, setting this true
       will prevent the weapon from shooting. This will ensure the weapon cannot shoot into another
       room.

   * - On Activated
     - The Unity Event invoked when the firearm's gameobject is set active true.

.. list-table::
   :widths: 50 200
   :header-rows: 1

   * - Method
     - 

   * - Shoot()
     - If necessary, trigger a shooting event with this method.
 
   * - AnimationComplete()
     - Call this method when the shooting animation completes. This will not trigger a shooting event, but it will 
       terminated the animation state of the firearm. It is assumed that ShootAndWaitForAnimation() was called 
       before. If using Sprite Engine, call this in the Loop Once Event.

   * - ShootAndAnimationComplete()
     - Call this method when the sprite is complete. This will trigger a shooting event and terminate 
       the animation state of the firearm. If using Sprite Engine, call this in the Loop Once Event.

   * - ShootAndWaitForAnimation()
     - Call this method at the exact sprite frame where shooting is required. This will not end the animation state
       of the firearm. Therefore, the last frame in the shooting animation should call AnimationComplete(); 

   * - ChangeDefaultProjectile (ProjectileBase newProjectile)
     - Change the projectile type.

   * - ChangeChargeProjectile (ProjectileBase newProjectile)
     - Change the charge projectile type.

.. note::
   The animation methods are only necessary if Shoot Animation is enabled. If Shoot Animation is enabled, the firearm 
   will enter an animation wait state upon shooting, where the system will wait for the animation to complete.

------------

Projectile
==========

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Default Projectile
     - The projectile the firearm will be using. 
 
   * - Inventory (Optional)
     - The reference to Projectile Inventory. This contains a list of projectiles, which makes it simple for the
       system to swap projectiles on the firearm.

   * - Auto Discharge 
     - After the character is finished shooting, specify a small duration in which the firearm keeps shooting.
       If the value is zero, this feature will be disabled.

   * - Shoot Animation
     - If enabled, it's the animation the character plays before shooting. The system will set the specified
       animation signal true. If using Sprite Engine, make sure the signal name exists, configure the Sprite State accordingly, and set to Loop Once. 
       If this is enabled, **a return signal is required or the system will stay stuck.** Typically you will call ShootAndAnimationComplete (),
       or ShootAndWaitForAnimation () followed by AnimationComplete ();

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Recoil will provide pushback upon shooting a firearm.

   * - Type
     - If Slide Back is enabled, the player will slide back. If Shake is enabled, the player will slide back and then slide forward. Shake is meant
       for short time durations.
 
   * - Recoil When
     - If Velocity Zero is enabled, recoil will only work if the player is standing still.

   * - Distance
     - The distance the player recoils.

   * - Time
     - The time required to recoil.

   * - Has Gravity
     - If the player is influenced by gravity, enable this so the recoil system takes the gravity effect into consideration.

**Signals: recoil, recoilLeft, recoilRight, recoilDown, recoilUp, recoilSlide, recoilShake**

.. important::
   The player must have the Firearms ability enabled for recoil to work.

.. note::
   Since recoil will apply a velocity to the character, the direction of the sprite will flip. If using Sprite Engine,
   to keep the sprite in the correct state, enable recoil, recoilLeft, and recoilRight signals, and configure the state
   of the sprite direction. Typically, if recoilLeft is true, set flipLeft, and if recoilRight is true, set flipRight. 

------------

Rotation
==========

Rotate the firearm.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Rotate With
     - How to rotate the firearm: Mouse, EightDirection, Auto Seek, Fixed Angle, Fixed Direction, No Rotation.
 
   * - Point Towards
     - The direction the firearm will point towards. If Character Direction is enabled, the firearm will point in the
       direction of the character movement. If Mouse Direction is enabled, the firearm will point in the direction of the mouse.
       If Transform Direction is enabled, the firearm will point in the direction of the specified Transform. This can be useful
       in case the firearm belongs to an npc; the specified transform can be set to point towards the player. 

**Signals: mouseDirectionLeft, mouseDirectionRight**

.. note::
   If using Sprite Engine, enable the mouse signals and use them to keep the player facing the direction of the mouse, even if the player
   is running in the opposite direction. Typically, if mouseDirectionLeft is true, set flipLeft, and if mouseDirectionRight is true, set flipRight. 
   The character's running sprite might need extra consideration, as it will probably need to play in reverse to achieve a running backwards look.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Rotate With Mouse

   * - Top Limit
     - The range of motion of the firearm from 0 to 180 degrees. This will only be enabled if Point Towards is set to Character Direction.
 
   * - Bottom Limit
     - The range of motion of the firearm from 0 to -180 degrees.

   * - Angle Offset
     - If desired, the offset that is applied to the firearm.

.. note::
   If Top Limit and Bottom Limit both have zero values, the range of motion of the firearm will be 360 degrees.
   Otherwise, the firearm is considered clamped, and it will be restricted by the specified limits.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Rotate With Keyboard

   * - Buttons Left, Right, Up, Down
     - Specify the keyboard buttons for changing the direction of the firearm.

   * - Diagonal
     - If enabled, the firearm will be able to point in 45 degree angles.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Rotate With Auto Seek (Rotate Towards Targets Automatically)

   * - Target Layer
     - The layer where targets should be searched for.

   * - Search Radius
     - Only targets within this radius from the center of the firearm will be detected.

   * - Search Rate
     - How often the firearm should search for targets.

   * - Auto Shoot
     - If enabled, the firearm will automatically shoot at a target.

   * - On Found New Target
     - The Unity Event invoked each time the firearm finds a new target.

------------

Aim
===

Add visual elements, such as a beam or reticle, to help the player aim.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Beam

   * - Line Of Sight Beam
     - A beam will extend from the firearm. Create a gameobject and place a
       sprite that represents the beam. Set the Sprite Pivot to Left. This gameobject should be a child of the firearm,
       and it should be enabled.
 
   * - Layer
     - The layers the beam can interact with. Typically these are walls and enemy targets. 

   * - Beam
     - Place a reference of the beam gameobject here. 

   * - Beam End
     - This is optional. If the beam hits the target layer, this gameobject will be enabled
       at the end of the beam. It can play a sprite for special effect purposes. Create this gameobject 
       and make it a child of the firearm. This gameobject should not be enabled. 
       The system will control its active state. 

   * - Max Length
     - The max length of the beam. If no target layer is hit, the beam will extend to this length.

   * - Target
     - The layer that should contain only enemies. If the beam hits an enemy target, the On Target Hit event
       will be invoked.

   * - Auto Shoot
     - If enabled and an enemy target is hit  using the Target layer, the firearm will shoot automatically.
 
   * - On Target Hit
     - The Unity Event invoked when an enemy is hit using the Target layer.

   * - On Beam Hit
     - The Unity Event invoked when the beam hits anything.

   * - On Nothing Hit
     - The Unity Event invoked when the beam hits nothing.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Reticle

   * - Line Of Sight Reticle
     - A reticle will be displayed at a specific distance from the firearm. 
       Create a gameobject and place a sprite that will act as the reticle. 
       Make this gameobject a child of the firearm.
 
   * - Aim Reticle
     - Place a reference of the reticle gameobject here.  

   * - Follow Type
     - If Fixed Position is enabled, the reticle will point in the direction of
       the firearm at the specified Distance. If Follow Mouse is enabled, the reticle
       will follow the exact position of the mouse.

   * - Distance
     - If Fixed Position is enabled, specify how far the reticle should be from the firearm.

------------

Charge
======

Charge the firearm to unleash a super charged bullet attack.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Projectile
     - The projectile used in the discharge attack.
 
   * - Charge Time
     - The time the user must hold a button before triggering a discharge. It is also possible
       to set a minimum threshold time in which the player can still discharge the firearm.

   * - Discharge Time
     - The time required to discharge the firearm completely.

   * - Cooldown Time
     - The time that must elapse before the next charge can begin.

   * - Shoot Animation
     - If enabled, it's the animation the character plays before discharging. The system will set the specified
       animation signal true. If using Sprite Engine, make sure the signal name exists, configure the Sprite State accordingly, and set to Loop Once. 
       If this is enabled, **a return signal is required or the system will stay stuck.** For a charging setup, only call ShootAndAnimationComplete ()
       once the animation is complete.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Event
     - 

   * - OnCharging
     - The Unity Event invoked when the firearm is charging.
 
   * - OnCharging Complete
     - The Unity Event invoked when the firearm finishes charging.
   
   * - OnDischarging
     - The Unity Event invoked when the firearm is discharging. This will return a value between 0 and 1, 
       representing the remaining discharge time.

   * - OnDischarging Complete
     - The Unity Event invoked when the firearm finishes discharging.

   * - OnDischarging Failed
     - The Unity Event invoked when the firearm fails to discharge. This can result from not having enough ammo.

   * - OnCooling Down
     - The Unity Event invoked when the firearm is cooling down. This will return a value between 0 and 1, 
       representing the remaining cool down time.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Recoil
     - 

   * - On Discharge
     - This recoil has the same properties as the default projectile recoil. While Discharging, specify
       if the player should recoil only once or as many times as required during the discharge period.

.. note::
   The charge system requires the user to hold a button for charging. Thus, it's best to set the trigger type of the 
   normal shoot button to On Press. This way, the fire arm won't be shooting bullets while charging. Also, the 
   projectile used for charging should be set with a high fire and projectile rate to take advantage of the continuous discharge.