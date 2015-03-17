===============================
How to use ColossalFramework.UI
===============================

The ColossalFramework.UI is the UI that is used in the game and you can create your own UI components.

The UIView
==========
The UIView is a MonoBehaviour which is like the main class for the UI.
It's like the canvas component in the UnityUI this UIView has all UI elements in it.
So if you're adding a new UI element it will have to be added to the UIView.

.. code-block:: c#
    :linenos:

    UIView v = UIView.GetAView ();


Adding a UIComponent
====================
UI components have to be added to the UIView.
A UIComponent is a holder and base class for a UI element like a panel, button, text etc.
All these components extend from UIComponent. (See list of components below).

.. code-block:: c#
    :linenos:

    UIComponent uic = v.AddUIComponent (typeof(ExamplePanel));

ExamplePanel is the class of the custom panel we create.
This class would extend from a UIComponent lke UIPanel.

.. code-block:: c#
    :linenos:

    public class ExamplePanel : UIPanel {
    }


Setting up a component
======================
When you have created your 'custom' component you can set it up in the Start() method.
This is a default Monobehaviour method people who have used Unity should be familiar with this.

.. code-block:: c#
    :linenos:

    public override void Start () {
            this.backgroundSprite = "GenericPanel";
            this.color = new Color32(255,0,0,100);
            this.width = 100;
            this.height = 200;
    }

It's quite simple to understand what this does. It just creates a panel 100 wide and 200 high.
And then it sets the background sprite of the panel to "GenericPanel" and the color to red half transparent.

Now each component has different properties and you can pretty much customize everything.
See the list of components below for a bit of information about how to set up each component.


Adding more stuff (children)
============================
Now that you have a panel you probably want to add some stuff inside of it.
It's really easy to add more components inside the component.
You don't even have to create a new class for every component you create.
So inside the Start() method where you set up the component you can also add more like this:

.. code-block:: c#
    :linenos:

    UILabel l = this.AddUIComponent<UILabel> ();
    l.text = "I am a label";
    l.eventClick += FooBarClickHandler;

Again quite straight forward how this works and it shouldn't be that hard to fill in your panel with more components. The only thing that might confuse you is the eventClick += FooBarClickHandler. See the next paragraph for more info about that.


(Input) Events
==============
There are many components that have some sort of user input.
For example a button you can click on it and it has a hover state and active state and so on.
The behavior of this can easily be modified by appending to the event delegate.
As you saw in the example above we used l.eventClick += FooBarClickHandler;
The FooBarClickHandler is just a function you can add in your ExamplePanel class.
Each method has a different set of arguments for example a slider value change event has the UIComponent as first arg and a float with the value as second arg. If you're using VisualStudio1 or MonoDevelop you can easily generate the method and it will fill in all arguments needed.


List of components
==================
There are more components then these but these are the most commonly used ones.
information about components will be added soon!


UIPanel
~~~~~~~
A panel is just a window with a background image. You can add components to this like buttons and so on to fill in your panel.


Properties
**********
backgroundSprite (A string that represents a sprite) [TODO need a list of sprites]
* flip (?)
* atlas (?)
* autoLayout (This can be set to true to automatically layout components in the panel)
* autoLayoutDirection (A LayoutDirection for the autoLayout option)
* padding (A RectOffset to specify the space between the border of the panel and the content)
* autoLayoutPadding (,, but then for auto layout)
* autoFitChildrenHorizontally (This can be set to make all components fit horizontal)
* autoFitChildrenVertically (,, vectical)
* wrapLayout (This will force components in the panel to only render inside the panel)
* autoLayoutStart (?)
* useCenter (?)


UIScrollablePanel
~~~~~~~~~~~~~~~~~
Coming soon...


UIButton
~~~~~~~~
Coming soon...


UISprite
~~~~~~~~
The UISprite is used for displaying images/sprites.


Properties
**********

* spriteName (A string that represents a sprite) [TODO need a list of sprites]
* spriteInfo (?)
* color (The color for the sprite)
* pixelsToUnits (The amount of pixels there are in one unit (Unity units))
* size (A Vector2 with the width,height of the sprite)
* flip (?)
* invertFill (?)
* fillDirection (?)
* fillAmount (?)
* offset (A vector3 to set the offset vector for the sprite)
* baseIndex (?)


UITextComponent
~~~~~~~~~~~~~~~
Coming soon...


UILabel
~~~~~~~
Coming soon...


UISlider
~~~~~~~~
Coming soon...


List of sprites
~~~~~~~~~~~~~~~
These are not all the sprites but these have been tested and used.


Getting a list of all sprites
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
TODO: Method to get a list of all sprites.


Sprite list
~~~~~~~~~~~
* name (what it does)


Kudos to `permutation <http://www.reddit.com/user/permutation>`__ for this post on `reddit <http://www.reddit.com/r/CitiesSkylinesModding/comments/2ytrm1/tiny_code_snippet_how_to_use_colossalframeworkui/>`__.
