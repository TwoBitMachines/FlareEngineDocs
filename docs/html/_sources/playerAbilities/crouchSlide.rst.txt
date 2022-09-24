Crouch Slide
++++++++++++

Let the player slide while crouching. The slide will come to a halt after the specified time. 

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Button
     - If pressed, the player will check if can crouch slide.

   * - Crouch Height
     - The new height of the player. This will modify the vertical size of the BoxCollider2D.

   * - Threshold
     - The velocity the player must be greater or equal to in order to enter a slide.

   * - Slide Time
     - The total duration of the slide.

.. important:: 
   The crouch signal will go true if the player can't properly stand after it completes a slide.

**Signals: crouchSlide, crouch**
