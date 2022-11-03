World Effects
+++++++++++++

The **WorldEffects** class is used for pooling effects. This is primarily used for displaying 
effects for bullet collisions. Since bullet collisions can occur frequently, the system 
will pool these effects and try to use them as efficiently as possible. Projectiles and other classes are equipped to call this 
class with a Unity Event that automatically passes the ImpactPacket class, which will contain the name of the effect, position, 
and direction. 

There are two types of effects. Regular effects (depicted in blue) are meant for general purpose effects.
Damage Effects (depicted in red) display the damage inflicted on an enemy and thus require a TextMeshPro-Text component on the 
gameobect. Once the damage effect is activated, the system will updates its text value to reflect the damage value.

You can place the World Effect component on the World Manager's gameobject. In the inspector, 
create a new element by clicking the add button. Name and set the gameobject reference of the effect. The effect 
can be anything, a particle system, a sprite, but whatever it is, it must have the ability to turn its gameobject 
to active false upon completion.

You can also use this class with WorldManger.get.effects (using TwoBitMachines.FlareEngine).

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - 

   * - Activate (ImpactPacket impact)
     - Activates an effect. 

   * - ActivatePlusDirection (ImpactPacket impact)
     - Activates an effect. This will rotate the prefab according to a direction. 

   * - ActivatePlusRawAngle (ImpactPacket impact)
     - Activates an effect. This will rotate the prefab according to an angle. 

   * - Activate (string name, Vector3 position)
     - Activate the effect with this name at the provided position.

   * - ActivatePlusDirection (string name, Vector3 position, Vector2 direction)
     - Activate the effect with this name at the provided position and direction.
    
   * - ActivateDamageEffect (ImpactPacket impact)
     - Activates the damage effect specified. 

   * - ActivateDamageEffect (string name, string value, Vector3 position)
     - Activate the damage effect with this name at the provided position. The value represent the damage value.