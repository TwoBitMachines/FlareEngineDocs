Options Binding Menu
++++++++++++++++++++

The Options Binding Menu provides a user interface template for adjusting
various settings in a game, including key bindings, music volume, SFX volume, 
full-screen mode, and screen resolution. All settings are saved in PlayerPrefs 
and will persist. The UI should be customized to your preference. For an example,
please check the tidbit scene OptionsBindingMenu

.. tip::
   Make sure the Input System is updated to at least version 1.4.1 (Package Manager).

For key bindings, the system utilizes two scripts. To rebind keys for the new
Input System, use **RebindNewInput** created by Unity. To rebind keys for 
the old input system, use **RebindInputButtonSO**. 

.. warning::
   Since the old inputs are being stored in scriptable objects, any key changes you make 
   during runtime will not reset on PlayMode exit.

Options Binding Menu
====================

This component holds the UI references and configures their events. Additionally, 
you will need to set the references for the Audio Manager and Input Action 
(if modifying keys in the new input system). You can place this component on 
the parent canvas object.

Rebind Keys
===========

Use the provided Rebind objects in the example scene as templates. It is possible 
to represent the binding key as a label or an icon. If implementing Icons,
populate the **SetInputIcons** with sprites for both the old and new inputs. These components 
can be found in the parent canvas. Finally, each **RebindKey** should have an image element 
as a child to represent the Icon.

When the **RebindKey** is pressed, the system will wait for any input to be 
pressed and use that as the new key. As of now, the only way to cancel a rebind is by 
pressing the Esc key.

**RebindNewInput** is a script created by Unity. In this script, you will specify the Action, 
which represents the New Input you wish to modify. This script holds references to UI elements.
**RebindInputButtonSO** will modify old inputs.

.. list-table::
   :widths: 25 100
   :header-rows: 1

   * - Property
     - 

   * - Input Button SO
     - Reference to the old input you wish to modify

   * - Reset Key To
     - When the Reset All button is pressed, it will reset the input to the specified keys.

   * - Key Label
     - The UI reference to the key label.

   * - Binding Label
     - The UI reference to the binding label. This will display the assigned key or mouse value.

   * - Override Key Label
     - If enabled, the system will not automatically update the Key Label.

   * - Rebind Events
     - The events invoked when the binding process starts and stops.