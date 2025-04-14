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

GetOSDriveLetter
~~~~~~~~~~~~~~~~

.. code-block:: luau  

    FileSystem.GetOSDriveLetter() -> string

Returns the partition name where LimeOS is installed on.


GetPartitions
~~~~~~~~~~~~~~~~

.. code-block:: luau  

    FileSystem.GetPartitions() -> table

Returns a table of all partitions in LimeOS.


GetPartitionByIndex
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.GetPartitionByIndex(index:number) -> table or bool, string

Returns a partition based on an index number. :raw-html:`<br />`
``index`` The index number of a partition. (e.g., 2 will always get the 2nd partition) :raw-html:`<br />`


GetPartitionByName
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.GetPartitionByName(name:string) -> table or bool, string

Returns a partition based on a string name. :raw-html:`<br />`
``name`` The name of a partition. :raw-html:`<br />`


CheckPartitionSize
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.CheckPartitionSize(partition:string, Data:table) -> bool

Retuns ``true`` when there is still space on the partition for the provided data. :raw-html:`<br />`
``partition`` The name for the to be checked partition. :raw-html:`<br />`
``Data`` The partition data. :raw-html:`<br />`


CreatePartition
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.CreatePartition(name:string, PartitionSize:number, IsOSDrive:bool) -> table or bool, string

Creates a new partition table and returns it. :raw-html:`<br />`
``name`` The name of the new partition. :raw-html:`<br />`
``PartitionSize`` The partition size in MB for the new partition. :raw-html:`<br />`
``IsOSDrive`` A bool value, that marks if LimeOS is installed on that partition. :raw-html:`<br />`

.. warning::
    Do not enter any value for ``IsOSDrive`` :raw-html:`<br />`


DelPartition
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   FileSystem.DelPartition(partition:string) -> bool, string

Deletes a partition based on a string name. The function will return ``true`` if the deletion was successful :raw-html:`<br />`
``partition`` The name for the to be deleted partition. :raw-html:`<br />`