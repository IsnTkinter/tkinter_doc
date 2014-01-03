************************
Universal widget methods
************************

 The methods are defined below on all widgets. In the descriptions, w can be any widget of any type.

w.after(delay_ms, callback=None, *args)

    Requests Tkinter to call function callback with arguments args after a delay of at least delay_ms milliseconds. There is no upper limit to how long it will actually take, but your callback won't be called sooner than you request, and it will be called only once.

    This method returns an integer “after identifier” that can be passed to the .after_cancel() method if you want to cancel the callback.

    If you do not pass a callback argument, this method waits delay_ms milliseconds, as in the .sleep() function of the standard Python time module. 
w.after_cancel(id)

    Cancels a request for callback set up earlier .after(). The id argument is the result returned by the original .after() call. 
w.after_idle(func, *args)

    Requests that Tkinter call function func with arguments args next time the system is idle, that is, next time there are no events to be processed. The callback will be called only once. If you want your callback to be called again, you must call the .after_idle method again. 
w.bell()

    Makes a noise, usually a beep. 
w.bind(sequence=None, func=None, add=None)

    This method is used to attach an event binding to a widget. See Section 54, “Events” for the overview of event bindings.

    The sequence argument describes what event we expect, and the func argument is a function to be called when that event happens to the widget. If there was already a binding for that event for this widget, normally the old callback is replaced with func, but you can preserve both callbacks by passing add='+'. 
w.bind_all(sequence=None, func=None, add=None)

    Like .bind(), but applies to all widgets in the entire application. 
w.bind_class(className, sequence=None, func=None, add=None)

    Like .bind(), but applies to all widgets named className (e.g., 'Button'). 
w.bindtags(tagList=None)

    If you call this method, it will return the “binding tags” for the widget as a sequence of strings. A binding tag is the name of a window (starting with '.') or the name of a class (e.g., 'Listbox').

    You can change the order in which binding levels are called by passing as an argument the sequence of binding tags you want the widget to use.

    See Section 54, “Events” for a discussion of binding levels and their relationship to tags. 
w.cget(option)

    Returns the current value of option as a string. You can also get the value of an option for widget w as w[option]. 
w.clipboard_append(text)

    Appends the given text string to the display's clipboard, where cut and pasted strings are stored for all that display's applications. 
w.clipboard_clear()

    Clears the display's clipboard (see .clipboard_append() above). 
w.column_configure()

    See Section 4.2, “Other grid management methods”. 
w.config(option=value, ...)

    Same as .configure(). 
w.configure(option=value, ...)

    Set the values of one or more options. For the options whose names are Python reserved words (class, from, in), use a trailing underbar: 'class_', 'from_', 'in_'.

    You can also set the value of an option for widget w with the statement

        w[option] = value

    If you call the .config() method on a widget with no arguments, you'll get a dictionary of all the widget's current options. The keys are the option names (including aliases like bd for borderwidth). The value for each key is:

        for most entries, a five-tuple: (option name, option database key, option database class, default value, current value); or,

        for alias names (like 'fg'), a two-tuple: (alias name, equivalent standard name). 

w.destroy()

    Calling w.destroy() on a widget w destroys w and all its children. 
w.event_add(virtual, *sequences)

    This method creates a virtual event whose name is given by the virtual string argument. Each additional argument describes one sequence, that is, the description of a physical event. When that event occurs, the new virtual event is triggered.

    See Section 54, “Events” for a general description of virtual events. 
w.event_delete(virtual, *sequences)

    Deletes physical events from the virtual event whose name is given by the string virtual. If all the physical events are removed from a given virtual event, that virtual event won't happen anymore. 
w.event_generate(sequence, **kw)

    This method causes an event to trigger without any external stimulus. The handling of the event is the same as if it had been triggered by an external stimulus. The sequence argument describes the event to be triggered. You can set values for selected fields in the Event object by providing keyword=value arguments, where the keyword specifies the name of a field in the Event object.

    See Section 54, “Events” for a full discussion of events. 
w.event_info(virtual=None)

    If you call this method without an argument, you'll get back a sequence of all the currently defined virtual event names.

    To retrieve the physical events associated with a virtual event, pass this method the name of the virtual event and you will get back a sequence of the physical sequence names, or None if the given virtual event has never been defined. 
