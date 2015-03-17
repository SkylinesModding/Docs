==============================================
Setting Up and Using Visual Studio for Modding
==============================================

Install Visual Studio 2013
==========================

If you don't own a copy of Visual Studio 2013, you can download `Visual Studio Community 2013 <https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx>`__ **for free**. Installing Visual Studio should be straightforward.


Create a new solution and project
=================================

1. Start Visual Studio
2. Click ``File → New → Project...`` or press Ctrl+Shift+N
3. Select the "Class Library" template for the "Visual C#" language (other .NET languages should work, but I haven't tried that)
4. Enter a name for your project
5. Choose any location you'd like for your project, but don't use the mod directory
6. Click OK to create the solution


Add references
==============

1. Right-click your project in the Solution Explorer and choose ``Add → Reference...``
2. Click the "Browse..." button at the bottom of the dialog
3. Navigate to ``[SteamLibrary]\SteamApps\common\Cities_Skylines\Cities_Data\Managed``, where [SteamLibrary] is the path where your Steam games are.
4. Select the assembly DLLs you want to use. A short overview over what does what:
    * ICities.dll: The official mod API. **Required**.
    * UnityEngine.dll: Unity engine base types. Pretty much required.
    * UnityEngine.UI.dll: Unity built-in UI. Optional.
    * ColossalManaged.dll: Custom Colossal UI (among other things), which can be used to place your own native-looking UI elements (as demonstrated earlier). Optional.
    * Assembly-CSharp.dll: Seems to contain most of the game logic classes. Optional.


Code
====

Create your base class implementing ICities.IUserMod as usual. Add as many classes in as many source files as you like. They will all be compiled to a single DLL.


Compile
=======

Press F6 to compile your mod. The compiled DLL will be placed in ``bin\Debug`` or ``bin\Release`` under the project folder, depending on the active configuration. You can switch configurations with the combo box in the toolbar.


Test
====

Create a directory for your mod in ``%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\`` and copy the compiled DLL to it. It should now be available in the Content Manager of Cities: Skylines.


Automate
========

To automatically copy the DLL to the mod directory after each build, follow these steps:
1. Right-click your project in the Solution Explorer and choose Properties
2. Select "Build Events" on the left hand side of the property sheet
3. Paste the following in the "Post-build event command line":

.. code-block:: batch

    mkdir "%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\$(SolutionName)"
    del "%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\$(SolutionName)\$(TargetFileName)"
    xcopy /y "$(TargetPath)" "%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\$(SolutionName)"


This assumes that your mod directory has the same name as your solution.
If it doesn't you can change $(SolutionName) to the directory of your mod.
4. To make the game reload your mod while running, change the last two lines in AssemblyInfo.cs (under "Properties" in the Solution Explorer) to read:

``[assembly: AssemblyVersion("1.0.*")]
//[assembly: AssemblyFileVersion("1.0.0.0")]``

Kudos to `reimarvin <http://www.reddit.com/user/reimarvin>`__ for this post on reddit.
Kudos to `walrus_pug <http://www.reddit.com/user/walrus_pug>`__ for the auto updating with the AssemblyVersion.
