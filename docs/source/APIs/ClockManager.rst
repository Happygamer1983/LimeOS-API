==========
ClockManager
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

This module allows you to get/format time. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 


Functions
---------

ConvertTime
~~~~~~~~~~~

.. code-block:: luau  

   ClockManager.ConvertTime(Value:number, From:string, To:string) -> number

Converts the gives value from one format to another. :raw-html:`<br />`
``Value`` The value you want to convert. :raw-html:`<br />`
``From`` The current format the value is now. :raw-html:`<br />`
``To`` The format to which you want to convert. :raw-html:`<br />`

.. warning::
    If it cant find the ``From`` or ``To`` values it will return ``-1`` :raw-html:`<br />`

All avalible formats: :raw-html:`<br />`
``"second"``, :raw-html:`<br />`
``"minute"``, :raw-html:`<br />`
``"hour"``, :raw-html:`<br />`
``"day"``, :raw-html:`<br />`
``"week"``, :raw-html:`<br />`
``"month"``, :raw-html:`<br />`
``"year"``, :raw-html:`<br />`


CurrentTime
~~~~~~~~~~~

.. code-block:: luau  

   ClockManager.CurrentTime(FormatString:string) -> string

Returns a formatted version of the current time/date. :raw-html:`<br />`
``FormatString`` The string that the formatter uses, see `os.date <https://create.roblox.com/docs/reference/engine/libraries/os#date>`_. :raw-html:`<br />`
``┗━>`` If nothing is provided, it defaults to this format ``Hour:Minute`` (24 Hour time). :raw-html:`<br />`

Here are some formats, you can see more at `os.date <https://create.roblox.com/docs/reference/engine/libraries/os#date>`_: :raw-html:`<br />`
``"%Y" = Year``, :raw-html:`<br />`
``"%m" = Month``, :raw-html:`<br />`
``"%d" = Day``, :raw-html:`<br />`
``"%H" = Hour (24-hour clock)``, :raw-html:`<br />`
``"%I" = Hour (12-hour clock)``, :raw-html:`<br />`
``"%M" = Minute``, :raw-html:`<br />`
``"%S" = Second``, :raw-html:`<br />`
``"%p" = AM/PM``, :raw-html:`<br />`