w.focus_displayof()

    Returns the name of the window that currently has input focus on the same display as the widget. If no such window has input focus, returns None.

    See Section 53, “Focus: routing keyboard input” for a general description of input focus. 
w.focus_force()

    Force the input focus to the widget. This is impolite. It's better to wait for the window manager to give you the focus. See also .grab_set_global() below. 
w.focus_get()

    Returns the widget that has focus in this application, if any—otherwise returns None. 
w.focus_lastfor()

    This method retrieves the name of the widget that last had the input focus in the top-level window that contains w. If none of this top-level's widgets have ever had input focus, it returns the name of the top-level widget. If this application doesn't have the input focus, .focus_lastfor() will return the name of the widget that will get the focus next time it comes back to this application. 
w.focus_set()

    If w's application has the input focus, the focus will jump to w. If w's application doesn't have focus, Tk will remember to give it to w next the application gets focus. 
w.grab_current()

    If there is a grab in force for w's display, return its identifier, otherwise return None. Refer to Section 54, “Events” for a discussion of grabs. 
w.grab_release()

    If w has a grab in force, release it. 
w.grab_set()

    Widget w grabs all events for w's application. If there was another grab in force, it goes away. See Section 54, “Events” for a discussion of grabs. 
w.grab_set_global()

    Widget w grabs all events for the entire screen. This is considered impolite and should be used only in great need. Any other grab in force goes away. Try to use this awesome power only for the forces of good, and never for the forces of evil, okay? 
w.grab_status()

    If there is a local grab in force (set by .grab_set()), this method returns the string 'local'. If there is a global grab in force (from .grab_set_global()), it returns 'global'. If no grab is in force, it returns None. 
w.grid_forget()

    See Section 4.2, “Other grid management methods”. 
w.grid_propagate()

    See Section 4.2, “Other grid management methods”. 
w.grid_remove()

    See Section 4.2, “Other grid management methods”. 
w.image_names()

    Returns the names of all the images in w's application as a sequence of strings. 
w.keys()

    Returns the option names for the widget as a sequence of strings. 
w.lift(aboveThis=None)

    If the argument is None, the window containing w is moved to the top of the window stacking order. To move the window just above some Toplevel window w, pass w as an argument. 
w.lower(belowThis=None)

    If the argument is None, the window containing w is moved to the bottom of the window stacking order. To move the window just below some Toplevel window w, pass w as an argument. 
w.mainloop()

    This method must be called, generally after all the static widgets are created, to start processing events. You can leave the main loop with the .quit() method (below). You can also call this method inside an event handler to resume the main loop. 
w.nametowidget(name)

    This method returns the actual widget whose path name is name. See Section 5.11, “Window names”. If the name is unknown, this method will raise KeyError. 
w.option_add(pattern, value, priority=None)

    This method adds default option values to the Tkinter option database. The pattern is a string that specifies a default value for options of one or more widgets. The priority values are one of:
    20 	For global default properties of widgets.
    40 	For default properties of specific applications.
    60 	For options that come from user files such as their .Xdefaults file.
    80 	For options that are set after the application starts up. This is the default priority level.

    Higher-level priorities take precedence over lower-level ones. See Section 27, “Standardizing appearance” for an overview of the option database. The syntax of the pattern argument to .option_add() is the same as the option-pattern part of the resource specification line.

    For example, to get the effect of this resource specification line:

    *Button*font: times 24 bold

    your application (self in this example) might include these lines:

        self.bigFont = tkFont.Font(family='times', size=24,
                                     weight='bold')
        self.option_add('*Button*font', self.bigFont)

    Any Button widgets created after executing these lines would default to bold Times 24 font (unless overriden by a font option to the Button constructor). 
w.option_clear()

    This method removes all options from the Tkinter option database. This has the effect of going back to all the default values. 
w.option_get(name, classname)

    Use this method to retrieve the current value of an option from the Tkinter option database. The first argument is the instance key and the second argument is the class key. If there are any matches, it returns the value of the option that best matches. If there are no matches, it returns ''.

    Refer to Section 27, “Standardizing appearance” for more about how keys are matched with options. 
