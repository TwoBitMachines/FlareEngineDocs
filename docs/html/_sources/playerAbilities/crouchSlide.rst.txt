Crouch Slide
++++++++++++

Let the player slide while crouching. The slide will come to a halt after the specified time. 

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Button
     - If pressed, the crouch slide will commence.

   * - Slide Type
     - If Constant Velocity is enabled, the player will slide with a constant speed. Otherwise, it will slow down to a halt.

   * - Crouch Height
     - The new height of the player. This will modify the vertical size of the BoxCollider2D.

   * - Speed Threshold
     - The velocity the player must reach to enter a slide.

   * - Slide Time
     - Max time specifies the total duration of the slide. Min time specifies the minimum amount of time the player will have to slide before exiting early.

.. important:: 
   The crouch signal will go true if the player can't properly stand after it completes a slide.

**Signals: crouchSlide, crouch**
