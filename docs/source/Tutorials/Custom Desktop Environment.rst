=================
Custom Desktop Environment
=================

.. role:: raw-html(raw)
    :format: html

Here you learn the basics of creating your own desktop environment. :raw-html:`<br />`
This page only gives you the things needed to make the DE work, you need to code the functions on your own.

Needed Functions
----------------

.. code-block:: luau 

    local DesktopEnvironment = {}

    function DesktopEnvironment.CreateLink(Name, Type, FilePath, Icon)	

    end

    function DesktopEnvironment.UnloadDesktop()

    end

    function DesktopEnvironment.LoadDesktop()

    end

    function DesktopEnvironment.ChangeTaskbarSize(NewSize)

    end

    function DesktopEnvironment.AddTaskbarTab(AppName, ProcID, AppIcon)

    end

    function DesktopEnvironment.RemoveTaskbarTab(ProcID)

    end

    return DesktopEnvironment

Your desktop environment needs to have these functions. :raw-html:`<br />`
When you are done coding your DE, save it as a ``.LEF`` inside this dir ``/root/de/`` with the name ``DE_Main``. :raw-html:`<br />`
After that you need to go to the settings and enable your DE. :raw-html:`<br />`