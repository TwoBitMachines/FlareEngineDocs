World Effects
+++++++++++++

The **WorldEffects** class will instantiate gameobjects and pool them. These gameobjects 
typically represent some type of game effect like a particle system, but they can be anything. The most 
common use case is to call an effect when an enemy is damaged.

The Health and Projectile components, as well as many other components, have a Unity Event
for calling the Activate method in WorldEffects to instantiate the correct game effect. The information passed will contain
the name of the effect, the position, and direction that will be applied to the effect. This information
is packed automatically using the ImpactPacket class. Usually, somewhere in the inspector there is a field asking you to type in the 
name of the effect.

When you create an effect, it must usually have the ability to deactivate itself when it's complete. For example,
if you're using Sprite Engine to play a sprite effect, use the On Loop Once Unity Event to deactivate the 
gameobject by choosing GameObect.SetActive to false. If you are using a particle system, you can use the 
Basic Timer component that will deactivate the gameobect after a certain amount of time. When the object is 
deactivated, the system will pool it and activate it again when it's needed.

As alluded, the game effects don't necessarily have to be particle types. You can use a LetsWiggle component, too.
For example, every time an enemy is hit, you can set a LetsWiggle to briefly change the x and y scale of the 
transform to create a stretch effect (though do remember to set the scale values back to 1). 

If the gameobjet contains a TextMeshPro, the system will write the damage value to the text to display 
the damage applied to the enemy. This also usually contains a LetsWiggle to move the text.

There is also a Splatter effect you can apply to any surface. Any surface that will receive splatter must contain the 
material SplatterSurface. The sprite that is the splatter must contain the material Splatter. This is great for 
creating blood effects.

To set this system up, create an empty gameobject and add the WorldEffects component to it. Place
each gameobject effect as a child of this object and press the Grab Effects button to register them. The name of the 
gameobject is the name of the effect the system will look for. During runtime, all the instantiated effects will 
be placed here.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - 

   * - Activate (ImpactPacket impact)
     - Activates an effect. 

   * - ActivateWithDirection (ImpactPacket impact)
     - Activates an effect. This will rotate the prefab according to a direction. 

   * - ActivateWithInvertedDirection (ImpactPacket impact)
     - Activates an effect. This will rotate the prefab according to an inverted direction.

   * - ActivateWithMirrorDirection (ImpactPacket impact)
     - Activates an effect. This will flip the effect on its y axis if the impact's x direction is negative.

World Effect Request
====================

This component allows you to specify the effect you want to call and to modify its position, among other related properties. 
This is optional but convenient. Its main purpose is to work with **ReactionProfile**, which
allows you to group related game effects and reactions into one place, so they can serve as a reaction profile for any AI or object that calls it. This will 
reduce the amount of work and connections you have to make.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - 
     - 

   * - Activate
     - Choose the Activate method.

   * - Type
     - Set the correct type for LetsWiggle and TextMeshPro effects. 

   * - Position
     - This position is where the effect will be instantiated. The position is usually determined by the collider of a character, but not always.
       For example, the center position is the exact center of the character's collider. For blood splatter, you might want to pick the bottom position 
       to instantiate the gameobject effect near the feet of the enemy.

   * - Quantity
     - The number of effects that you want to instantiate. You can also randomize this value between a min and max value.

   * - Controller
     - A reference to WorldEffects. If this reference is empty, the system will call WorldEffects through a static method (if one exists).

   * - Random Rotation
     - Apply a random rotation to the effect. The min and max values represent the range of possible random values.

   * - Random Offset
     - Apply a random offset to the position of the effect. The min and max values represent the range of possible offset values.

   * - Check For Walls
     - If enabled, this will check if the effect is being instantiated inside a wall. If it is, the gameobject's position will
       be set to the center position of the character or object that is calling it.
       
   * - Effect Name
     - The name of the effect you want to instantiate. If more than one effect is specified, the system will randomly pick between them. 