w.option_readfile(fileName, priority=None)

    As a convenience for user configuration, you can designate a named file where users can put their preferred options, using the same format as the .Xdefaults file. Then, when your application is initializing, you can pass that file's name to this method, and the options from that file will be added to the database. If the file doesn't exist, or its format is invalid, this method will raise tk.TclError.

    Refer to Section 27, “Standardizing appearance” for an introduction to the options database and the format of option files. 
w.register(function)

    This method creates a Tcl wrapper around a Python function, and returns the Tcl wrapper name as a string. For an example of the usage of this method, see Section 10.2, “Adding validation to an Entry widget”. 
w.quit()

    This method exits the main loop. See .mainloop(), above, for a discussion of main loops. 
w.rowconfigure()

    See Section 4.2, “Other grid management methods”. 
w.selection_clear()

    If w currently has a selection (such as a highlighted segment of text in an entry widget), clear that selection. 
w.selection_get()

    If w currently has a selection, this method returns the selected text. If there is no selection, it raises tk.TclError. 
w.selection_own()

    Make w the owner of the selection in w's display, stealing it from the previous owner, if any. 
w.selection_own_get()

    Returns the widget that currently owns the selection in w's display. Raises tk.TclError if there is no such selection. 
w.tk_focusFollowsMouse()

    Normally, the input focus cycles through a sequence of widgets determined by their hierarchy and creation order; see Section 53, “Focus: routing keyboard input”. You can, instead, tell Tkinter to force the focus to be wherever the mouse is; just call this method. There is no easy way to undo it, however. 
w.tk_focusNext()

    Returns the widget that follows w in the focus traversal sequence. Refer to Section 53, “Focus: routing keyboard input” for a discussion of focus traversal. 
w.tk_focusPrev()

    Returns the widget that precedes w in the focus traversal sequence. 
w.unbind(sequence, funcid=None)

    This method deletes bindings on w for the event described by sequence. If the second argument is a callback bound to that sequence, that callback is removed and the rest, if any, are left in place. If the second argument is omitted, all bindings are deleted.

    See Section 54, “Events”, below, for a general discussion of event bindings. 
w.unbind_all(sequence)

    Deletes all event bindings throughout the application for the event described by the given sequence. 
w.unbind_class(className, sequence)

    Like .unbind(), but applies to all widgets named className (e.g., 'Entry' or 'Listbox'). 
w.update()

    This method forces the updating of the display. It should be used only if you know what you're doing, since it can lead to unpredictable behavior or looping. It should never be called from an event callback or a function that is called from an event callback. 
w.update_idletasks()

    Some tasks in updating the display, such as resizing and redrawing widgets, are called idle tasks because they are usually deferred until the application has finished handling events and has gone back to the main loop to wait for new events.

    If you want to force the display to be updated before the application next idles, call the w.update_idletasks() method on any widget. 
w.wait_variable(v)

    Waits until the value of variable v is set, even if the value does not change. This method enters a local wait loop, so it does not block the rest of the application. 
w.wait_visibility(w)

    Wait until widget w (typically a Toplevel) is visible. 
w.wait_window(w)

    Wait until window w is destroyed. 
w.winfo_children()

    Returns a list of all w's children, in their stacking order from lowest (bottom) to highest (top). 
w.winfo_class()

    Returns w's class name (e.g., 'Button'). 
w.winfo_containing(rootX, rootY, displayof=0)

    This method is used to find the window that contains point (rootX, rootY). If the displayof option is false, the coordinates are relative to the application's root window; if true, the coordinates are treated as relative to the top-level window that contains w. If the specified point is in one of the application's top-level window, this method returns that window; otherwise it returns None. 
w.winfo_depth()

    Returns the number of bits per pixel in w's display. 
w.winfo_fpixels(number)

    For any dimension number (see Section 5.1, “Dimensions”), this method returns that distance in pixels on w's display, as a number of type float. 
w.winfo_geometry()

    Returns the geometry string describing the size and on-screen location of w. See Section 5.10, “Geometry strings”.
    Warning

    The geometry is not accurate until the application has updated its idle tasks. In particular, all geometries are initially '1x1+0+0' until the widgets and geometry manager have negotiated their sizes and positions. See the .update_idletasks() method, above, in this section to see how to insure that the widget's geometry is up to date.
