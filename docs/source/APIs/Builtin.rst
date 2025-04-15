=================
Builtin Functions
=================

.. role:: raw-html(raw)
    :format: html

These functions are Built into the Script Editor so you dont need ``loadlib()`` to load them.


LimeOS Functions
-----------

loadlib
~~~~~~~~~~~~~~~~

.. code-block:: luau

  loadlib(name: string) -> table

This loads modules so you can acces their functions, you can see the avalible modules in the side bar. :raw-html:`<br />`
``name`` The name of the module you want to load. :raw-html:`<br />`


Lime.CreateWindow
~~~~~~~~~~~~~~~~

.. code-block:: luau  

  Lime.CreateWindow(name: string, icon: number) -> instance

Creates and returns a new application window. :raw-html:`<br />`
``name`` A string representing the name of the application. :raw-html:`<br />`
``icon`` An optional number representing the icon ID for the application. If omitted, the window will be created without an icon. :raw-html:`<br />`


Lime.CreateUI
~~~~~~~~~~~~~~~~

.. code-block:: luau  

  Lime.CreateUI(parent: instance, name: string) -> instance

Creates and returns a new UI object, placing it inside the specified parent instance. :raw-html:`<br />`
``parent`` The instance in which the UI object will be placed. :raw-html:`<br />`
``name`` A string representing the type of UI element to create (e.g., "TextLabel"). :raw-html:`<br />`


Lime.GetService
~~~~~~~~~~~~~~~~

.. code-block:: luau  

  Lime.GetService(name: string) -> table

Returns a Roblox service by its name. :raw-html:`<br />`
``name`` A string representing the name of the Roblox service to retrieve. :raw-html:`<br />`


Lime.Encryption
~~~~~~~~~~~~~~~~

.. code-block:: luau  

  Lime.Encryption(ModuleVersion: string) -> table

Returns an encryption module and its functions. :raw-html:`<br />`
``ModuleVersion`` (Optional) A string specifying which encryption module to return. :raw-html:`<br />`
``├──`` If "AES" is provided, it returns the AES encryption module (work in progress). :raw-html:`<br />`
``└──`` If nothing is provided, it returns the standard LimeOS encryption module. :raw-html:`<br />`
    ``├──`` ``.Encrypt(Data:string)`` This encrypts the provided input and retuns it. :raw-html:`<br />`
    ``└──`` ``.Decrypt(Data:string)`` This decrypts the provided input and retuns it. :raw-html:`<br />`




Roblox Functions
-----------

print
~~~~~~~~~~~~~~~~

.. code-block:: luau

  print() -> nil

Prints output to the Script Editor console.


log
~~~~~~~~~~~~~~~~

.. code-block:: luau

  log() -> nil

Logs output to the Roblox console.

