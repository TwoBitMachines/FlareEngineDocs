Projectiles
+++++++++++

Projectiles are used for shooting, and there are four basic types: Bullet, Instant, 
Short Range, and Grappling Gun. Each type can be customized to create a wide variety
of options. When a projectile hits a game object that has a Health component and 
exists in the target layer, it will deal damage.

To ensure the positions of the projectiles are preserved, it is recommended to have 
the **Projectile** component in a game object with a static parent. The Projectile component 
takes care of creating an object pool and managing the life cycle of all the projectiles.

Projectile
==========
.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
   * - Name. 
     - Name the projectile. This must be unique for identification purposes.

   * - Projectile Type. 
     - A Bullet is a discrete gameobject. Instant is a raycast. Short Range is a BoxCollider2D. Grappling Gun is a raycast with a LineRenderer.
 
   * - Ammo Type 
     - If Discrete is enabled, the ammo count will be decreased by a unit of one. If Continuous is enabled,
       the ammo will be decreased by a unit of time. Typically, a Bullet is set to Discrete, Short Range is set
       to Continuous, and Instant can be either depending on the setup. If Infinite is enabled, ammo will never run out.

   * - Ammo Amount
     - The available ammo for shooting. If Continuous is enabled and the value is 10, the projectile 
       can provide the firearm with 10 seconds of shooting, for example. The max value clamps the ammo count.
  
   * - Ammo Damage
     - The amount of damage dealt to any target with a Health component.

   * - Ammo Force
     - The forced applied in the direction of damage.

   * - Fire Rate
     - How often a firearm can shoot this projectile. A value of zero will mean the firearm can shoot this projectile
       every frame.

   * - On Ammo Reload
     - The Unity Event invoked when the ammo count is increased.

   * - On Ammo Empty
     - The Unity Event invoked when the ammo count is zero.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - 

   * - ChangeAmmo(float value) 
     - Increase or decrease the ammo amount.
 
   * - AmmoCount()
     - Returns the ammo amount.

   * - EnoughAmmo()
     - Returns true if the ammo amount is greater than zero.

   * - AmmoIsInfinite()
     - Returns true if the ammo is infinite;

   * - AmmoMax()
     - Returns the maximum ammo amount;

   * - AmmoPercent()
     - Returns the percent of ammo remaining.

Bullet
======

There are six bullet types, each with a different behavior. There's also no limit on how many firearms can reference a
projectile type, making it great for saving resources.

.. important:: 
   First create a gameobject that contains the bullet's sprite and make it a child of the Projectile gameobject;
   only then will the properties bar appear. **For proper function, set the Sprite Pivot to Left. If using bounce, set Pivot to Center.**

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Setup

   * - Bullet Type
     - Basic, Bounce, Bounce4R, Colliding, Seeker, StickToWall.
       
   * - Pool Size 
     - The total number of bullets that can exist in the scene. The bullets will be created as needed and will never be destroyed.
 
   * - Projectile Rate
     - The amount of bullets discharged during a single firing event. If this value is greater than one, then it's possible to create 
       bullet patterns with the properties below.

   * - Position Flux 
     - This will vary the start position of a bullet in the y direction by the specified value.
 
   * - Angle
     - The angle at which bullets will be fired relative to other bullets.

   * - Separation
     - The relative space between bullets in the x and y direction.
  
   * - Direction
     - If Weapon Direction is enabled, bullets will be fired according to the pattern settings. If Circular Direction is enabled,
       it will ignore those settings and shoot the bullets radially.

