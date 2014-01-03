.. _CTRLVARIABLES:

************************************************
Control variables: the values behind the widgets
************************************************

A Tkinter control variable is a special object that acts like a regular Python variable in that it is a container for a value, such as a number or string.

One special quality of a control variable is that it can be shared by a number of different widgets, and the control variable can remember all the widgets that are currently sharing it. This means, in particular, that if your program stores a value ``v`` into a control variable ``c`` with its ``c.set(v)`` method, any widgets that are linked to that control variable are automatically updated on the screen.

Tkinter uses control variables for a number of important functions, for example:

* Checkbuttons use a control variable to hold the current state of the checkbutton (on or off).

* A single control variable is shared by a group of radiobuttons and can be used to tell which one of them is currently set. When the user clicks on one radiobutton in a group, the sharing of this control variable is the mechanism by which Tkinter groups radiobuttons so that when you set one, any other set radiobutton in the group is cleared.

* Control variables hold text string for several applications. Normally the text displayed in an Entry widget is linked to a control variable. In several other controls, it is possible to use a string-valued control variable to hold text such as the labels of checkbuttons and radiobuttons and the content of Label widgets.

  For example, you could link an ``Entry`` widget to a Label widget so that when the user changes the text in the entry and presses the Enter key, the label is automatically updated to show that same text. 

To get a control variable, use one of these class constructors, depending on what type of values you need to store in it::

    v = tk.DoubleVar()   # Holds a float; default value 0.0
    v = tk.IntVar()      # Holds an int; default value 0
    v = tk.StringVar()   # Holds a string; default value ''

All control variables have these two methods:

.. py:method:: get()

           Returns the current value of the variable. 

.. py:method:: set(value)

        Changes the current value of the variable. If any widget options are slaved to this variable, those widgets will be updated when the main loop next idles; see ``.update_idletasks()`` in Section 26, “Universal widget methods” for more information on controlling this update cycle. 

Here are some comments on how control variables are used with specific widgets:

``Button``

    You can set its textvariable to a ``StringVar.`` Anytime that variable is changed, the text on the button will be updated to display the new value. This is not necessary unless the button's text is actually going to change: use the text attribute if the button's label is static. 

``Checkbutton``

    Normally, you will set the widget's variable option to an IntVar, and that variable will be set to 1 when the checkbutton is turned on and to 0 when it is turned off. However, you can pick different values for those two states with the ``onvalue`` and ``offvalue`` options, respectively.

    You can even use a ``StringVar`` as the checkbutton's variable, and supply string values for the ``offvalue`` and ``onvalue.`` Here's an example
    
    ::

        self.spamVar = tk.StringVar()
        self.spamCB  = tk.Checkbutton(self, text='Spam?',
            variable=self.spamVar, onvalue='yes', offvalue='no')

    If this checkbutton is on, ``self.spamVar.get()`` will return the string ``'yes'``; if the checkbutton is off, that same call will return the string ``'no'``. Furthermore, your program can turn the checkbutton on by calling ``.set('yes').``

    You can also the textvariable option of a checkbutton to a StringVar. Then you can change the text label on that checkbutton using the .set() method on that variable. 

``Entry``

    Set its ``textvariable`` option to a ``StringVar.`` Use that variable's ``.get()`` method to retrieve the text currently displayed in the widget. You can also the variable's ``.set()`` method to change the text displayed in the widget. 
    
``Label``

    You can set its ``textvariable`` option to a ``StringVar``. Then any call to the variable's ``.set()`` method will change the text displayed on the label. This is not necessary if the label's text is static; use the text attribute for labels that don't change while the application is running. 

``Menubutton``

    If you want to be able to change the text displayed on the menu button, set its ``textvariable`` option to a ``StringVar`` and use that variable's ``.set()`` method to change the displayed text. 

``Radiobutton``

    The variable option must be set to a control variable, either an ``IntVar`` or a ``StringVar``. All the radiobuttons in a functional group must share the same control variable.

    Set the value option of each radiobutton in the group to a different value. Whenever the user sets a radiobutton, the variable will be set to the value option of that radiobutton, and all the other radiobuttons that share the group will be cleared.

    You might wonder, what state is a group of radiobuttons in when the control variable has never been set and the user has never clicked on them? Each control variable has a default value: 0 for an ``IntVar,`` 0.0 for a ``DoubleVar``, and '' for a ``StringVar``. If one of the radiobuttons has that value, that radiobutton will be set initially. If no radiobutton's value option matches the value of the variable, the radiobuttons will all appear to be cleared.

    If you want to change the text label on a radiobutton during the execution of your application, set its ``textvariable`` option to a ``StringVar``. Then your program can change the text label by passing the new label text to the variable's ``.set()`` method. 
    
``Scale``

    For a scale widget, set its variable option to a control variable of any class, and set its ``from_`` and to options to the limiting values for the opposite ends of the scale.

    For example, you could use an ``IntVar`` and set the scale's ``from_=0`` and ``to=100``. Then every user change to the widget would change the variable's value to some value between 0 and 100 inclusive.

    Your program can also move the slider by using the ``.set()`` method on the control variable. To continue the above example, ``.set(75)`` would move the slider to a position three-fourths of the way along its trough.

    To set up a ``Scale`` widget for float values, use a ``DoubleVar``.

    You can use a ``StringVar`` as the control variable of a ``Scale`` widget. You will still need to provide numeric ``from_`` and ``to`` values, but the numeric value of the widget will be converted to a string for storage in the ``StringVar``. Use the scale's digits option to control the precision of this conversion. 
