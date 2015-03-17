================
Folder Structure
================

The main directory you will need for modding is located in local app appdata.
This is where you create all your modifications to the game.

* **On Windows** ``%LOCALAPPDATA%\Colossal Order\Cities_Skylines``
* **On Mac** ``/Users/<username>/Library/Application Support/Colossal Order/Cities_Skylines``
* **On Linux** ``/home/<username>/.local/share/Colossal Order/Cities_Skylines``

The other directory you might need is located in your steamapps.
This directory contains all the DLL's for :doc:`modding <Modding>`, :doc:`output log <Output-Log>` and more.

.. This might be different for Mac/Linux.
* **On Windows** ``[SteamLibrary]\SteamApps\common\Cities_Skylines``
* **On Mac** ``[SteamLibrary]/SteamApps/common/Cities_Skylines``
* **On Linux** ``[SteamLibrary]/SteamApps/common/Cities_Skylines``

Structure AppData
=================
* Root
* Addons
    * **Assets** - Assets saved from the :doc:`Asset Editor <Asset-Editor>` are stored here
    * **ColorCorrections** - Custom :doc:`color corrections <Color-Corrections>` look-up tables can be placed in this folder
    * **Import** - All the assets (textures, models) to import custom assets in the :doc:`Asset Editor <Asset-Editor>` are placed here
    * MapEditor
        * **Brushes** - Custom made brush textures can be placed here
        * **Heightmaps** - Heightmaps to import are placed in this folder, exported heightmaps from the :doc:`Map Editor <Map-Editor>` also will appear in this folder
    * **Mods** - Base folder for user made code modifications
* **Maps** - Maps saved from the :doc:`Map Editor <Map-Editor>` are stored here
* **Saves** - Save games are stored here
* **Snapshots**\* - Snapshots taken from the :doc:`Map Editor <Map-Editor>` and the :doc:`Asset Editor <Asset-Editor>` are stored in subfolders named after their unique id
* **WorkshopStagingArea**\*\* - Steam Workshop content is shown in subfolders here before being uploaded

\* - *These folders are never automatically cleaned up, that means the more snapshots a user take, the more images and subfolders there will be. It is convenient when working for a long time with multiple maps to preserve older snapshots to be reused. The folder can be deleted manually with no side effects for the game if needs arise.*

\*\* - *These folders exist only during the time they are needed.*

Additionally, the game may use an additional "Temp" folder if needed. The folder is created under Addons and does not require any human interactions.

Structure SteamApps
===================
*Only the directories you need are listed*

* Root
* **Cities Skylines Soundtrack** - If you have bought the Deluxe version of the game this is were you can find the bonus soundtracks.
* Cites_Data - The :doc:`output_log.txt <Output-Log>` is stored here which might contain errors from your mod
    * **Managed** - All the DLL's you need are listed here. See :doc:`setting up your environment <Setting-Up-Your-Environment>` for more info about these.
* **Locale** - The locale files for all supported languages.
* Files - All the external files the game uses including some default mods and locale files.
    * **Mods** - Three default mods (HardMode, UnlimitedMoney, UnlockAll) and a template mod (NewMod) as reference.

This folder also contains the Digital Artbook and Momunmental Buildings PDF.


Files
=========
Cities: Skylines uses an in-house Colossal Raw Asset Package (.crp) file format to store various data. Those packages are containers and can encapsulate any data type, so a .crp file can be a save, a map, a color correction or an asset. The game will output packages in their respective designated place so it is safe to assume a Savegame produced by the game will always be written to the Saves folder.
For assets importing, standard image formats such as png, jpg, bmp, tga, dds, raw, r8, r16, and tiff are supported, but depending on the tool you are using those with, only a subset may be available. Please refer to the tool documentation for more details. For geometry/models/meshes, the FBX file format is the only one officially supported.