The bullet types share some of the following properties below. In the case of the Seeker type, it will ignore the gravity setting.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Layer
     - The target layer the bullet will interact with. The most common layers are enemies and walls.
       
   * - Ignore Edges
     - Specify how to handle Edge Collider 2D collisions. If Ignore If Up Direction is enabled, a bullet will ignore this
       collision if the bullet has a positive y velocity.
 
   * - Life Span
     - The amount of time the bullet can be active in the scene.

   * - Speed
     - How quickly the bullet moves.
 
   * - Gravity
     - If this value is greater than zero, the bullet will be affected by gravity.

   * - Blast Radius
     - If this value is greater than zero, the bullet will deal damage to any target within
       this radius when the bullet collides or time expires.

   * - World Effect
     - The name of the world effect that will be used on impact. If not needed, leave empty.

   * - Bullet Rays
     - Bullets use only one raycast to detect targets. If more are needed, specify that number here.
       
   * - Bullet Size
     - Specify the correct size of the bullet for proper bullet collision.

   * - Add Momentum
     - If enabled, the character's velocity will be combined with the bullet's velocity.

   * - Invert Y
     - Since bullets can be rotated, this will invert they y scale to keep the sprite looking correct. If bullet is symmetrical, ignore.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Event
     - 

   * - On Fire
     - The Unity Event invoked when successfully fired.
  
   * - On Impact
     - The Unity Event invoked when the bullet makes any kind of contact. This event can 
       also invoke world effects. If the impact effect is specified, the hit point and direction will be applied to the world effect.
       
   * - On Hit Target
     - The Unity Event invoked when the bullet hits a target that contains the Health Component. This event can 
       also invoke world effects. If the impact effect is specified, the hit point and direction will be applied to the world effect.
 
   * - On Life Span Expired
     - The Unity Event invoked when the bullet's time expires. The position of the bullet is returned.

------------

Basic 
=====

This is the most basic bullet. It has no extra properties.

Bounce 
======

This bullet will bounce off walls. By default, this will check for World and Platform collisions if the y velocity is negative.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - Common

   * - Bounce Friction
     - If this value is greater than zero, every time the bullet bounces off a wall, it will lose velocity in the specified axis.

   * - Bounce Radius
     - The radius of the bullet. Required for collision checks.
       
   * - Bounce Spin
     - How much the bullet spins on its axis. If the bullet is a bouncing ball (that means gravity is enabled), then set 
       this to a nonzero value, or else the bullet will constantly rotate according to its direction, which might look
       inappropriate for a bouncing ball.

   * - No Spin
     - If enabled, the bullet will not rotate.

   * - Active After Hit
     - If enabled, the bullet will keep moving event after hitting damageable objects.

.. important:: 
   Bounce and Bounce4R work exactly the same. However, Bounce4R uses four raycasts to detect walls. Use Bounce4R
   if more perfect collisions are necessary.

Colliding
=========

This bullet uses a Collider2D instead of raycasts to detect targets.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Expire On Impact
     - If enabled, the bullet will not deactivate once it collides.

.. important:: 
   Add a Collider2D (set Is Trigger true) and a RigidBody2D (set to Kinematic) 
   to the bullet, or else there will be no collisions. The target layer should be used primarily for enemies
   and not wall collisions.

Seeker
======

This bullet will curve, change directions, to follow  a target.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
   * - Search Radius
     - The radius around the bullet's position used for finding targets.
       
   * - Search Rate
     - The bullet will execute a find function at the specified rate until it finds a target to latch to.

   * - Turn Speed
     - How quickly the bullet can change direction.

   * - Find
     - If Random Target is enabled, and if more than one target is found, the bullet will pick a random target from the list to follow. 
       If Nearest Target is enabled, the bullet will follow the nearest target found.

.. important:: 
   Since the Seeker bullet can take wide turns, the target layer should not contain walls or else 
   the bullet will deactivate on a wall collision.

Stick To Wall
=============

This bullet can stick to walls. Perfect for arrows!

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
       
   * - Stick Timer
     - The amount of time the bullet sticks to the wall before deactivating.

   * - OnStickToWallExpire
     - The Unity Event invoked when the bullet is done sticking to the wall. The bullet's position is returned.

-----------

Instant
=======

