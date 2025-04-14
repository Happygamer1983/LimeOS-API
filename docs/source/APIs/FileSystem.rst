==========
FileSystem
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

The FileSystem module is responsable for the filesystem in LimeOS. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 

The LimeOS filesytem uses 4 permissions. (``R = Read, W = Write, D = Delete, and A = Admin``) :raw-html:`<br />` 
These permissions need to be formatted correctly, multible permissions are separated by a hyphen (e.g. "R-W-D").
For single permissions, simply use the corresponding letter (e.g. "R" or "D")

The LimeOS folder structure looks like this.

.. code-block:: bash  

    root      
    ├── sys   : System files
    ├── bin   : Terminal commands
    ├── boot  : Boot files/options
    ├── dmp   : Crash dumps
    ├── init  : Programs which autostart
    ├── menu  : Custom start menu entries
    ├── etc   : Configuration files, etc.
    └── de    : Files for custom DEs
    users     
    └── app   : Application data


Partition Functions
-------------------

These functions handle everything partition related.
When an functions fails, most of them return 2 values a bool and a string, the string being an error message.

.. code-block:: luau  

    FileSystem.GetOSDriveLetter() -> string

Returns the partition name where LimeOS is installed on.
