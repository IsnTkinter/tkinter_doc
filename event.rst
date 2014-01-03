.. _EVENTS:

*****************************
Events: responding to stimuli
*****************************

An event is something that happens to your application—for example, the user presses a key or clicks or drags the mouse—to which the application needs to react.

The widgets normally have a lot of built-in behaviors. For example, a button will react to a mouse click by calling its command callback. For another example, if you move the focus to an entry widget and press a letter, that letter gets added to the content of the widget.

However, the event binding capability of Tkinter allows you to add, change, or delete behaviors.

First, some definitions:

* An event is some occurrence that your application needs to know about.

* An event handler is a function in your application that gets called when an event occurs.

* We call it binding when your application sets up an event handler that gets called when an event happens to a widget.
    
Levels of binding
=================

You can bind a handler to an event at any of three levels:

1) Instance binding: You can bind an event to one specific widget. For example, you might bind the PageUp key in a canvas widget to a handler that makes the canvas scroll up one page. To bind an event of a widget, call the .bind() method on that widget (see Section 26, “Universal widget methods”).

   For example, suppose you have a canvas widget named self.canv and you want to draw an orange blob on the canvas whenever the user clicks the mouse button 2 (the middle button). To implement this behavior:

   ::

        self.canv.bind('<Button-2>', self.__drawOrangeBlob)

   The first argument is a sequence descriptor that tells Tkinter that whenever the middle mouse button goes down, it is to call the event handler named self.__drawOrangeBlob. (See Section 54.6, “Writing your handler: The Event class”, below, for an overview of how to write handlers such as .__drawOrangeBlob()). Note that you omit the parentheses after the handler name, so that Python will pass in a reference the handler instead of trying to call it right away.

2) Class binding: You can bind an event to all widgets of a class. For example, you might set up all Button widgets to respond to middle mouse button clicks by changing back and forth between English and Japanese labels. To bind an event to all widgets of a class, call the .bind_class() method on any widget (see Section 26, “Universal widget methods”, above).

   For example, suppose you have several canvases, and you want to set up mouse button 2 to draw an orange blob in any of them. Rather than having to call .bind() for every one of them, you can set them all up with one call something like this:

   ::

        self.bind_class('Canvas', '<Button-2>',
                           self.__drawOrangeBlob)

3) Application binding: You can set up a binding so that a certain event calls a handler no matter what widget has the focus or is under the mouse. For example, you might bind the PrintScrn key to all the widgets of an application, so that it prints the screen no matter what widget gets that key. To bind an event at the application level, call the .bind_all() method on any widget (see Section 26, “Universal widget methods”).

   Here's how you might bind the PrintScrn key, whose “key name” is 'Print':

   ::
  
        self.bind_all('<Key-Print>', self.__printScreen)

Event sequences
===============

Tkinter has a powerful and general method for allowing you to define exactly which events, both specific and general, you want to bind to handlers.

In general, an event sequence is a string containing one or more event patterns. Each event pattern describes one thing that can happen. If there is more than one event pattern in a sequence, the handler will be called only when all the patterns happen in that same sequence.

The general form of an event pattern is:


        ``<[modifier-]...type[-detail]>``

* The entire pattern is enclosed inside <…>.

* The event type describes the general kind of event, such as a key press or mouse click. See Section 54.3, “Event types”.

* You can add optional modifier items before the type to specify combinations such as the shift or control keys being depressed during other key presses or mouse clicks. Section 54.4, “Event modifiers”

* You can add optional detail items to describe what key or mouse button you're looking for. For mouse buttons, this is 1 for button 1, 2 for button 2, or 3 for button 3.

  + The usual setup has button 1 on the left and button 3 on the right, but left-handers can swap these positions.

  + For keys on the keyboard, this is either the key's character (for single-character keys like the A or * key) or the key's name; see Section 54.5, “Key names” for a list of all key names. 

Here are some examples to give you the flavor of event patterns:

``<Button-1>`` 	The user pressed the first mouse button.

``<KeyPress-H>`` 	The user pressed the H key.

``<Control-Shift-KeyPress-H>`` 	The user pressed control-shift-H.

Event types
===========

The full set of event types is rather large, but a lot of them are not commonly used. Here are most of the ones you'll need:

