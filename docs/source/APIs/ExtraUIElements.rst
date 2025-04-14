==========
ExtraUIElements
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

This module provides a set of premade UI elements and menus. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 


Menus
-----

OpenSaveFileMenu
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   ExtraUIElements.OpenSaveFileMenu(InputData:table) -> table

Opens a save file dialog and returns the saved file. :raw-html:`<br />`

.. note::
    The ``InputData`` table has to have these values inside with these exact names! :raw-html:`<br />`

``StartPath`` The path where the save dialog should open in. :raw-html:`<br />`
``AllowedFileTypes`` The file extestions that are allowed to be saved. (e.g. ``{".txt", ".txt2"}``) :raw-html:`<br />`
``Data`` The data to be saved in the file. :raw-html:`<br />`



OpenOpenFileMenu
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   ExtraUIElements.OpenOpenFileMenu(InputData:table) -> table

Opens a open file dialog and returns the opened file. :raw-html:`<br />`

.. note::
    The ``InputData`` table has to have these values inside with these exact names! :raw-html:`<br />`

``StartPath`` The path where the open dialog should open in. :raw-html:`<br />`
``ExtraText`` Some info text displayed in the dialog. :raw-html:`<br />`



CreateDropdownMenu
~~~~~~~~~~~~~~~~~~

.. code-block:: luau  

   ExtraUIElements.CreateDropdownMenu(OptionsFrame:instance, Options:table, callback:function) -> string

Creates a dropdown menu and calls a callback function once a option has been selected. :raw-html:`<br />`
``OptionsFrame`` The UI object under which the dropdown menu apears. :raw-html:`<br />`
``Options`` The options the menu should have. (e.g. ``{"Option 1", "Option 2"}``) :raw-html:`<br />`
``callback`` The function that gets called once a option has been picked, this also returns the option picked. :raw-html:`<br />`





Interactables
-------------

OpenColorPicker
~~~~~~~~~~~~~~~

.. code-block:: luau  

   ExtraUIElements.OpenColorPicker(callback:function, cancelcallback:function, confirmcallback:function) -> nil

Opens a new window with a color picker. :raw-html:`<br />`
``callback`` Gets called when the color changes in the color picker. :raw-html:`<br />`
``cancelcallback`` When the user picks a color". :raw-html:`<br />`
``confirmcallback`` When the user canceles and closes the color picker. :raw-html:`<br />`


CreateSlider
~~~~~~~~~~~~

.. code-block:: luau  

   ExtraUIElements.CreateSlider(Parent:instance, Position:udim2, Size:udim2, MinValue:number, MaxValue:number, callback:function) -> nil

Creates a Slider with a Min and Max value. :raw-html:`<br />`
``Parent`` The Parent of the slider. :raw-html:`<br />`
``Position`` The position of the slider. :raw-html:`<br />`
``Size`` The size of the slider. :raw-html:`<br />`
``MinValue`` The minimum value that the slider can go to. :raw-html:`<br />`
``MaxValue`` The maximum value that the slider can go to. :raw-html:`<br />`
``callback`` The function that gets called when the slider value changes :raw-html:`<br />`



CreateCheckBox
~~~~~~~~~~~~~~

.. code-block:: luau  

   ExtraUIElements.CreateCheckBox(BoxParent:instances, Position:udim2, Size:udim2, StartingState:bool, callback:function) -> nil

Creates a checkbox UI object. :raw-html:`<br />`
``BoxParent`` The Parent of the checkbox. :raw-html:`<br />`
``Position`` The position of the checkbox. :raw-html:`<br />`
``Size`` The size of the checkbox. :raw-html:`<br />`
``StartingState`` The state the checkbox starts. :raw-html:`<br />`
``callback`` The function that gets called when the checkbox state changes :raw-html:`<br />`



CreateCheckBoxWithText
~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: luau  

   ExtraUIElements.CreateCheckBoxWithText(BoxParent:instance, Text:string, TextFieldSize:udim2, Position:udim2, StartingState:bool, callback:function) -> nil

Creates a checkbox UI object with text on the left side. :raw-html:`<br />`
``BoxParent`` The Parent of the checkbox. :raw-html:`<br />`
``Text`` The text next to the checkbox. :raw-html:`<br />`
``TextFieldSize`` The size of the text. :raw-html:`<br />`
``Position`` The position of the checkbox. :raw-html:`<br />`
``Size`` The size of the checkbox. :raw-html:`<br />`
``StartingState`` The state the checkbox starts. :raw-html:`<br />`
``callback`` The function that gets called when the checkbox state changes :raw-html:`<br />`





Premade UI
----------

CreatePrefabUI
~~~~~~~~~~~~~~

.. code-block:: luau  

   ExtraUIElements.CreatePrefabUI(Parent:instance, Size:udim2, Position:udim2, UI:string) -> nil

Creates a premade UI. :raw-html:`<br />`
``Parent`` The Parent of the new UI object. :raw-html:`<br />`
``Size`` The size of the UI object. :raw-html:`<br />`
``Position`` The position of the UI object. :raw-html:`<br />`
``UI`` The name of the premade UI. :raw-html:`<br />`


.. note::
    These premade UIs are currently avalible: :raw-html:`<br />`
    ``PropertiesFrame``