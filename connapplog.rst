.. _CONNECTING:

************************************************
Connecting your application logic to the widgets
************************************************

The preceding sections talked about how to arrange and configure the widgets—the front panel of the application.

Next, we'll talk about how to connect up the widgets to the logic that carries out the actions that the user requests.

* To make your application respond to events such as mouse clicks or keyboard inputs, there are two methods:

  + Some controls such as buttons have a command attribute that lets you specify a procedure, called a handler, that will be called whenever the user clicks that control.

    The sequence of events for using a Button widget is very specific, though. The user must move the mouse pointer onto the widget with mouse button 1 up, then press mouse button 1, and then release mouse button 1 while still on the widget. No other sequence of events will “press” a Button widget.

  + There is a much more general mechanism that can let your application react to many more kinds of inputs: the press or release of any keyboard key or mouse button; movement of the mouse into, around, or out of a widget; and many other events. As with command handlers, in this mechanism you write handler procedures that will be called whenever certain types of events occur. This mechanism is discussed under Section 54, “Events”. 

* Many widgets require you to use control variables, special objects that connect widgets together and to your program, so that you can read and set properties of the widgets. Control variables will be discussed in the next section.
