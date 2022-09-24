World Effects
+++++++++++++

The **WorldEffects** class is used for pooling effects. This is primarily used for displaying 
effects for bullet collisions. Since bullet collisions can occur frequently, the system 
will pool these effects and try to use them as efficiently as possible. Projectiles are equipped to call this 
class with a Unity Event that passes the ImpactPacket class. 

You can place this component on the World Manager's gameobject. In the inspector, 
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
     - Activates the effect specified by impact. Call this method using the projectile impact event.

   * - ActivatePlusDirection (ImpactPacket impact)
     - Activates the effect specified by impact. This will rotate the prefab according to the direction of the projectile. Call this method using the projectile impact event.

   * - Activate (string name, Vector3 position)
     - Activate the effect with this name at the provided position.

   * - ActivatePlusDirection (string name, Vector3 position, Vector2 direction)
     - Activate the effect with this name at the provided position and direction.