.. list-table::
   :header-rows: 1
   :widths: 10 10 80
   
   * - Type
     - Name
     - Description
   * - 36
     - ``Activate`` 
     - A widget is changing from being inactive to being active. This refers to changes in the state option of a widget such as a button changing from inactive (grayed out) to active.
   * - 4
     - ``Button`` 
     - The user pressed one of the mouse buttons. The detail part specifies which button. For mouse wheel support under Linux, use Button-4 (scroll up) and Button-5 (scroll down). Under Linux, your handler for mouse wheel bindings will distinguish between scroll-up and scroll-down by examining the .num field of the Event instance; see Section 54.6, “Writing your handler: The Event class”.
   * - 5
     - ``ButtonRelease`` 
     - The user let up on a mouse button. This is probably a better choice in most cases than the Button event, because if the user accidentally presses the button, they can move the mouse off the widget to avoid setting off the event.
   * - 22
     - ``Configure`` 
     - The user changed the size of a widget, for example by dragging a corner or side of the window.
   * - 37
     - ``Deactivate`` 
     - A widget is changing from being active to being inactive. This refers to changes in the state option of a widget such as a radiobutton changing from active to inactive (grayed out).
   * - 17
     - ``Destroy`` 
     - A widget is being destroyed.
   * - 7
     - ``Enter`` 
     - The user moved the mouse pointer into a visible part of a widget. (This is different than the enter key, which is a KeyPress event for a key whose name is actually 'return'.)
   * - 12
     - ``Expose`` 
     - This event occurs whenever at least some part of your application or widget becomes visible after having been covered up by another window.
   * - 9
     - ``FocusIn`` 
     - A widget got the input focus (see Section 53, “Focus: routing keyboard input” for a general introduction to input focus.) This can happen either in response to a user event (like using the tab key to move focus between widgets) or programmatically (for example, your program calls the .focus_set() on a widget).
   * - 10
     - ``FocusOut`` 
     - The input focus was moved out of a widget. As with FocusIn, the user can cause this event, or your program can cause it.
   * - 2
     - ``KeyPress`` 
     - The user pressed a key on the keyboard. The detail part specifies which key. This keyword may be abbreviated Key.
   * - 3
     - ``KeyRelease`` 
     - The user let up on a key.
   * - 8
     - ``Leave`` 
     - The user moved the mouse pointer out of a widget.
   * - 19
     - ``Map`` 
     - A widget is being mapped, that is, made visible in the application. This will happen, for example, when you call the widget's .grid() method.
   * - 6
     - ``Motion`` 
     - The user moved the mouse pointer entirely within a widget.
   * - 38
     - ``MouseWheel`` 
     - The user moved the mouse wheel up or down. At present, this binding works on Windows and MacOS, but not under Linux. For Windows and MacOS, see the discussion of the .delta field of the Event instance in Section 54.6, “Writing your handler: The Event class”. For Linux, see the note above under Button.
   * - 18
     - ``Unmap`` 
     - A widget is being unmapped and is no longer visible. This happens, for example, when you use the widget's .grid_remove() method.
   * - 15
     - ``Visibility`` 
     - Happens when at least some part of the application window becomes visible on the screen.

Event modifiers
===============

The modifier names that you can use in event sequences include:

* ``Alt`` : True when the user is holding the alt key down.

* ``Any`` : This modifier generalizes an event type. For example, the event pattern '<Any-KeyPress>' applies to the pressing of any key.

* ``Control`` : True when the user is holding the control key down.

* ``Double`` : Specifies two events happening close together in time. For example, <Double-Button-1> describes two presses of button 1 in rapid succession.

* ``Lock`` : True when the user has pressed shift lock.

* ``Shift`` : True when the user is holding down the shift key.

* ``Triple`` : Like Double, but specifies three events in rapid succession.

You can use shorter forms of the events. Here are some examples:

    ``'<1>'`` is the same as ``'<Button-1>'``.

    ``'x'`` is the same as ``'<KeyPress-x>'``. 

Note that you can leave out the enclosing ``'<…>'`` for most single-character keypresses, but you can't do that for the space character (whose name is ``'<space>'``) or the less-than (``<``) character (whose name is ``'<less>'``).

Key names
=========

The detail part of an event pattern for a KeyPress or KeyRelease event specifies which key you're binding. (See the Any modifier, above, if you want to get all keypresses or key releases).

The table below shows several different ways to name keys. See Section 54.6, “Writing your handler: The Event class”, below, for more information on Event objects, whose attributes will describe keys in these same ways.

* The .keysym column shows the “key symbol”, a string name for the key. This corresponds to the .keysym attribute of the Event object.

