==============
ConsoleManager
==============

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

This module is used by terminal commands. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 

.. note::
    These functions are only relevant to you when creating your own commands. :raw-html:`<br />`
    

Functions
---------

CheckLocalPath
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   ConsoleManager.CheckLocalPath(path:string) -> string

Handles path proccesing  which enables shotcuts like ``./`` or ``../``. :raw-html:`<br />`
And returns a real path. :raw-html:`<br />`


PrintTable
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   ConsoleManager.PrintTable(table:table/string) -> string

Either returns a formatted string based on the table or returns just the input if its not a table. :raw-html:`<br />`

