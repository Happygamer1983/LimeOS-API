==========
DesktopManager
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

This module manages the desktop. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 

.. warning::
    When creating your own DE your module needs to have all of these functions! :raw-html:`<br />`

Functions
---------

UnloadDesktop
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   DesktopEnvironment.UnloadDesktop() -> nil

Unloads the Desktop. :raw-html:`<br />`


LoadDesktop
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   DesktopEnvironment.LoadDesktop() -> nil

Loads the Desktop. :raw-html:`<br />`


CreateLink
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   DesktopEnvironment.CreateLink(Name:string, Type:string, FilePath:string, Icon:string) -> nil	

Creates a new Icon on the current users desktop. :raw-html:`<br />`
``Name`` The name of the desktop icon, this is also the text under the icon itself. :raw-html:`<br />`
``Type`` The type of the link, like: ``(dir, LEF, etc)``. :raw-html:`<br />`
``FilePath`` The path to the linked object, eg. a directory you want to open.. :raw-html:`<br />`
``Icon`` The icon ID of the desktop icon. :raw-html:`<br />`


ChangeTaskbarSize
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   DesktopEnvironment.ChangeTaskbarSize(NewSize:number) -> nil

Changes the taskbar hight/size :raw-html:`<br />`
``NewSize`` The new size in px of the taskbar. :raw-html:`<br />`


AddTaskbarTab
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   DesktopEnvironment.AddTaskbarTab(AppName:string, ProcID:string, AppIcon:string) -> nil

Adds a new tab to the taskbar :raw-html:`<br />`
``AppName`` The name of the app, gets displayed on the tab itself. :raw-html:`<br />`
``ProcID`` The process ID of the process. :raw-html:`<br />`
``AppIcon`` The icon ID of the process for the icon in the tab. :raw-html:`<br />`


RemoveTaskbarTab
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   DesktopEnvironment.RemoveTaskbarTab(ProcID:string) -> nil

Removes a tab from the taskbar :raw-html:`<br />`
``ProcID`` The process ID of the process. :raw-html:`<br />`