* The .keycode column is the “key code.” This identifies which key was pressed, but the code does not reflect the state of various modifiers like the shift and control keys and the NumLock key. So, for example, both a and A have the same key code.

* The .keysym_num column shows a numeric code equivalent to the key symbol. Unlike .keycode, these codes are different for different modifiers. For example, the digit 2 on the numeric keypad (key symbol KP_2) and the down arrow on the numeric keypad (key symbol KP_Down) have the same key code (88), but different .keysym_num values (65433 and 65458, respectively).

* The “Key” column shows the text you will usually find on the physical key, such as tab. 

There are many more key names for international character sets. This table shows only the “Latin-1” set for the usual USA-type 101-key keyboard. For the currently supported set, see the manual page for Tk keysym values.

.. list-table::
   :widths: 15 10 10 65
   :header-rows: 1

   * - ``.keysym``
     - `.keycode`
     - `.keysym_num`
     - Key
   * - ``Alt_L``
     - `64`
     - `65513`
     - The left-hand alt key
   * - ``Alt_R``
     - `113`
     - `65514`
     - The right-hand alt key
   * - ``BackSpace``
     - `22`
     - `65288`
     - backspace
   * - ``Cancel``
     - `110`
     - `65387`
     - break
   * - ``Caps_Lock``
     - `66`
     - `65549`
     - CapsLock
   * - ``Control_L``
     - `37`
     - `65507`
     - The left-hand control key
   * - ``Control_R``
     - `109`
     - `65508`
     - The right-hand control key
   * - ``Delete``
     - `107`
     - `65535`
     - Delete
   * - ``Down``
     - `104`
     - `65364`
     - ↓
   * - ``End``
     - `103`
     - `65367`
     - end
   * - ``Escape``
     - `9`
     - `65307`
     - esc
   * - ``Execute``
     - `111`
     - `65378`
     - SysReq
   * - ``F1``
     - `67`
     - `65470`
     - Function key F1
   * - ``F2``
     - `68`
     - `65471`
     - Function key F2
   * - ``Fi``
     - `66+i`
     - `65469+i`
     - Function key Fi
   * - ``F12``
     - `96`
     - `65481`
     - Function key F12
   * - ``Home``
     - `97`
     - `65360`
     - home
   * - ``Insert``
     - `106`
     - `65379`
     - insert
   * - ``Left``
     - `100`
     - `65361`
     - ←
   * - ``Linefeed``
     - `54`
     - `106`
     - Linefeed (control-J)
   * - ``KP_0``
     - `90`
     - `65438`
     - 0 on the keypad
   * - ``KP_1``
     - `87`
     - `65436`
     - 1 on the keypad
   * - ``KP_2``
     - `88`
     - `65433`
     - 2 on the keypad
   * - ``KP_3``
     - `89`
     - `65435`
     - 3 on the keypad
   * - ``KP_4``
     - `83`
     - `65430`
     - 4 on the keypad
   * - ``KP_5``
     - `84`
     - `65437`
     - 5 on the keypad
   * - ``KP_6``
     - `85`
     - `65432`
     - 6 on the keypad
   * - ``KP_7``
     - `79`
     - `65429`
     - 7 on the keypad
   * - ``KP_8``
     - `80`
     - `65431`
     - 8 on the keypad
   * - ``KP_9``
     - `81`
     - `65434`
     - 9 on the keypad
   * - ``KP_Add``
     - `86`
     - `65451`
     - \+ on the keypad
   * - ``KP_Begin``
     - `84`
     - `65437`
     - The center key (same key as 5) on the keypad
   * - ``KP_Decimal``
     - `91`
     - `65439`
     - Decimal (.) on the keypad
   * - ``KP_Delete``
     - `91`
     - `65439`
     - delete on the keypad
   * - ``KP_Divide``
     - `112`
     - `65455`
     - / on the keypad
   * - ``KP_Down``
     - `88`
     - `65433`
     - ↓ on the keypad
   * - ``KP_End``
     - `87`
     - `65436`
     - end on the keypad
   * - ``KP_Enter``
     - `108`
     - `65421`
     - enter on the keypad
   * - ``KP_Home``
     - `79`
     - `65429`
     - home on the keypad
   * - ``KP_Insert``
     - `90`
     - `65438`
     - insert on the keypad
   * - ``KP_Left``
     - `83`
     - `65430`
     - ← on the keypad
   * - ``KP_Multiply``
     - `63`
     - `65450`
     - × on the keypad
   * - ``KP_Next``
     - `89`
     - `65435`
     - PageDown on the keypad
   * - ``KP_Prior``
     - `81`
     - `65434`
     - PageUp on the keypad
   * - ``KP_Right``
     - `85`
     - `65432`
     - → on the keypad
   * - ``KP_Subtract``
     - `82`
     - `65453`
     - \- on the keypad
   * - ``KP_Up``
     - `80`
     - `65431`
     - ↑ on the keypad
   * - ``Next``
     - `105`
     - `65366`
     - PageDown
   * - ``Num_Lock``
     - `77`
     - `65407`
     - NumLock
   * - ``Pause``
     - `110`
     - `65299`
     - pause
   * - ``Print``
     - `111`
     - `65377`
     - PrintScrn
   * - ``Prior``
     - `99`
     - `65365`
     - PageUp
   * - ``Return``
     - `36`
     - `65293`
     - The enter key (control-M). The name Enter refers to a mouse-related event, not a keypress; see Section 54, “Events”
   * - ``Right``
     - `102`
     - `65363`
     - →
   * - ``Scroll_Lock``
     - `78`
     - `65300`
     - ScrollLock
   * - ``Shift_L``
     - `50`
     - `65505`
     - The left-hand shift key
   * - ``Shift_R``
     - `62`
     - `65506`
     - The right-hand shift key
   * - ``Tab``
     - `23`
     - `65289`
     - The tab key
   * - ``Up``
     - `98`
     - `65362`
     - ↑

