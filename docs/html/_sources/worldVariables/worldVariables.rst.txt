World Variables
+++++++++++++++
.. complete
These components allow you to create data that can be easily referenced. This data is also
automatically saved and restored during runtime to preserve important information. The three types of variables
used are **Float**, **String**, and **Vector3**. The **Health** component is also part of this group, 
but it works as a Float underneath the hood.

Each of these variables can be linked to a corresponding scriptable object. For example, if using the
Health component, the **WorldFloatSO** (scriptable object) that belongs to it can be used as a reference for UI elements 
to display the character's health. Any other system, like an enemy AI, can also read this value to change its behavior.
This will help decouple your systems because information is exchanged between gameobjects without 
creating hard references.

------------

Float And Health
================

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

   * - Recovery Time
     - If this is Health, the amount of time after being damaged where the character can't take any damage.

   * - Save
     - If enabled, the system will save and restore the current value.

   * - Is Scriptable Object
     - If enabled, a button will appear to create a scriptable object (**WorldFloatSO**). If created, it will be found in the AssetsFolder/Variables folder. If the scriptable
       object is no longer required, delete it manually.

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
     - If Save is enabled, the Unity Event invoked if the restored value is greater than zero (True) on Start. 

   * - On Load Condition False
     - If Save is enabled, the Unity Event invoked if the restored value is zero (False) on Start.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - 

   * - GetValue()
     - Returns the current value.

   * - Save()
     - Save the current value.

   * - SetValueAndSave(float value)
     - Set the current value and save it.

   * - Increment(float value)
     - Increment the current value.
 
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

------------

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

------------

String And Vector3
==================

These work in a similar fashion as Float. The respective scriptable objects are **WorldStringSO** and **WorldVector3SO**.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Events
     - 

   * - AfterLoad
     - If Save is enabled, the event invoked after the value has been restored. This occurs during Start. 

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - 

   * - GetValue()
     - Returns the current value.

   * - Save()
     - Save the current value.

   * - SetValueAndSave(type value)
     - Set the current value and save it.
 
   * - SetValue(type value)
     - Set the current value.