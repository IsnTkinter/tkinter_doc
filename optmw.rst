*********************
The OptionMenu widget
*********************

 The purpose of this widget is to offer a fixed set of choices to the user in a drop-down menu.

The illustrations above shows an OptionMenu in two states. The left-hand example shows the widget in its initial form. The right-hand example shows how it looks when the mouse has clicked on it and dragged down to the 'boat' choice.

To create a new OptionMenu widget as the child of a root window or frame named parent:

.. py:class:: OptionMenu(parent, variable, choice1, choice2, ...)

        This constructor returns the new OptionMenu widget. The variable is a StringVar instance (see Section 52, “Control variables: the values behind the widgets”) that is associated with the widget, and the remaining arguments are the choices to be displayed in the widget as strings.

        The illustration above was created with this code snippet
        
        .. code-block:: python

                optionList = ('train', 'plane', 'boat')
                self.v = tk.StringVar()
                self.v.set(optionList[0])
                self.om = tk.OptionMenu(self, self.v, \*optionList)


        To find out which choice is currently selected in an OptionMenu widget, the .get() method on the associated control variable will return that choice as a string. 
