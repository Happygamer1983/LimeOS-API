==========
Kernel
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

This module is the base of LimeOS. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 

.. warning::
    Most of the Kernel functions can or will crash the system, be carefull when using them. :raw-html:`<br />`


Memory Functions
----------------

MemAlloc
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   Kernel.MemAlloc(memamount:number) -> nil

Allowcates a specified amount of memory. :raw-html:`<br />`
``memamount`` The amount of memory you want to allowcate in bytes. :raw-html:`<br />`


MemDealloc
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   Kernel.MemDealloc(memamount:number) -> nil

Deallocates a specified amount of memory. :raw-html:`<br />`
``memamount`` The amount of memory you want to deallocate in bytes. :raw-html:`<br />`


MemUpdate
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   Kernel.MemUpdate(applicationdata:table) -> nil

Recalculates and updates the required amount of memory for a provided application. :raw-html:`<br />`
``applicationdata`` The info table for an application. :raw-html:`<br />`


ReturnMem
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   Kernel.ReturnMem(returnmax:bool) -> number

Returns the amount of system memory or the used amount of memory. :raw-html:`<br />`
``returnmax`` The toggle value for what it returns. :raw-html:`<br />`
``┗━>`` If ``true`` is provided, it returns the amount of memory the system has. :raw-html:`<br />`
``┗━>`` If nothing or ``false`` is provided, it returns the amount of used system memory. :raw-html:`<br />`


MemCalc
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   Kernel.MemCalc(application:instance) -> number

Calculates the amount of memory required for a specified app. :raw-html:`<br />`
``application`` The application you want to calculate the memory for :raw-html:`<br />`





System Functions
----------------

SystemStart
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   Kernel.SystemStart() -> nil

Starts the system and loads everything required.


SystemShutdown
~~~~~~~~~~~~~~~~

.. code-block:: luau  

 Kernel.SystemShutdown(systemrestart:bool) -> nil 

Shuts down or Reboots the system, also saves the file system. :raw-html:`<br />`
``systemrestart`` The toggle value for if it restarts. :raw-html:`<br />`
``┗━>`` If ``true`` is provided, it will reboot the system. :raw-html:`<br />`
``┗━>`` If nothing or ``false`` is provided, it shuts down and kicks the player. :raw-html:`<br />`





Debug Functions
----------------

KernelPanic
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   Kernel.KernelPanic(errorcode:string) -> nil

Crashes the system and creates a dump file. :raw-html:`<br />`
``errorcode`` The error code you see in the crash screen :raw-html:`<br />`
Dump files can be found in ``/root/dmp/``

