========================
Setting Up Visual Studio
========================

Install Visual Studio 2013
==========================
If you don't own a copy of Visual Studio 2013, you can download `Visual Studio Community 2013 <https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx>`__ **for free**. Installing Visual Studio should be straightforward.


Create a new solution and project
=================================

1. Start Visual Studio
2. Click :menuselection:`File --> New --> Project…` or press :kbd:`Ctrl+Shift+N`
3. Select the :guilabel:`Class Library` template for the :guilabel:`Visual C#` language (other .NET languages should work, but I haven't tried that)
4. Enter a name for your project
5. Choose any location you'd like for your project, but don't use the mod directory
6. Click :guilabel:`OK` to create the solution


Add references
==============

1. Right-click your project in the Solution Explorer and choose :menuselection:`Add --> Reference…`
2. Click the :guilabel:`Browse…` button at the bottom of the dialog
3. Navigate to ``[SteamLibrary]\SteamApps\common\Cities_Skylines\Cities_Data\Managed``, where ``[SteamLibrary]`` is the path where your Steam games are.
4. Select the :doc:`assembly DLL(s) </modding/Workflow/Assemblies>` you want to use.

Code
====
Create your base class implementing ``ICities.IUserMod`` as usual. Add as many classes in as many source files as you like. They will all be compiled to a single DLL.

Compile
=======
Press :kbd:`F6` to compile your mod. The Output Type in your project's Properties should be set to Class Library. The compiled DLL will be placed in ``obj\Debug`` or ``obj\Release`` under the project folder, depending on the active configuration. You can switch configurations with the combo box in the toolbar.

Test
====
Create a directory for your mod in ``%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\`` and copy the compiled DLL to it. It should now be available in the Content Manager of Cities: Skylines.

Automate
========
To automatically copy the DLL to the mod directory after each build, follow these steps:

1. Right-click your project in the :guilabel:`Solution Explorer` and choose :guilabel:`Properties`
2. Select :guilabel:`Build Events` on the left hand side of the property sheet
3. Paste the following in the :guilabel:`Post-build event command line`:

    .. code-block:: batch

        mkdir "%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\$(SolutionName)"
        del "%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\$(SolutionName)\$(TargetFileName)"
        xcopy /y "$(TargetPath)" "%LOCALAPPDATA%\Colossal Order\Cities_Skylines\Addons\Mods\$(SolutionName)"

    This assumes that your mod directory has the same name as your solution.
    If it doesn't you can change ``$(SolutionName)`` to the directory of your mod.

    Optionally, you can automate the launching of the game (to save those precious seconds of clicking in steam):

    .. code-block:: batch

        "%STEAMDIRECTORY%\Steam.exe" -applaunch 255710

4. To make the game reload your mod while running, change the last two lines in AssemblyInfo.cs (under :guilabel:`Properties` in the :guilabel:`Solution Explorer`) to read:

    .. code-block:: c#

        [assembly: AssemblyVersion("1.0.*")]
        //[assembly: AssemblyFileVersion("1.0.0.0")]
    
    If you get a build error about the asterix (*) and deterministic builds, you'll need to manualy set the "Determinism" property in your <SolutionName>.csproj file to false as     .. code-block: c#
        <Deterministic>false</Deterministic> 
        //<Deterministic>true</Deterministic>
        
    'Description of determinism <https://blog.paranoidcoding.com/2016/04/05/deterministic-builds-in-roslyn.html>'
    Source 'John Deer <https://stackoverflow.com/questions/53782085/visual-studio-assemblyversion-with-dont-work>'
    'Why determinism is on by default <https://developercommunity.visualstudio.com/t/new-solutions-are-deterministic/348650>

Kudos to `reimarvin <http://www.reddit.com/user/reimarvin>`__ for this post on reddit.

Kudos to `walrus_pug <http://www.reddit.com/user/walrus_pug>`__ for the auto updating with the ``AssemblyVersion``.
