=========
Debugging
=========

The game has a debug panel which you can add messages to.

Using the panel
===============
To open the panel press **F7** in game.
You can resize the panel and drag it around.
The panel also has a clear button, this will clear all the messages.

Reference the DLL
=================
To be able to use this method of logging you will have to add a reference to the **Assembly-CSharp DLL**.
If you're not sure how to do this see this guide for :doc:`Visual Studio <Setting-Up-Visual-Studio>` or for :doc:`MonoDevelop <Setting-Up-MonoDevelop>`.
And you'll also have to add this line at the top of your class to be able to use it.

.. code-block:: c#

    using ColossalFramework;

Logging
=======
To send a message to the debug panel you use this code.

.. code-block:: c#
    :linenos:

    DebugOutputPanel.AddMessage(ColossalFramework.Plugins.PluginManager.MessageType.Message, "Message");

you can easily create some static methods for logging.
It's also recommended to prefix you log message so that users know were the message came from.
For example: *"[TreeBrush] Some debug message.."*

Other logging methods
=====================
There are a few other logging methods that other people made.
Here is a list to some of them.

* `ChirpLogger <https://github.com/Enagan/ChirpLogger>`__
* *More will be added soon...*
