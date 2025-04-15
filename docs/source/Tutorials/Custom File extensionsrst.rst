=================
Custom File Extensions
=================

.. role:: raw-html(raw)
    :format: html

Here you can learn how to add your own file extensions

Adding Extension
----------------

Extensions are saved in the Registry, so to add your own you need to create a key in the Registry.
If you want to use your own app, save your app as a .LEF file.

.. code-block:: luau 

    local RegistryHandler = loadlib("RegistryHandler")
    local Extension = "Your extension here" -- Change this to the extension you want to make
    local App = "Builtin App or file path" -- If you want to open a builtin app change this to the name of the app.
    -- If you want to use your own app set it to the path to your app file

    RegistryHandler.CreateKey("System/FileExtensions/"..Extension, App)

And thats it, now you should have a working file extension!
If you need more help or have questions, join our `Discord <https://discord.gg/DmxuDXrThg>`_!