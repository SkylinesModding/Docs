==========
Assemblies
==========
Below are the assemblies you might need when making your mod.
There might be some that aren't listed below but these are the ones for Cities: Skylines and Unity.

You can find these assemblies in your steamapps. (See :doc:`folder structure </general/Folder-Structure>`)
``[SteamLibrary]\SteamApps\common\Cities_Skylines``

Check out the :doc:`reverse engineering page </modding/Workflow/Reverse-Engineering>` for more information how these can be usefull.
You will also need to reference these when settup up your project to be able to use them.


ICities.dll
***********
This is the official :doc:`modding API </modding/Development/ICities-API>`.

ColossalManaged.dll
*******************
The custom Colossal UI and a lot other framework classes which are used in the game.
Things like: DataBinding, Globalization, HTTP, Importers, IO, Math, Packaging, Plugins, Security, Steamworks and Threading.

Assembly-CSharp.dll
*******************
This contains almost all of the gameplay related classes.
From the road system to citizens and from buildings to the chirper.
You will find most things in this assembly.

UnityEngine.dll
***************
The `Unity game engine <http://unity3d.com/>`__ which the game was built in.
Check out the `scripting reference <http://docs.unity3d.com/ScriptReference/>`__ on unity for more information.
Remember that this doesn't contain UnityEditor only everything in the UnityEngine namespace.

UnityEngine.UI.dll
******************
The built in `UI from Unity <http://unity3d.com/learn/tutorials/modules/beginner/ui>`__.
You can also use ColossalManaged to use the UI which the game uses.
It completely depends on your preference, in fact you can even use the `old GUI <http://docs.unity3d.com/ScriptReference/GUI.html>`__ from Unity but this is not recommended.
