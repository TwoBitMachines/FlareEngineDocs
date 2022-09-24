Zipline
++++++++

Allow the player to zipline. This component works directly with Unity's Line Renderer. Modify the necessary settings there, mainly
the width and color of the line. The player ability, **Ziplining** must be enabled. Place this component on an empty gameobject 
and scene gizmos will appear. The gameobject's position will be the start position, and a red gizmo will modify the end position. 

.. image:: ../images/interactables/ZipLineGif.gif
   :align: center
   :width: 100%
   
|

.. note::
   Don't forget to add a material to the Line Renderer (Default-Line).

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Lines      
     - The number of lines in the zipline.
 
   * - Gravity       
     - The force of gravity acting on the zipline.

   * - Up Friction 
     - The friction exerted on the player if moving up the zipline. To ignore, leave as zero.

   * - Bounce 
     - The force exerted on the zipline when interacting with the player.
  
   * - Stiffness
     - The larger the number, the less sag the zipline will have. For performance, keep this value below 30.

   * - Line Renderer
     - The reference to Line Renderer.

   * - Area
     - The system will check for ziplines once the player is inside this area. 
       The area width is set automatically, but the height must be specified. The offset will offset the area in the y direction.

   * - Create On Awake
     - If enabled, the zipline will recreate itself on Awake in case it was moved. Typically, you want to initialize this during editor time to reduce initializing time.

   * - Create
     - Once all the settings are chosen, press this button to create the zipline. Anytime you change the position or a setting, recreate the zipline to enact the changes.

   * - View
     - If enabled, the zipline gizmos will be visible.

.. important::
   The start of the zipline corresponds to the transform's position. Make sure the transform's handle position is set to Pivot (and not to Center) for proper placement.
   A scene handle tool, a red circle, is used to specify the end of the zipline. The distance between the start and end points determines the length of the zipline.