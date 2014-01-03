.. _FOCUS:

*****************************
Focus: routing keyboard input
*****************************

To say a widget has focus means that keyboard input is currently directed to that widget.

* By focus traversal, we mean the sequence of widgets that will be visited as the user moves from widget to widget with the tab key. See below for the rules for this sequence.

* You can traverse backwards using shift-tab.

* The Entry and Text widgets are intended to accept keyboard input, and if an entry or text widget currently has the focus, any characters you type into it will be added to its text. The usual editing characters such as ← and → will have their usual effects.

* Because Text widgets can contain tab characters, you must use the special key sequence control-tab to move the focus past a text widget.

* Most of the other types of widgets will normally be visited by focus traversal, and when they have focus:

  + Button widgets can be “pressed” by pressing the spacebar.

  + Checkbutton widgets can be toggled between set and cleared states using the spacebar.

  + In Listbox widgets, the ↑ and ↓ keys scroll up or down one line; the PageUp and PageDown keys scroll by pages; and the spacebar selects the current line, or de-selects it if it was already selected.

  + You can set a Radiobutton widget by pressing the spacebar.

  + Horizontal Scale widgets respond to the ← and → keys, and vertical ones respond to ↑ and ↓.

  + In a Scrollbar widget, the PageUp and PageDown keys move the scrollbar by pageloads. The ↑ and ↓ keys will move vertical scrollbars by units, and the ← and → keys will move horizontal scrollbars by units. 

* Many widgets are provided with an outline called the focus highlight that shows the user which widget has the highlight. This is normally a thin black frame located just outside the widget's border (if any). For widgets that don't normally have a focus highlight (specifically, frames, labels, and menus), you can set the highlightthickness option to a nonzero value to make the focus highlight visible.

* You can also change the color of the focus highlight using the highlightcolor option.

* Widgets of class Frame, Label, and Menu are not normally visited by the focus. However, you can set their takefocus options to 1 to get them included in focus traversal. You can also take any widget out of focus traversal by setting its takefocus option to 0. 

The order in which the tab key traverses the widgets is:

* For widgets that are children of the same parent, focus goes in the same order the widgets were created.

* For parent widgets that contain other widgets (such as frames), focus visits the parent widget first (unless its takefocus option is 0), then it visits the child widgets, recursively, in the order they were created. 

To sum up: to set up the focus traversal order of your widgets, create them in that order. Remove widgets from the traversal order by setting their takefocus options to 0, and for those whose default takefocus option is 0, set it to 1 if you want to add them to the order.

The above describes the default functioning of input focus in Tkinter. There is another, completely different way to handle it—let the focus go wherever the mouse goes. Under Section 26, “Universal widget methods”, refer to the .tk_focusFollowsMouse() method.

You can also add, change or delete the way any key on the keyboard functions inside any widget by using event bindings. See Section 54, “Events” for the details. 
