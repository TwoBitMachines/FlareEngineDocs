High Jump
++++++++++

Launch a character into the air. This has two modes, Trampoline and Wind. Place this component 
on an empty gameobject. A blue rectangle gizmo will appear in the scene to modify its bounds for character detection. 
Typically, a trampoline will have a smaller collider area, and Wind will have a much taller collider area.

.. image:: ../images/interactables/TrampolineGif.gif
   :align: center
   :width: 100%
   
|

.. note::
   High Jump must also be enabled in the character settings.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 
   * - Type 
     - Launch the character with Trampoline, or gradually push the character upward with Wind.
       Wind typically has small values below 1. Trampoline has big values above 10.

   * - Force  
     - The amount of force acting on the character.

   * - On Trampoline
     - The Unity Event invoked when trampoline is triggered. Call a World Effect with the dynamic Activate method.