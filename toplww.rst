**********************************
Toplevel: Top-level window methods
**********************************

 A top-level window is a window that has an independent existence under the window manager. It is decorated with the window manager's decorations, and can be moved and resized independently. Your application can use any number of top-level windows.

For any widget w, you can get to its top-level widget using w.winfo_toplevel().

To create a new top-level window:

    w = tk.Toplevel(option, ...)

Options include:

Table 34. Toplevel window methods
bg or background 	The background color of the window. See Section 5.3, “Colors”.
bd or borderwidth 	Border width in pixels; default is 0. For possible values, see Section 5.1, “Dimensions”. See also the relief option, below.
class_ 	You can give a Toplevel window a “class” name. Such names are matched against the option database, so your application can pick up the user's configuration preferences (such as colors) by class name. For example, you might design a series of pop-ups called “screamers,” and set them all up with class_='Screamer'. Then you can put a line in your option database like this:

*Screamer*background: red

and then, if you use the .option_readfile() method to read your option database, all widgets with that class name will default to a red background. This option is named class_ because class is a reserved word in Python.
cursor 	The cursor that appears when the mouse is in this window. See Section 5.8, “Cursors”.
height 	Window height; see Section 5.1, “Dimensions”.
highlightbackground	The color of the focus highlight when the window does not have focus. See Section 53, “Focus: routing keyboard input”.
highlightcolor 	The color of the focus highlight when the window has the focus.
highlightthickness 	The thickness of the focus highlight. Default is 1. Set highlightthickness=0 to suppress display of the focus highlight.
menu	To provide this window with a top-level menubar, supply a Menu widget as the value of this option. Under MacOS, this menu will appear at the top of the screen when the window is active. Under Windows or Unix, it will appear at the top of the application.
padx	Use this option to provide extra space on the left and right sides of the window. The value is a number of pixels.
pady	Use this option to provide extra space on the top and bottom sides of the window. The value is a number of pixels.
relief 	Normally, a top-level window will have no 3-d borders around it. To get a shaded border, set the bd option larger that its default value of zero, and set the relief option to one of the constants discussed under Section 5.6, “Relief styles”.
takefocus	Normally, a top-level window does not get focus. Use takefocus=True if you want it to be able to take focus; see Section 53, “Focus: routing keyboard input”.
width 	The desired width of the window; see Section 5.1, “Dimensions”.

These methods are available for top-level windows:

.aspect(nmin, dmin, nmax, dmax)

    Constrain the root window's width:length ratio to the range [ nmin / dmin, nmax / dmax ]. 
.deiconify()

    If this window is iconified, expand it. 
.geometry(newGeometry=None)

    Set the window geometry. For the form of the argument, see Section 5.10, “Geometry strings”. If the argument is omitted, the current geometry string is returned. 
.iconify()

    Iconify the window. 
.lift(aboveThis=None)

    To raise this window to the top of the stacking order in the window manager, call this method with no arguments. You can also raise it to a position in the stacking order just above another Toplevel window by passing that window as an argument. 
.lower(belowThis=None)

    If the argument is omitted, moves the window to the bottom of the stacking order in the window manager. You can also move the window to a position just under some other top-level window by passing that Toplevel widget as an argument. 
.maxsize(width=None, height=None)

    Set the maximum window size. If the arguments are omitted, returns the current (width, height). 
.minsize(width=None, height=None)

    Set the minimum window size. If the arguments are omitted, returns the current minima as a 2-tuple. 
.overrideredirect(flag=None)

    If called with a True argument, this method sets the override redirect flag, which removes all window manager decorations from the window, so that it cannot be moved, resized, iconified, or closed. If called with a False argument, window manager decorations are restored and the override redirect flag is cleared. If called with no argument, it returns the current state of the override redirect flag.

    Be sure to call the .update_idletasks() method (see Section 26, “Universal widget methods”) before setting this flag. If you call it before entering the main loop, your window will be disabled before it ever appears.

    This method may not work on some Unix and MacOS platforms. 
.resizable(width=None, height=None)

    If is true, allow horizontal resizing. If height is true, allow vertical resizing. If the arguments are omitted, returns the current size as a 2-tuple. 
.state(newstate=None)

    Returns the window's current state, one of:

        'normal': Displayed normally.

        'iconic': Iconified with the .iconify() method.

        'withdrawn': Hidden; see the .withdraw() method below. 

    To change the window's state, pass one of the strings above as an argument to the method. For example, to iconify a Toplevel instance T, use “T.state('iconify') ”. 
.title(text=None)

    Set the window title. If the argument is omitted, returns the current title. 
.transient(parent=None)

    Make this window a transient window for some parent window; the default parent window is this window's parent.

    This method is useful for short-lived pop-up dialog windows. A transient window always appears in front of its parent. If the parent window is iconified, the transient is iconified as well. 
.withdraw()

    Hides the window. Restore it with .deiconify() or .iconify().
    
