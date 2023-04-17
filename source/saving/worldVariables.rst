World Variables
+++++++++++++++

These components create easily referenced data that is automatically saved and restored 
during runtime to preserve information. They consist of **Float**, **Bool**, **String**, 
and **Vector3** variables, as well as the **Health** component, which inherits from Float. 
They are extremely useful for remembering game state. A common use case it to use World Bool 
to remember unlocked doors.

Each variable can also be linked to a corresponding Scriptable Object. For instance, the Health 
component's associated **WorldFloatSO** can be used as a reference for UI elements to display 
the character's health, or by an enemy AI to alter its behavior, helping to decouple systems.

Float And Health
================

The Float and Health components have similar functionality, with Health having some 
additional properties.

For advance use, both components can make use of a temporary value to make it easier to save 
or delete the current value. For example, if the Float variable is being used to collect coins,
the tempValue can be automatically cleared to remove unsaved coins when the player dies or the 
game resets. To work with the temporary value, you must call the appropriate methods, and use 
the Save Manually Only option to have complete control over it.

.. tip::
 Float can be treated as a boolean by setting its value to either 1 or 0 (True or False).

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Name ID
     - The name of the variable. If using the save system, this name must be unique. Click the generate button to create a unique Name ID if necessary.
 
   * - Value
     - The current value. This is the value that will be saved.
 
   * - Clamp
     - Clamp the current value.

   * - Broadcast Value
     - If enabled, and if the current value changes, this will also set the current value for all variables with the same Name ID.

   * - Save
     - If enabled, the system will save and restore the current value. During development, press the delete icon to erase saved data.
       If Save Manually Only is enabled, the Save() method must be called to save the data. The system won't automatically do it at the end of the scene.

   * - Is Scriptable Object
     - If enabled, create a Scriptable Object (**WorldFloatSO**) that will be placed in the AssetsFolder/Variables folder. If the Scriptable
       Object is no longer required, delete it manually.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Extra Health Properties
     - 

   * - World Effect
     - If name of the effect that will be invoked if using ImpactPacket.

   * - Recovery Time
     - The amount of time after being damaged where the character can't take any damage.

   * - Hash Shield
     - If enabled, the character can only take damage according to the direction of the shield, which is either 1 or -1. 
       For example, if the shield direction is 1, the character can only take damage from behind.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Events
     - 

   * - On Min Value
     - The Unity Event invoked when the current value reaches the minimum value.
 
   * - On Max Value
     - The Unity Event invoked when the current value reaches the maximum value.
 
   * - On Value Changed
     - The Unity Event invoked when the current value has been changed. This is invoked with the change in value and the direction of damage, if using Health.

   * - On Load Condition True
     - The Unity Event invoked if the value is greater than zero (True) on Start. 

   * - On Load Condition False
     - The Unity Event invoked if the value is zero (False) on Start.

   * - On Shield Hit
     - The Unity Event invoked when the shield mechanic blocks an enemy attack.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - 

   * - GetValue()
     - Returns the current value.

   * - Save()
     - Save the current value.

   * - DeleteSavedData()
     - Delete the current saved data.

   * - SetValueAndSave(float value)
     - Set the current value and save it.

   * - Increment(float value)
     - Increment the current value.

   * - IncreaseTempValue(float value)
     - Increment the temporary value. This will bypass the OnMinValue, OnMaxValue, and OnValueChanged events.

   * - SetValue(float value)
     - Set the current value.

   * - CanIncrement(bool value)
     - If false, the current value can't be incremented.

   * - SetTrue()
     - Give the current value a value of 1f.

   * - SetFalse()
     - Give the current value a value of 0f.

   * - CanTakeDamage(bool value)
     - If this is Health, the layer on this gameobject will be switched to the ignore raycast layer if False. Will revert on True.

   * - SaveTempValue()
     - This will save the current value if you are using temporary value.
  
   * - ClearTempValue()
     - This will clear the temporary value. This is called on each game reset.

String, Bool, And Vector3
=========================

These work in a similar fashion as Float. The respective Scriptable Objects are **WorldStringSO**, **WorldBoolSO**, and **WorldVector3SO**.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Events
     - 

   * - AfterLoad
     - The event invoked after the value has been initialized. 

   * - On Load Condition True
     - For Bool, the Unity Event invoked if the value is True on Start. 

   * - On Load Condition False
     - For Bool, the Unity Event invoked if the value is False on Start.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - 

   * - GetValue()
     - Returns the current value.

   * - Save()
     - Save the current value.

   * - DeleteSavedData()
     - Delete the current saved data.
     
   * - SetValueAndSave(type value)
     - Set the current value and save it.
 
   * - SetValue(type value)
     - Set the current value.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - For Bool

   * - SetTrue()
     - Set value true.

   * - SetFalse()
     - Set value false.

   * - IsTrue()
     - Returns true if value is true.

   * - IsFalse()
     - Returns true if value is false;

World Float HUD
===============

**WorldFloatHUD** is a convenient class for displaying world float values using UI elements. 
This class can also work with other classes like Projectile and Firearms to display ammunition 
values. The UI element style is left to your personal taste. This class will simply enable 
images and set values.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Type
     - Discrete items will be displayed as UI images, such as health hearts, with specified sprites 
       for empty and full values. The number of UI images used to display the value must also be set.
       For continuous items, the value will be displayed by modifying the fillAmount Property of a UI Image.
       For numeric values, a TextMesh will be used to display the value.

   * - Value Type
     - Only set the reference for one of these to display the value.For Projectile, Firearms, and Tool, 
       the value represents ammunition amount. To display the ammunition amount for the player's current 
       firearm, drag the player gameobject into this field. To display the ammunition amount for a tool, 
       drop any firearm into this field.

   * - Can Increase
     - This feature will allow Discrete Items to increase its item count as the game progresses, such as increasing
       the number of hearts the player has. For proper use, you must create the maximum number of discrete items and set their
       references. During runtime, call the IncreaseDiscreteValue method to increase the item count. If Saved Manually
       is enabled, the current items available will be saved each time this method is called. Otherwise, call the SaveDiscrete 
       method to control when this is saved.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - For Bool

   * - IncreaseWorldFloat()
     - If the HUD type is for discrete items, call this method to increase the World Float or Health variable being
       used. This ensures that it doesn't increase more than the visual discrete items available.