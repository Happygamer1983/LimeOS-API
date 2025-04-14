==========
AccountManager
==========

.. role:: raw-html(raw)
    :format: html

Module Info
-----------

This module is responsable for user account managment. :raw-html:`<br />` 
This module is not built in, you need to use ``loadlib()`` to load it. :raw-html:`<br />` 


Functions
---------

GetCurrentUser
~~~~~~~~~~~~~~

.. code-block:: luau  

   AccountManager.GetCurrentUser() -> string

Returns the currently logged-in user



CreateAccount
~~~~~~~~~~~~~

.. code-block:: luau  

   AccountManager.CreateAccount(username:string, pin:number, permissions:string) -> nil

Creates a new user account :raw-html:`<br />`
``username`` The name of the new user account. :raw-html:`<br />`
``pin`` The PIN number for the account, can be left empty. :raw-html:`<br />`
``permissions`` The permissions that the user will have, see :ref:`how to use permissions <PermissionsInfo>`. :raw-html:`<br />`



DeleteAccount
~~~~~~~~~~~~~

.. code-block:: luau  

   AccountManager.DeleteAccount(username:string) -> nil

Deletes a user account. :raw-html:`<br />`
``username`` The name of the user account you want to delete. :raw-html:`<br />`



SetAccountPIN
~~~~~~~~~~~~~

.. code-block:: luau  

   AccountManager.SetAccountPIN(username:string oldpin:number, newpin:number) -> bool

Updates the PIN number on a user account. :raw-html:`<br />`
``username`` The name of the user account you want to change the PIN for. :raw-html:`<br />`
``oldpin`` The current PIN number of the user account. :raw-html:`<br />`
``newpin`` The new PIN number of the user account. :raw-html:`<br />`