Writing your handler: The Event class
=====================================

The sections above tell you how to describe what events you want to handle, and how to bind them. Now let us turn to the writing of the handler that will be called when the event actually happens.

The handler will be passed an Event object that describes what happened. The handler can be either a function or a method. Here is the calling sequence for a regular function:

.. code-block:: python

        def handlerName(event):


And as a method:

.. code-block:: python

        def handlerName(self, event):

The attributes of the Event object passed to the handler are described below. Some of these attributes are always set, but some are set only for certain types of events.

.. list-table::
   :widths: 15 85
   :header-rows: 0

   * - ``.char`` 
     - If the event was related to a KeyPress or KeyRelease for a key that produces a regular ASCII character, this string will be set to that character. (For special keys like delete, see the .keysym attribute, below.)
   * - ``.delta`` 
     - For MouseWheel events, this attribute contains an integer whose sign is positive to scroll up, negative to scroll down. Under Windows, this value will be a multiple of 120; for example, 120 means scroll up one step, and -240 means scroll down two steps. Under MacOS, it will be a multiple of 1, so 1 means scroll up one step, and -2 means scroll down two steps. For Linux mouse wheel support, see the note on the Button event binding in Section 54.3, “Event types”.
   * - ``.height`` 
     - If the event was a Configure, this attribute is set to the widget's new height in pixels.
   * - ``.keycode`` 
     - For KeyPress or KeyRelease events, this attribute is set to a numeric code that identifies the key. However, it does not identify which of the characters on that key were produced, so that “x” and “X” have the same .keyCode value. For the possible values of this field, see Section 54.5, “Key names”.
   * - ``.keysym`` 
     - For KeyPress or KeyRelease events involving a special key, this attribute is set to the key's string name, e.g., 'Prior' for the PageUp key. See Section 54.5, “Key names” for a complete list of .keysym names.
   * - ``.keysym_num`` 
     - For KeyPress or KeyRelease events, this is set to a numeric version of the .keysym field. For regular keys that produce a single character, this field is set to the integer value of the key's ASCII code. For special keys, refer to Section 54.5, “Key names”.
   * - ``.num`` 
     - If the event was related to a mouse button, this attribute is set to the button number (1, 2, or 3). For mouse wheel support under Linux, bind Button-4 and Button-5 events; when the mouse wheel is scrolled up, this field will be 4, or 5 when scrolled down.
   * - ``.serial`` 
     - An integer serial number that is incremented every time the server processes a client request. You can use .serial values to find the exact time sequence of events: those with lower values happened sooner.
   * - ``.state`` 
     - An integer describing the state of all the modifier keys. See the table of modifier masks below for the interpretation of this value.
   * - ``.time`` 
     - This attribute is set to an integer which has no absolute meaning, but is incremented every millisecond. This allows your application to determine, for example, the length of time between two mouse clicks.
   * - ``.type`` 
     - A numeric code describing the type of event. For the interpretation of this code, see Section 54.3, “Event types”.
   * - ``.widget`` 
     - Always set to the widget that caused the event. For example, if the event was a mouse click that happened on a canvas, this attribute will be the actual Canvas widget.
   * - ``.width`` 
     - If the event was a Configure, this attribute is set to the widget's new width in pixels.
   * - ``.x`` 
     - The x coordinate of the mouse at the time of the event, relative to the upper left corner of the widget.
   * - ``.y`` 
     - The y coordinate of the mouse at the time of the event, relative to the upper left corner of the widget.
   * - ``.x_root`` 
     - The x coordinate of the mouse at the time of the event, relative to the upper left corner of the screen.
   * - ``.y_root`` 
     - The y coordinate of the mouse at the time of the event, relative to the upper left corner of the screen.


