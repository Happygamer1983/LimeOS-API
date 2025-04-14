==========
RegistryHandler
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

This module allows you to change the LimeOS registry. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />`

The LimeOS registry uses the same pathing system as the filesystem. (e.g. "System/FileExtensions")

This is the current LimeOS registry, you can get a more detailed view via the terminal.

.. code-block:: txt  

    System
    ├── FileExtensions
    │   ├── dmp
    │   ├── txt
    │   └── se
    ├── ShellPaths
    │   ├── %LocalUser%
    │   └── %System%
    ├── SystemConfig
    │   ├── LoginBackground
    │   └── LoginBackgroundColor
    ├── SystemSpecs
    │   ├── Resolution
    │   ├── CPU
    │   └── GPU
    ├── DesktopEnvironment
    │   ├── CustomDEEnabled
    │   ├── CustomDEInstalled
    │   └── DEName
    └── TerminalSettings
       └── CurrentPath
    Users


Key Functions
-------------

CreateKey
~~~~~~~~~

.. code-block:: luau  

   RegistryHandler.CreateKey(key:string, data:string) -> bool

Creates a new registry key. :raw-html:`<br />`
``key`` The registry key path. :raw-html:`<br />`
``┗━>`` The key name is everything past the last ``/``, so ``/System/NewRegKey`` would have a key name of ``NewRegKey``. :raw-html:`<br />`
``data`` The data for the registry key. :raw-html:`<br />`


DeleteKey
~~~~~~~~~

.. code-block:: luau  

   RegistryHandler.DeleteKey(key:string) -> bool

Deletes a registry key. :raw-html:`<br />`
``key`` The registry key path. :raw-html:`<br />`


SetKey
~~~~~~

.. code-block:: luau  

   RegistryHandler.SetKey(key:string, data:string) -> nil

Updates the data of a registry key to a new value. :raw-html:`<br />`
``key`` The registry key path. :raw-html:`<br />`
``data`` The new registry key data. :raw-html:`<br />`


GetKey
~~~~~~

.. code-block:: luau  

   RegistryHandler.GetKey(key:string) -> table

Returns a registry key. :raw-html:`<br />`
``key`` The registry key path. :raw-html:`<br />`



Config Functions
-------------

SaveRegistry
~~~~~~~~~~~~

.. code-block:: luau  

   RegistryHandler.SaveRegistry() -> nil

Saves the registry to a file.


LoadRegistry
~~~~~~~~~~~~

.. code-block:: luau  

   RegistryHandler.LoadRegistry() -> nil

Loads the registry from a file.


InitRegistry
~~~~~~~~~~~~

.. code-block:: luau  

   RegistryHandler.InitRegistry() -> nil

Sets up the registry.

