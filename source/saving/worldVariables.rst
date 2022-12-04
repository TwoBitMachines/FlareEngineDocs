World Variables
+++++++++++++++

These components allow you to create data that can be easily referenced. This data is also
automatically saved and restored during runtime to preserve important information. The four types of variables
used are **Float**, **Bool**, **String**, and **Vector3**. The **Health** component is also part of this group; it inherits from Float

Each of these variables can be linked to a corresponding Scriptable Object. For example, if using the
Health component, the **WorldFloatSO** (Scriptable Object) that belongs to it can be used as a reference for UI elements 
to display the character's health. Any other system, like an enemy AI, can also read this value to change its behavior.
This will help decouple your systems.

Float And Health
================

Both the Float and Health components work very similarly. The Health component just implements a few extra properties.

This class makes use of something called a **tempValue**. The temporary value simply makes it easier to save 
or delete the current value in case it needs to revert. One scenario is where the Float variable is being used 
to collect coins. Perhaps you want the coin amount that hasn't been saved to be lost when the player dies or 
the game resets. The tempValue will make it easy to remove the unsaved coin amount. You will need to call the 
appropriate methods to work with this value, and typically, you will also want to use the Save Manually Only option,
so you can control this value completely.

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
     - If enabled, the character won't take damage in the direction it is facing. This is still experimental.

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

World Float HUD
===============

**WorldFloatHUD** is a convenient class for displaying world float values using UI elements. This class can also work with other classes 
like Projectile and Firearms to display ammunition values. The UI element style is left to your personal taste. This class will 
simply enable images and set values.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Type
     - Discrete items will display the value in terms of UI images. Think health hearts. Specify the sprites that represent an empty and full value. Must also
       set number of UI images that will be used to display the value. Continuous will display the value by modifying the fillAmount of an image. 
       Numbers will use a TextMesh to display the value.

   * - Value Type
     - Only set the reference for one of these to display the value. For Projectile, Firearms, and Tool the value represents ammunition amount.
       To set Firearms simply drag the player gameobject into this field. This will display the ammunition amount for the current firearm the player has
       active. To set tool, drop any Firearm into this field.

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