Teleport
++++++++
.. complete!
Any gameobject that enters the collider2D on any gameobject with the Teleport component will be teleported to the specified destination. 
It is perfectly possible to create bidirectional teleports that work together.

.. image:: ../images/interactables/TeleportGif.gif
   :align: center
   :width: 100%
   
|

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Destination
     - The transform where the gameobject will be teleported to.

   * - LayerMask
     - Only gameobjects on this layer mask will be teleported.

   * - On Teleport
     - The event invoked when a gameobject is teleported.