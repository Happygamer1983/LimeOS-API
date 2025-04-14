==========
SystemLogs
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

This module is for logging system events. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 


Functions
---------

Log
~~~

.. code-block:: luau  

   SystemLogs.Log(Info:string) -> string

Logs and action with a timestamp. :raw-html:`<br />`
``Info`` The info that you want to log. :raw-html:`<br />`


GetLogs
~~~~~~~

.. code-block:: luau  

   SystemLogs.GetLogs() -> table

Returns a copy of the log table.


LogDump
~~~~~~~

.. code-block:: luau  

   SystemLogs.LogDump() -> nil

Creates a dump file of all logs, can be found at ``/root/dmp``.

