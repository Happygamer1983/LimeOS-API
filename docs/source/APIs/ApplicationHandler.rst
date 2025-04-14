==========
ApplicationHandler
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

This module handles everything related to applications. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 


Functions
---------

GetProcesses
~~~~~~~~~~~~

.. code-block:: luau  

   ApplicationManager.GetProcesses() -> nil

Returns all open processes.


ExecuteLEF
~~~~~~~~~~

.. code-block:: luau  

   ApplicationManager.ExecuteLEF(lefdata:string) -> nil

Executes LEF files.
``lefdata`` The LEF file data. :raw-html:`<br />`


UpdateProcess
~~~~~~~~~~~~~

.. code-block:: luau  

   ApplicationManager.UpdateProcess(processid:string, toupdate:string, data:string) -> nil

Updates a property of a process to a new value. :raw-html:`<br />`
``processid`` The process ID of the process that you want to update. :raw-html:`<br />`
``toupdate`` The property you want to update. :raw-html:`<br />`
``data`` The new value for the property. :raw-html:`<br />`


StartProcess
~~~~~~~~~~~~

.. code-block:: luau  

   ApplicationManager.StartProcess(processname:string, processdata:table) -> instance

Starts a new process and returns the newly created app.
``processname`` The name for your new process, use the :doc:`Built-in` when you are creating new process. :raw-html:`<br />`
``processdata`` The process ID of the process that you want to update. :raw-html:`<br />`


ExitProcess
~~~~~~~~~~~

.. code-block:: luau  

   ApplicationManager.ExitProcess(processid:string) -> nil

Closes a process. :raw-html:`<br />`
``processid`` The process ID of the process that you want to close. :raw-html:`<br />`


CloseAllProcesses
~~~~~~~~~~~~~~~~~

.. code-block:: luau  

   ApplicationManager.CloseAllProcesses() -> nil

Closes all processes. :raw-html:`<br />`

