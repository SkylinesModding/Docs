==============
Best Practices
==============
This is a list of best practises.
Some of these are very important as they can break people their game!
Check this page fruequently for new things.

Consistant Assembly Versioning
~~~~~~~~~~~~~~
The game keeps strict version references, so if you update the assembly version of your mod, old references will break, corrupting the savegame.
So, **always use the same assembly version**!
See `this reddit post <http://www.reddit.com/r/CitiesSkylinesModding/comments/2zeiwx/how_i_broke_everyones_savegame_and_fixed_them/>`__ for more information about this issue.

Spaceless Assembly Names
~~~~~~~~~~~~~~~~~
Assembly names should not contain spaces.
Assemblies with a space in the name do not serialize properly, thus removing the mod will break serialized objects.


If you have anything else please :doc:`contribute </contributing>` to this page or post it on the `forums <http://www.skylinesmodding.com/c/modding>`__!
