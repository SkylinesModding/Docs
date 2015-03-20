===================
Reverse Engineering
===================
`Reverse engineering <http://en.wikipedia.org/wiki/Reverse_engineering>`__ is taking apart an object to see how it works in order to duplicate or enhance the object.
So in our case we will be taking apart the game source to create mods for it.
Here you can read how to do this properly and efficient.
There are of course other methods then the ones described here but this method will work fine for most.
If you only want to work with the API you don't really need any of these things.

Other mods
----------
The method described below also applies to other mods.
This means you can read the source code of other mods and learn from it.
It can also be used to check for malicious code.

The game source
---------------
It is possible to browse through the source code of the game.
This means you can read how the game is build, what all methods do, what classes there are and so on.
We have to thanks Pardox/CO for not obfuscating the code else this wouldn't be as easy as it is now.
Mods can still obfuscate their code but it's really not recommended to do so.
People will most likely report your mods as it can't really be trusted.
Even with obfuscation it's possible to read the code but it makes it a lot harder and a lot easier to put in malicious code.

Decompiling
-----------
To decompile the assembly and browse through it, you will need a ``.NET`` compiler.
There are many programs that can do this but for this guide we will be using ILSpy.
Some other good alternatives are `DotPeek <https://www.jetbrains.com/decompiler/>`__, `JustDecompile <http://www.telerik.com/products/decompiler.aspx>`__ or built in options in your IDE.

* `Download ILSpy here <http://ilspy.net/>`_ (Download binaries)
* Extract the ZIP somwhere on your hard drive (It doesn't have an installer)
* Open The program. (``ILSpy.exe`` for Windows)
* Load in the :doc:`needed assemblies </modding/Workflow/Assemblies>` (.dll) :menuselection:`File --> Open`

You can now browse through all the classes in the assembly.
And when you click on any of the classes they will open up and you can see all the code.
Remember that you can **search**!

Using the ModTools mod
----------------------
Thanks to `nlight <http://www.skylinesmodding.com/users/nlight/>`__ we now have a mod that can help with reverse engineering.
This mod has a scene explorer which allows you to examine all objects in the scene.
It doesn't just list the objects it also shows all the components, fields, properties and methods.
This will help you a lot with understanding how the game works and find the parts of the code you need.
It also has some other useful features like logging exceptions in the console so make sure to check it out!
`ModTools by nlight. <http://www.skylinesmodding.com/t/modtools-in-game-debugging/123>`__

More things to reverse engineer
-------------------------------
There are several other things in the game which can be useful or required for your mod.
For example the locale files, crp files and so on.
Check out the following pages to learn more about this.

.. toctree::
    :maxdepth: 3
    :titlesonly:

    Locale-Files
    CRP-Files