w.winfo_height()

    Returns the current height of w in pixels. See the remarks on geometry updating under .winfo_geometry(), above. You may prefer to use .winfo_reqheight(), described below, which is always up to date. 
w.winfo_id()

    Returns an integer that uniquely identifies w within its top-level window. You will need this for the .winfo_pathname() method, below. 
w.winfo_ismapped()

    This method returns true if w is mapped, false otherwise. A widget is mapped if it has been gridded (or placed or packed, if you are using one of the other geometry managers) into its parent, and if its parent is mapped, and so on up to the top-level window. 
w.winfo_manager()

    If w has not been gridded (or placed via one of the other geometry managers), this method returns an empty string. If w has been gridded or otherwise placed, it returns a string naming the geometry manager for w: this value will be one of 'grid', 'pack', 'place', 'canvas', or 'text'. 
w.winfo_name()

    This method returns w's name relative to its parent. See Section 5.11, “Window names”. Also see .winfo_pathname(), below, to find out how to obtain a widget's path name. 
w.winfo_parent()

    Returns w's parent's path name, or an empty string if w is a top-level window. See Section 5.11, “Window names” above, for more on widget path names. 
w.winfo_pathname(id, displayof=0)

    If the displayof argument is false, returns the window path name of the widget with unique identifier id in the application's main window. If displayof is true, the id number specifies a widget in the same top-level window as w. See Section 5.11, “Window names” for a discussion of widget path names. 
w.winfo_pixels(number)

    For any dimension number (see Dimensions, above), this method returns that distance in pixels on w's display, as an integer. 
w.winfo_pointerx()

    Returns the same value as the x coordinate returned by .winfo_pointerxy(). 
w.winfo_pointerxy()

    Returns a tuple (x, y) containing the coordinates of the mouse pointer relative to w's root window. If the mouse pointer isn't on the same screen, returns (-1, -1). 
w.winfo_pointery()

    Returns the same value as the y coordinate returned by .winfo_pointerxy(). 
w.winfo_reqheight()

    These methods return the requested height of widget w. This is the minimum height necessary so that all of w's contents have the room they need. The actual height may be different due to negotiations with the geometry manager. 
w.winfo_reqwidth()

    Returns the requested width of widget w, the minimum width necessary to contain w. As with .winfo_reqheight(), the actual width may be different due to negotiations with the geometry manager. 
w.winfo_rgb(color)

    For any given color, this method returns the equivalent red-green-blue color specification as a 3-tuple (r, g, b), where each number is an integer in the range [0, 65536). For example, if the color is 'green', this method returns the 3-tuple (0, 65535, 0).

    For more on specifying colors, see Section 5.3, “Colors”. 
w.winfo_rootx()

    Returns the x coordinates of the left-hand side of w's root window relative to w's parent.

    If w has a border, this is the outer edge of the border. 
w.winfo_rooty()

    Returns the y coordinate of the top side of w's root window relative to w's parent.

    If w has a border, this is the top edge of the border. 
w.winfo_screenheight()

    Returns the height of the screen in pixels. 
w.winfo_screenmmheight()

    Returns the height of the screen in millimeters. 
w.winfo_screenmmwidth()

    Returns the width of the screen in millimeters. 
w.winfo_screenvisual()

    Returns a string that describes the display's method of color rendition. This is usually 'truecolor' for 16- or 24-bit displays, 'pseudocolor' for 256-color displays. 
w.winfo_screenwidth()

    Returns the width of the screen in pixels. 
w.winfo_toplevel()

    Returns the top-level window containing w. That window supports all the methods on Toplevel widgets; see Section 25, “Toplevel: Top-level window methods”. 
w.winfo_viewable()

    A predicate that returns a True value if w is viewable, that is, if it and all its ancestors in the same Toplevel are mapped. 
w.winfo_width()

    Returns the current width of w in pixels. See the remarks on geometry updating under .winfo_geometry(), above. You may prefer to use the .winfo_reqwidth() method, described above; it is always up to date. 
w.winfo_x()

    Returns the x coordinate of the left side of w relative to its parent. If w has a border, this is the outer edge of the border. 
w.winfo_y()

    Returns the y coordinate of the top side of w relative to its parent. If w has a border, this is the outer edge of the border. 
