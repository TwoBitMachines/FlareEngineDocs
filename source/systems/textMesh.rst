Text Mesh Pro Effects
+++++++++++++++++++++
.. complete!
Create special effects for any TextMeshPro. This includes the classic typewriting effect and a variety of other effects that can
be applied to individual words or sentences. Since the system is working with TextMeshPro, feel free to apply Rich Text Tags to your text. 
This system makes specif use of **<link>** for many of the effects below.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Text Mesh  
     - The TextMeshPro that will have the effects applied to it.
 
   * - Typewriter Speed 
     - The speed at which letters are typed.

   * - Typewriter Wobble
     - The wobble effect applied to the letters as they are typed.
  
   * - Typewriter Fade
     - The fade effect applied to the letters as they are typed. The larger this number, the longer the fade effect will last. 

   * - Wobble
     - Apply a wobble like motion to words.
       
       
       To apply: **<link="wobble">This is a Wobble</link>**

   * - Wave
     - Apply a wave like motion to words. Specify the speed, strength, and phase.
       
       To apply: **<link="wave">This is a Wave</link>**

   * - Jitter
     - Jitter will have the effect of shaking the words. Specify the rate at which it occurs, and its strength.
       
       
       To apply: **<link="jitter">This is a Jitter</link>**

   * - Distortion
     - This will distort the words. Specify the rate at which it occurs, and its strength.
       

       To apply: **<link="distortion">This is a Distortion</link>**

   * - Pause
     - This will pause the typewriter for the specified time.


       To apply: **<link="pause1"></link> These words will not be typed until 1 second has elapsed.** 


       To apply: **<link="pause0.5"></link> These words will not be typed until 0.5 seconds have elapsed.** 

   * - Speed
     - This will change the typewriter speed.

       To apply: **<link="speed3"></link> These words will be typed with a speed of 3.** 