A raycast is used to instantly hit a target.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
   * - Layer
     - The target layer the raycast will interact with. The most common layers are enemies and walls.
       
   * - Ignore Edges
     - Specify how to handle Edge Collider 2D collisions. If Ignore If Up Direction is enabled, a raycast will ignore this
       collision if the raycast has a positive y velocity.

   * - On Idle
     - If Deactivate GameObject is enabled, the gameobject will bet set Active false when the firearm is no longer shooting. This is
       useful in case this gameobject has a sprite that represents the raycast. If Leave As Is is enabled, it will
       leave this gameobject in its current state.

   * - Max Length
     - The length of the raycast.

   * - Hit Rate
     - If the firearm is fired continuously, set the rate at which a target can be hit. If left to zero, this means a target will
       be applied damage every frame. Avoid this to make the damage applied frame independent.
   
   * - On Fire
     - The Unity Event invoked when successfully fired.

   * - Impact Object
     - The gameobject that will be set active true at the impact point. Useful for particle effects for a laser. If not needed, leave empty.

   * - Impact Effect
     - The name of the world effect that will be used on impact. If not needed, leave empty.

   * - On Impact
     - The Unity Event invoked when the raycast makes a hit. This event is called at the same time as Hit Rate. This event can 
       also invoke world effects. If the impact effect is specified, the hit point and direction will be applied to the world effect.
 
.. important:: 
   It's possible to place a sprite on this projectile to act as a visual laser. Set the Sprite Pivot to Left to properly
   scale the sprite image from firearm to hit point.

-----------

Short Range
===========

A BoxCollider2D will search for targets to hit.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
   * - Layer
     - The target layer the BoxCollider2D will interact with.
       
   * - Collider
     - Place a BoxCollider2D component on this gameobject, configure the size, then set the reference here

   * - On Idle
     - If Deactivate GameObject is enabled, the gameobject will bet set Active false when the firearm is no longer shooting.
       If Leave As Is is enabled, it will leave this gameobject in its current state.

   * - Hit Rate
     - If the firearm is fired continuously, set the rate at which a target can be hit. If left to zero, this means a target will
       be applied damage every frame. Avoid this to make the damage applied frame independent.

   * - On Fire
     - The Unity Event invoked when successfully fired.
      
.. tip:: 
   Place a sprite to go along with the BoxCollider2D. There's also a Flame Thrower component made specifically for this projectile type.
   Place it on this gameobject and configure the particle properties to shoot some flames!

-----------

Grappling Gun
=============

The Grappling Gun projectile differs from the other types as its primary purpose is not to 
inflict damage. Instead, it is designed to attach to walls and enable players to propel 
themselves towards the wall for traversal within a level. To visualize the grappling rope, 
a LineRenderer, is required. This LineRenderer can be included in the same component as 
the Projectile. 

For proper function, this projectile should exist on a gameobject that is a child of the 
player. Please refer to the GrapplingGun tidbit scene for an example.

.. tip:: 
   Change the local positions of the grappling gun and grappling rope to determine where to shoot 
   and extend the rope from. Since the grappling gun is a Firearm, it's local position will need 
   to be changed in the Firearm component.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
   * - Layer
     - The target layer the grappling gun can attach to.
       
   * - Line Renderer
     - Reference to the Line Renderer component and the number of points it can have.

   * - Line Length
     - Maximum and minimum rope length. If a wall is beyond the max range, no attach
       point is found. If retract is enabled, the min length is the shortest possible length.

   * - Shoot Curve
     - Animates the rope during shooting. Specify the curve animation and amplitude.

   * - Shoot Speed
     - Determines the speed of the shooting curve animation.
      
   * - Swing Force
     - Applies force to the swinging motion of the rope when the player moves in the x direction.

   * - Jump Away
     - Applies a jump force to the player, allowing them to detach from the grappling gun.

   * - Gravity
     - Applies gravitational force to the rope.

   * - Retract
     - When enabled, the grappling gun propels towards the attached wall at the specified speed.

   * - Friction
     - Applies friction to the retracting rope.

   * - Type
     - If set to Automatic, the rope will retract automatically. Otherwise, manual retraction requires pressing a button.


Projectile Inventory
====================

This holds a list of projectiles. The inventory system uses this list to swap projectiles on a firearm. Create as 
many as necessary since firearms can reference different projectile inventories.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Projectile References
     - The list of projectile references. Create as many as necessary.