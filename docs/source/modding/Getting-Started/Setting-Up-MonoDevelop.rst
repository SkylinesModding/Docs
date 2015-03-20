======================
Setting Up MonoDevelop
======================

Install MonoDevelop
===================
If you don't own a copy of MonoDevelop, you can download `MonoDevelop <http://www.monodevelop.com/download/>`__ **for free**. Installing MonoDevelop should be straightforward.


Setup a new project/solution
============================

1. Start MonoDevelop and create a new "solution".
2. Put the source wherever you want except for the actual modding-directory the Modding API wiki suggests. You don't want the game to compile the source files.
3. Make it a C# Library, we don't need it to be executable.

Let's assume your project is called FooBar.
You should get a solution with a ``MyClass.cs`` file with a tiny bit of code (namespace FooBar and a public class).


Set references
==============

1. In Solution, right click ``References - Edit References``. (If you don't see a "Solution" panel on the left side, go to View - Pads - Solution.)
2. I don't know if you can use the default System library, but just in case I remove it from "Selected references".
3. In the tab .NET Assembly, navigate to your Steam library folder, and then to ``SteamLibrary\SteamApps\common\Cities_Skylines\Cities_Data\Managed``
4. Select the :doc:`assembly DLL(s) </modding/Workflow/Assemblies>` you want to use.


Test autocompletion
===================
You should now be able to write a simple class like ...

.. code-block:: c#

    public class myLoader : LoadingExtensionBase {
    }

... and have the program autocomplete the LoadingExtensionBase keyword. Inside, you can then hit ``Alt+Insert`` to generate stubs for the interface. And inside those methods, you should be able to access the classes from ColossalManaged.dll and Assembly-CSharp.dll. For example, you should be able to use DebugOutputPanel.AddMessage() (which writes to the ingame Debug Console).


Compiling
=========

1. You can hit F7 to build your solution (or go to ``Build - Build FooBar``). This should generate warning/error messages if you make a mistake, etc.
2. By default, the project should be set to the "Debug" configuration (see Project - Active Configuration). Thus, F7 creates a directory ``bin\Debug\`` (relative to your project file) and fills it with the necessary .dll-files and your Mod's .dll.
3. Now you need to copy that .dll to the appropriate folder (see `wiki <http://www.skylineswiki.com/Modding_API#Overview>`__) in its own sub-folder (e.g. ``"..\Addons\Mods\FooBar\FooBar.dll"``).


Testing the Mod
===============

1. Start the game
2. Hit F7 to open the Debug Console. It should tell you that it didn't find the source for FooBar, but it should still be selectable in Content Manager - Mods. (Ignore the error it's harmless)


Automate
========
This will copy dll to Mods folder and then delete it before the next build so the new dll can be copied.

1. Go to Project - FooBar Options
2. Go to Build - Custom Commands, select Debug as configuration
3. From the drop down, add "**After Build**"

* Command:

.. code-block:: batch

   xcopy /Y "bin\${ProjectConfigName}\${SolutionName}.dll" "%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons Mods\${SolutionName}\"

* Working Directory: ``${ProjectDir}``
* Check "Run on external console" (you can check Pause, too, to debug)

4. From the drop down, add "**Before Build**"

* Command:

.. code-block:: batch

   cmd /c "IF EXIST '%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\${SolutionName}\${SolutionName}.dll' (del '%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\${SolutionName}\${SolutionName}.dll')"

* Working Directory: ``${ProjectDir}``
* check "Run on external console" (you can check Pause, too, to debug)


It should look similar to `this <http://i.imgur.com/QxBuZJw.png>`__.
Now whenever you build this project, MonoDevelop deletes your old .dll (IF it exists), then after the build is complete the new .dll is copied via xcopy.

Kudos to `permutation <http://www.reddit.com/user/permutation>`__ for this post on reddit.
