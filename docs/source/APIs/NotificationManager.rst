==========
NotificationManager
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

With this module you can send Notifications and create Popups. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 


Functions
---------

SendNotification
~~~~~~~~~~~~~~~~

.. code-block:: luau  

   NotificationManager.SendNotification(title:string, body:string) -> nil

Sends a side notification with a Title and body :raw-html:`<br />`
``title`` The title of the notification. :raw-html:`<br />`
``body`` The body of the notification. :raw-html:`<br />`


PopUp
~~~~~

.. code-block:: luau  

   NotificationManager.PopUp(Title:string, Prompt:string, AnswerType:number, MsgType:number, callback:function) -> nil

Creates a popup with diffrent options :raw-html:`<br />`
``title`` The title of the popup, located in the topbar of the popup. :raw-html:`<br />`
``body`` The body of the popup. :raw-html:`<br />`
``AnswerType`` The answer options of the popup. :raw-html:`<br />`
    ``├──`` ``1`` is a Yes/No answer option. :raw-html:`<br />`
    ``└──`` ``2`` is a OK answer option. :raw-html:`<br />`
``MsgType`` What type of popup. :raw-html:`<br />`
    ``├──`` ``1`` is a Info popup. :raw-html:`<br />`
    ``├──`` ``2`` is a Warning popup. :raw-html:`<br />`
    ``└──`` ``3`` is an Error popup, the popup text is also the color red. :raw-html:`<br />`
``callback`` A function that gets called if a Yes has been clicked on a Yes/No popup. :raw-html:`<br />`