Use these masks to test the bits of the .state value to see what modifier keys and buttons were pressed during the event:

.. list-table::
   :widths: 10 30
   :header-rows: 1

   * - Mask
     - Modifier
   * - `0x0001` 
     - Shift.
   * - `0x0002` 
     - Caps Lock.
   * - `0x0004` 
     - Control.
   * - `0x0008` 
     - Left-hand Alt.
   * - `0x0010` 
     - Num Lock.
   * - `0x0080` 
     - Right-hand Alt.
   * - `0x0100` 
     - Mouse button 1.
   * - `0x0200` 
     - Mouse button 2.
   * - `0x0400` 
     - Mouse button 3.

Here's an example of an event handler. Under Section 54.1, “Levels of binding”, above, there is an example showing how to bind mouse button 2 clicks on a canvas named self.canv to a handler called self.__drawOrangeBlob(). Here is that handler:

.. code-block:: python

    def __drawOrangeBlob(self, event):
        '''Draws an orange blob in self.canv where the mouse is.
        '''
        r = 5   # Blob radius
        self.canv.create_oval(event.x-r, event.y-r,
            event.x+r, event.y+r, fill='orange')

When this handler is called, the current mouse position is (event.x, event.y). The .create_oval() method draws a circle whose bounding box is square and centered on that position and has sides of length 2*r.

The extra arguments trick
=========================

Sometimes you would like to pass other arguments to a handler besides the event.

Here is an example. Suppose your application has an array of ten checkbuttons whose widgets are stored in a list self.cbList, indexed by the checkbutton number in range(10).

Suppose further that you want to write one handler named .__cbHandler for <Button-1> events in all ten of these checkbuttons. The handler can get the actual Checkbutton widget that triggered it by referring to the .widget attribute of the Event object that gets passed in, but how does it find out that checkbutton's index in self.cbList?

It would be nice to write our handler with an extra argument for the checkbutton number, something like this:

.. code-block:: python

    def __cbHandler(self, event, cbNumber):

But event handlers are passed only one argument, the event. So we can't use the function above because of a mismatch in the number of arguments.

Fortunately, Python's ability to provide default values for function arguments gives us a way out. Have a look at this code:

.. code-block:: python

    def __createWidgets(self):
        #...
        self.cbList = []    # Create the checkbutton list
        for i in range(10):
            cb = tk.Checkbutton(self, ...)
            self.cbList.append(cb)
            cb.grid(row=1, column=i)
            def handler(event, self=self, i=i):   1
                return self.__cbHandler(event, i)
            cb.bind('<Button-1>', handler)
        #...
    def __cbHandler(self, event, cbNumber):
        #...

These lines define a new function handler that expects three arguments. The first argument is the Event object passed to all event handlers, and the second and third arguments will be set to their default values—the extra arguments we need to pass it.

This technique can be extended to supply any number of additional arguments to handlers. 

Virtual events
==============

You can create your own new kinds of events called virtual events. You can give them any name you want so long as it is enclosed in double pairs of <<…>>.
For example, suppose you want to create a new event called <<panic>>, that is triggered either by mouse button 3 or by the pause key. To create this event, call this method on any widget w::

    w.event_add('<<panic>>', '<Button-3>',
                  '<KeyPress-Pause>')

You can then use '<<panic>>' in any event sequence. For example, if you use this call::

    w.bind('<<panic>>', h)

any mouse button 3 or pause keypress in widget w will trigger the handler h.

See .event_add(), .event_delete(), and .event_info() under Section 26, “Universal widget methods” for more information about creating and managing virtual events.
