Slope Slide
+++++++++++

The player will slide down slopes and deal damage.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Button   
     - The button that will initiate a slope slide. If set to automatic, the player will automatically slide down a slope.

   * - Speed Boost 
     - Scale the horizontal speed while slope sliding.

   * - Exit Time
     - If this value is greater than 0, the player will continue to slide for this amount of time after it's no longer on the slope.
       The signal slopeSlideAuto will go true during this time period.

   * - Deal Damage
     - If enabled, the player will be able to deal damage to enemies while slope sliding. During this time, the player will not be 
       able to receive damage. Set the layer to deal damage, the amount of damage, and the forced applied in the direction of damage.

**Signals: slopeSlide, slopeSlideAuto**
