Push Back
+++++++++
.. complete!
If the player is damaged, apply a push back velocity in the relevant direction. This ability works in tandem
with the Health component. When the Health value changes, use its OnValueChanged Unity Event
and connect it to the ActivatePushBack method (found on the Push Back component). That's it. This event will send two values, damage and direction. 
If damage is negative, Push Back will commence.

.. note:: 
   Typically, Push Back is set to the highest priority so it can override all other abilities. For example, if the player is climbing a wall, the player 
   will fall down when Push Back is triggered.

.. Important:: 
   It's possible for the Crouch ability to override any ability if the player can't fully
   stand up due to a low ceiling. If this is the case, Push Back will not be triggered, even if it has a higher priority.
   To prevent this, add Crouch as an exception to Push Back so that both abilities can execute at the same time.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Distance
     - The total displacement in the x direction.

   * - Jump Force
     - The force applied in the y direction. This force is applied only once.

   * - Time
     - The total duration of the push back. The x velocity will be overridden during this time period.

   * - Sprite Renderer And Material
     - The player will be applied a damage flash during push back. Set the Sprite Renderer
       of the player. If the material is set, it will be applied to the Sprite Renderer; otherwise
       the color of the sprite will be tinted. You can use the Material Hurt that comes with the system.

   * - Color
     - The color of the flash.

   * - Flash
     - The number of times the flash occurs during push back.

.. tip:: 
   Use the signals to maintain the same direction of the Sprite during push back.

.. Important:: 
   If the damage flash is applied, the inspector will create a lag spike when the material is being swapped. To prevent this, 
   simply select another gameobject that is not the player.

**Signals: pushBack, pushBackLeft, pushBackRight**
