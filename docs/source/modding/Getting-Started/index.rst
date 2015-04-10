===============
Getting Started
===============
To create a mod you will have to write down c# source code.
The game is made in `Unity 5 <http://unity3d.com>`__ and this allows you to do almost anything you can do in Unity.
The source code you write for your mod will be compiled in to a DLL.
This DLL is your mod and this will also be placed on the workshop.

Compiling
~~~~~~~~~
The game comes with a compiler to compile the dll for your mod.
However, this compiler only compiles your mod when you use the :doc:`ICities API </modding/Development/ICities-API>`.
The API is currently very limited and you can't do very much with it.
Now the good news is that we also have access to all other classes.
This means you can access almost everything in the game but the only downside is that you can't use the in game compiler.
We have set up some guides to make it a lot easier to compile your mod within Visual Studio or MonoDevelop.

.. toctree::
    :maxdepth: 3
    :titlesonly:

    Setting-Up-Visual-Studio
    Setting-Up-MonoDevelop

Without an editor
~~~~~~~~~~~~~~~~~
If you are fine with just using the :doc:`API </modding/Development/ICities-API>` you don't have to use an editor.
You will still need a text editor like notepad or sublime text to write down your c# classes.

* Go to the mods folder in local appdata. (See :doc:`Folder Structure </general/Folder-Structure>`)
  ``%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\``
* Inside that folder create a sub folder for your mod with the name of your mod.
* Create a sub folder inside your mod folder with the name 'Source'.
* Inside the source folder create a c# file. (The name can be anything but it's recommended to use the name of your mod)
  C# files have a extension of ``.cs``!

Now you can start creating your mod the same way as you do with the other methods described above.

Starting a mod
~~~~~~~~~~~~~~

Namespace
---------
First of all you have to define a `namespace <https://msdn.microsoft.com/en-us/library/z2kcy19k.aspx>`__ for your mod.
All the classes you create should be wrapped inside this namespace.
The namespace should be the name of your mod or at least something very similar.
You can see the namespace as a container for all your code to organize things.

.. code-block:: c#
    :linenos:

    namespace UnlockAllMod {
        //Inside here you define your class or multiple classes.
    }

When using code from the API, Unity, other mods, the game or anything else you will have to let the compiler know about this.
For example to use the API you will be using the ICities namespace.
On the top of your classes above where you define your own namespace you specify all the namespaces you will be using.

.. code-block:: c#
    :linenos:

    using System;
    using ICities;
    using UnityEngine;
    //etc...


Mod information
---------------
If you look in the Content Manager you will see all mods have a name followed with a description.
You will have to define this in your mod else your mod wont be recognized by the game.
To set the name and the description you have to inherit the IUserMod interface from the ICities namespace.

.. code-block:: c#
    :linenos:

    public class MyModInfo : IUserMod {
        public string Name {
            get { return "My mod name"; }
        }

        public string Description {
            get { return "My mod description"; }
        }
    }

Multiple classes
----------------
To keep things organized you should work with multiple classes/files.
Most people prefer just having one class per file and this is the most common way to work.
This does not mean that your mod won't work if you put all your code in one class/file.
You can even create more folders inside your Source folders to keep things even more organized.

Example
-------
With the information given above you should now have something like this.
When you compile this the mod should be in the Content Manager.
However, we haven't really coded anything so the mod will just load in and do nothing.

**MyModInfo.cs**

.. code-block:: c#
    :linenos:

    using System;
    using ICities;

    namespace MyMod {
        public class MyModInfo : IUserMod {
            public string Name {
                get { return "My mod name"; }
            }

            public string Description {
                get { return "My mod description"; }
            }
        }
    }

Next step
~~~~~~~~~
Now that you can create a mod and compile it it's time to do something in the mod.
Visit the pages below to learn more what to do next and make your mod actually do something.

* :doc:`Workflow </modding/Workflow/index>` - Information how to improve your workflow like debugging etc.
* :doc:`Development </modding/Development/index>` - This is where you can learn how to make content for your mods.



