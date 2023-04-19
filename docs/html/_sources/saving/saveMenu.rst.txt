Save Menu
+++++++++

The Save Menu will save the entire progress of a single game session. 
Each save slot can be saved, copied, and deleted. This will not require 
any changes to other save systems, such as World Variables, Check-Points,
or Inventory.

To start, go to the Save Options tab in the World Manager and enable 
Is Save Menu. This tells the system that the current scene is the 
Save Menu. Note that the World Manager turns purple to indicate this,
and this option should be disabled in other scenes.

Next, create the desired number of save slots. Each save slot is 
automatically indexed starting from zero. The index is considered the 
save slot's ID. Although you can choose the current save slot for 
convenience in the inspector, this will usually be chosen during 
runtime in the Save Menu.

This system offers two optional parameters that can be displayed: 
the total time played and the maximum level the player has reached. 
To specify which level you're on, use the Level Number field. You'll
need to enter this number manually in each scene. The total time played 
is tracked automatically by the World Manager.

---------

The Save Menu is constructed from UI elements that can be customized 
to your liking. There are two components to be aware of: the **Save Menu** 
and the **SaveSlotUI**. For an example, refer to the Save Menu tidbit scene.

Save Menu
=========

This component is responsible for managing, copying, and deleting slots.
Each save slot must be a child object of the Save Menu. This component has two UI 
elements it can set: the highlight image, which highlights the current 
slot the player has moved to in the menu, and the selected image, which 
always points to the officially selected save slot. Clicking a save slot 
twice will make it the official save slot.

To copy and delete slots, you will need to call the proper methods through
other UI elements such as buttons.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Highlight
     - The RectTransform reference for the highlight image.

   * - Selected
     - The RectTransform reference for the selected image.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Method
     - 

   * - CopySlotData()
     - Call this method to copy the current slot. There must be an empty 
       slot fo this work.

   * - DeleteSlotData()
     - Call this method to delete the current slot.

Save Slot UI
============

This is a selectable UI element and sets the total play time and 
current game level information; these are optional and can be 
left unreferenced. This game object should be placed as a child 
of the Save Menu.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Play Time Text
     - The TextMeshPro reference for displaying the total time played.

   * - Level Text
     - The TextMeshPro reference for displaying the current game level.
