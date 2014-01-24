.. _UNIVERSAL:

************************************
Méthodes communes à tous les widgets
************************************

Les méthodes données ci-après sont communes à tous les widgets (composants graphiques). Dans les description, ``w`` désigne un widget de type arbitraire.

.. py:method:: after(delai_ms, foncRapp=None, \*args)

            Demande à Tkinter d'appeller la fonction de rappel ``foncRapp`` avec les arguments ``args`` après l'écoulement du délai ``delai_ms`` donné en millisecondes. Votre fonction de rappel ne peut pas être appelée avant ce délai (même si son appel effectif peut le dépasser) et elle ne sera appelée qu'une fois.
            
            Elle retourne un entier qui sert d'identifiant et qui peut être passé à la méthode ``after_cancel`` pour annuler la demande d'appel de ``foncRapp``.

            Si vous ne donnez aucune fonction de rappel, cette fonction arrête l'exécution du programme pendant la durée du délai indiqué (comme la fonction standard sleep du module time).
            
.. py:method:: after_cancel(id)

            Annule la demande d'appel d'une fonction après un certain délai définie par la méthode ``after``. L'argument id est l'identifiant numérique retourné lors de l'appel originel de la méthode ``after``.

.. py:method:: after_idle(fonc, \*args)

            Demande à Tkinter d'appeler la fonction ``fonc`` avec les arguments ``args`` la prochaîne fois qu'il se trouvera en "sommeil", c'est à dire, la prochaîne fois qu'il n'aura plus aucun événement à traiter. La fonction fonc n'est appelée qu'une seule fois. Si vous souhaiter la rappeler, il faudra utiliser à nouveau cette méthode. Requests that Tkinter call function func with arguments args next time the system is idle, that is, next time there are no events to be processed. The callback will be called only once. If you want your callback to be called again, you must call the .after_idle method again. 

.. py:method:: bell()

             Produit un son, généralement un bip. 

.. py:method:: bind(sequence=None, evtGest=None, add=None)

             Cette méthode est utilisée pour attachée un gestionnaire d'événement (fonction) à la survenue d'un événement, précisé par sequence, sur le widget appelant (sur lequel cette méthode a été appliquée). Voir “Events” pour une vue d'ensemble sur le moyen de rendre votre application sensible aux actions de l'utilisateur.f

             L'argument sequence sert à décrire le type d'événement (action de l'utilisateur) auquel il faut réagir par le moyen du gestionnaire evtGest, c'est à dire en appelant cette fonction lorsque survient l'événement surveillé sur le widget. Si une liaison avait déjà été définie sur ce widget, l'ancien gestionnaire d'événement est remplacé par le nouveau sauf si vous utilisez add='+':  les deux gestionnaires (ou plus) sont alors préservés.

.. py:method:: bind_all(sequence=None, func=None, add=None)

             Similaire à la méthode bind(), mais s'applique à tous les widgets de l'application.

.. py:method:: bind_class(type, sequence=None, func=None, add=None)

             Similaire à la méthode ``bind()``, mais s'applique à tous les widget de type ``type`` (par exemple 'Button').

.. py:method:: bindtags(tagList=None)

             Si vous appelez cette méthode, elle vous retournera une marque (tag) "de liaison" pour le widget appelant comme une liste de chaînes de caractères. Une marque de liaison est le nom d'une fenêtre (qui débute par un '.') ou un type de widgtet (par exemple 'Listbox').If you call this method, it will return the “binding tags” for the widget as a sequence of strings. A binding tag is the name of a window (starting with '.') or the name of a class (e.g., 'Listbox').

             Vous pouvez modifier l'ordre dans lequel les niveaux de liaison sont appelés en passant à la méthode la liste des marques de liaison qui vous souhaitez que le widget utilisent.les niveaux de liaison You can change the order in which binding levels are called by passing as an argument the sequence of binding tags you want the widget to use.

             Voir, “Events” pour une discussion sur les niveaux de liaison et leur relation avec les marques. for a discussion of binding levels and their relationship to tags. 

.. py:method:: cget(option)

    Returns the current value of option as a string. You can also get the value of an option for widget w as w[option]. 

.. py:method:: clipboard_append(text)

    Appends the given text string to the display's clipboard, where cut and pasted strings are stored for all that display's applications. 

.. py:method:: clipboard_clear()

    Clears the display's clipboard (see .clipboard_append() above). 

.. py:method:: column_configure()

    See Section 4.2, “Other grid management methods”. 

.. py:method:: config(option=value, ...)

    Same as .configure(). 

.. py:method:: configure(option=value, ...)

    Set the values of one or more options. For the options whose names are Python reserved words (class, from, in), use a trailing underbar: 'class\_', 'from\_', 'in\_'.

    You can also set the value of an option for widget w with the statement

        w[option] = value

    If you call the .config() method on a widget with no arguments, you'll get a dictionary of all the widget's current options. The keys are the option names (including aliases like bd for borderwidth). The value for each key is:

        for most entries, a five-tuple: (option name, option database key, option database class, default value, current value); or,

        for alias names (like 'fg'), a two-tuple: (alias name, equivalent standard name). 


.. py:method:: destroy()

    Calling w.destroy() on a widget w destroys w and all its children. 

.. py:method:: event_add(virtual, \*sequences)

    This method creates a virtual event whose name is given by the virtual string argument. Each additional argument describes one sequence, that is, the description of a physical event. When that event occurs, the new virtual event is triggered.

    See Section 54, “Events” for a general description of virtual events. 

.. py:method:: event_delete(virtual, \*sequences)

    Deletes physical events from the virtual event whose name is given by the string virtual. If all the physical events are removed from a given virtual event, that virtual event won't happen anymore. 

.. py:method:: event_generate(sequence, \*\*kw)

    This method causes an event to trigger without any external stimulus. The handling of the event is the same as if it had been triggered by an external stimulus. The sequence argument describes the event to be triggered. You can set values for selected fields in the Event object by providing keyword=value arguments, where the keyword specifies the name of a field in the Event object.

    See Section 54, “Events” for a full discussion of events. 

.. py:method:: event_info(virtual=None)

    If you call this method without an argument, you'll get back a sequence of all the currently defined virtual event names.

    To retrieve the physical events associated with a virtual event, pass this method the name of the virtual event and you will get back a sequence of the physical sequence names, or None if the given virtual event has never been defined. 

.. py:method:: focus_displayof()

    Returns the name of the window that currently has input focus on the same display as the widget. If no such window has input focus, returns None.

    See Section 53, “Focus: routing keyboard input” for a general description of input focus. 

.. py:method:: focus_force()

    Force the input focus to the widget. This is impolite. It's better to wait for the window manager to give you the focus. See also .grab_set_global() below. 

.. py:method:: focus_get()

    Returns the widget that has focus in this application, if any—otherwise returns None. 

.. py:method:: focus_lastfor()

    This method retrieves the name of the widget that last had the input focus in the top-level window that contains w. If none of this top-level's widgets have ever had input focus, it returns the name of the top-level widget. If this application doesn't have the input focus, .focus_lastfor() will return the name of the widget that will get the focus next time it comes back to this application. 

.. py:method:: focus_set()

    If w's application has the input focus, the focus will jump to w. If w's application doesn't have focus, Tk will remember to give it to w next the application gets focus. 

.. py:method:: grab_current()

    If there is a grab in force for w's display, return its identifier, otherwise return None. Refer to Section 54, “Events” for a discussion of grabs. 

.. py:method:: grab_release()

    If w has a grab in force, release it. 

.. py:method:: grab_set()

    Widget w grabs all events for w's application. If there was another grab in force, it goes away. See Section 54, “Events” for a discussion of grabs. 

.. py:method:: grab_set_global()

    Widget w grabs all events for the entire screen. This is considered impolite and should be used only in great need. Any other grab in force goes away. Try to use this awesome power only for the forces of good, and never for the forces of evil, okay? 

.. py:method:: grab_status()

    If there is a local grab in force (set by .grab_set()), this method returns the string 'local'. If there is a global grab in force (from .grab_set_global()), it returns 'global'. If no grab is in force, it returns None. 

.. py:method:: grid_forget()

    See Section 4.2, “Other grid management methods”. 

.. py:method:: grid_propagate()

    See Section 4.2, “Other grid management methods”. 

.. py:method:: grid_remove()

    See Section 4.2, “Other grid management methods”. 

.. py:method:: image_names()

    Returns the names of all the images in w's application as a sequence of strings. 

.. py:method:: keys()

    Returns the option names for the widget as a sequence of strings. 

.. py:method:: lift(aboveThis=None)

    If the argument is None, the window containing w is moved to the top of the window stacking order. To move the window just above some Toplevel window w, pass w as an argument. 

.. py:method:: lower(belowThis=None)

    If the argument is None, the window containing w is moved to the bottom of the window stacking order. To move the window just below some Toplevel window w, pass w as an argument. 

.. py:method:: mainloop()

    This method must be called, generally after all the static widgets are created, to start processing events. You can leave the main loop with the .quit() method (below). You can also call this method inside an event handler to resume the main loop. 

.. py:method:: nametowidget(name)

    This method returns the actual widget whose path name is name. See Section 5.11, “Window names”. If the name is unknown, this method will raise KeyError. 

.. py:method:: option_add(pattern, value, priority=None)

    This method adds default option values to the Tkinter option database. The pattern is a string that specifies a default value for options of one or more widgets. The priority values are one of:
    20 	For global default properties of widgets.
    40 	For default properties of specific applications.
    60 	For options that come from user files such as their .Xdefaults file.
    80 	For options that are set after the application starts up. This is the default priority level.

    Higher-level priorities take precedence over lower-level ones. See Section 27, “Standardizing appearance” for an overview of the option database. The syntax of the pattern argument to .option_add() is the same as the option-pattern part of the resource specification line.

    For example, to get the effect of this resource specification line:

    \*Button\*font: times 24 bold

    your application (self in this example) might include these lines:

    .. code-block:: python

        self.bigFont = tkFont.Font(family='times', size=24,
                                     weight='bold')
        self.option_add('\*Button*font', self.bigFont)

    Any Button widgets created after executing these lines would default to bold Times 24 font (unless overriden by a font option to the Button constructor). 

.. py:method:: option_clear()

    This method removes all options from the Tkinter option database. This has the effect of going back to all the default values. 

.. py:method:: option_get(name, classname)

    Use this method to retrieve the current value of an option from the Tkinter option database. The first argument is the instance key and the second argument is the class key. If there are any matches, it returns the value of the option that best matches. If there are no matches, it returns ''.

    Refer to Section 27, “Standardizing appearance” for more about how keys are matched with options. 

.. py:method:: option_readfile(fileName, priority=None)

    As a convenience for user configuration, you can designate a named file where users can put their preferred options, using the same format as the .Xdefaults file. Then, when your application is initializing, you can pass that file's name to this method, and the options from that file will be added to the database. If the file doesn't exist, or its format is invalid, this method will raise tk.TclError.

    Refer to Section 27, “Standardizing appearance” for an introduction to the options database and the format of option files. 

.. py:method:: register(function)

    This method creates a Tcl wrapper around a Python function, and returns the Tcl wrapper name as a string. For an example of the usage of this method, see Section 10.2, “Adding validation to an Entry widget”. 

.. py:method:: quit()

    This method exits the main loop. See .mainloop(), above, for a discussion of main loops. 

.. py:method:: rowconfigure()

    See Section 4.2, “Other grid management methods”. 

.. py:method:: selection_clear()

    If w currently has a selection (such as a highlighted segment of text in an entry widget), clear that selection. 

.. py:method:: selection_get()

    If w currently has a selection, this method returns the selected text. If there is no selection, it raises tk.TclError. 

.. py:method:: selection_own()

    Make w the owner of the selection in w's display, stealing it from the previous owner, if any. 

.. py:method:: selection_own_get()

    Returns the widget that currently owns the selection in w's display. Raises tk.TclError if there is no such selection. 

.. py:method:: tk_focusFollowsMouse()

    Normally, the input focus cycles through a sequence of widgets determined by their hierarchy and creation order; see Section 53, “Focus: routing keyboard input”. You can, instead, tell Tkinter to force the focus to be wherever the mouse is; just call this method. There is no easy way to undo it, however. 

.. py:method:: tk_focusNext()

    Returns the widget that follows w in the focus traversal sequence. Refer to Section 53, “Focus: routing keyboard input” for a discussion of focus traversal. 

.. py:method:: tk_focusPrev()

    Returns the widget that precedes w in the focus traversal sequence. 

.. py:method:: unbind(sequence, funcid=None)

    This method deletes bindings on w for the event described by sequence. If the second argument is a callback bound to that sequence, that callback is removed and the rest, if any, are left in place. If the second argument is omitted, all bindings are deleted.

    See Section 54, “Events”, below, for a general discussion of event bindings. 

.. py:method:: unbind_all(sequence)

    Deletes all event bindings throughout the application for the event described by the given sequence. 

.. py:method:: unbind_class(className, sequence)

    Like .unbind(), but applies to all widgets named className (e.g., 'Entry' or 'Listbox'). 

.. py:method:: update()

    This method forces the updating of the display. It should be used only if you know what you're doing, since it can lead to unpredictable behavior or looping. It should never be called from an event callback or a function that is called from an event callback. 

.. py:method:: update_idletasks()

    Some tasks in updating the display, such as resizing and redrawing widgets, are called idle tasks because they are usually deferred until the application has finished handling events and has gone back to the main loop to wait for new events.

    If you want to force the display to be updated before the application next idles, call the w.update_idletasks() method on any widget. 

.. py:method:: wait_variable(v)

    Waits until the value of variable v is set, even if the value does not change. This method enters a local wait loop, so it does not block the rest of the application. 

.. py:method:: wait_visibility(w)

    Wait until widget w (typically a Toplevel) is visible. 

.. py:method:: wait_window(w)

    Wait until window w is destroyed. 

.. py:method:: winfo_children()

    Returns a list of all w's children, in their stacking order from lowest (bottom) to highest (top). 

.. py:method:: winfo_class()

    Returns w's class name (e.g., 'Button'). 

.. py:method:: winfo_containing(rootX, rootY, displayof=0)

    This method is used to find the window that contains point (rootX, rootY). If the displayof option is false, the coordinates are relative to the application's root window; if true, the coordinates are treated as relative to the top-level window that contains w. If the specified point is in one of the application's top-level window, this method returns that window; otherwise it returns None. 

.. py:method:: winfo_depth()

    Returns the number of bits per pixel in w's display. 

.. py:method:: winfo_fpixels(number)

    For any dimension number (see Section 5.1, “Dimensions”), this method returns that distance in pixels on w's display, as a number of type float. 

.. py:method:: winfo_geometry()

    Returns the geometry string describing the size and on-screen location of w. See Section 5.10, “Geometry strings”.
    Warning

    The geometry is not accurate until the application has updated its idle tasks. In particular, all geometries are initially '1x1+0+0' until the widgets and geometry manager have negotiated their sizes and positions. See the .update_idletasks() method, above, in this section to see how to insure that the widget's geometry is up to date.

.. py:method:: winfo_height()

    Returns the current height of w in pixels. See the remarks on geometry updating under .winfo_geometry(), above. You may prefer to use .winfo_reqheight(), described below, which is always up to date. 

.. py:method:: winfo_id()

    Returns an integer that uniquely identifies w within its top-level window. You will need this for the .winfo_pathname() method, below. 

.. py:method:: winfo_ismapped()

    This method returns true if w is mapped, false otherwise. A widget is mapped if it has been gridded (or placed or packed, if you are using one of the other geometry managers) into its parent, and if its parent is mapped, and so on up to the top-level window. 

.. py:method:: winfo_manager()

    If w has not been gridded (or placed via one of the other geometry managers), this method returns an empty string. If w has been gridded or otherwise placed, it returns a string naming the geometry manager for w: this value will be one of 'grid', 'pack', 'place', 'canvas', or 'text'. 

.. py:method:: winfo_name()

    This method returns w's name relative to its parent. See Section 5.11, “Window names”. Also see .winfo_pathname(), below, to find out how to obtain a widget's path name. 

.. py:method:: winfo_parent()

    Returns w's parent's path name, or an empty string if w is a top-level window. See Section 5.11, “Window names” above, for more on widget path names. 

.. py:method:: winfo_pathname(id, displayof=0)

    If the displayof argument is false, returns the window path name of the widget with unique identifier id in the application's main window. If displayof is true, the id number specifies a widget in the same top-level window as w. See Section 5.11, “Window names” for a discussion of widget path names. 

.. py:method:: winfo_pixels(number)

    For any dimension number (see Dimensions, above), this method returns that distance in pixels on w's display, as an integer. 

.. py:method:: winfo_pointerx()

    Returns the same value as the x coordinate returned by .winfo_pointerxy(). 

.. py:method:: winfo_pointerxy()

    Returns a tuple (x, y) containing the coordinates of the mouse pointer relative to w's root window. If the mouse pointer isn't on the same screen, returns (-1, -1). 

.. py:method:: winfo_pointery()

    Returns the same value as the y coordinate returned by .winfo_pointerxy(). 

.. py:method:: winfo_reqheight()

    These methods return the requested height of widget w. This is the minimum height necessary so that all of w's contents have the room they need. The actual height may be different due to negotiations with the geometry manager. 

.. py:method:: winfo_reqwidth()

    Returns the requested width of widget w, the minimum width necessary to contain w. As with .winfo_reqheight(), the actual width may be different due to negotiations with the geometry manager. 

.. py:method:: winfo_rgb(color)

    For any given color, this method returns the equivalent red-green-blue color specification as a 3-tuple (r, g, b), where each number is an integer in the range [0, 65536). For example, if the color is 'green', this method returns the 3-tuple (0, 65535, 0).

    For more on specifying colors, see Section 5.3, “Colors”. 

.. py:method:: winfo_rootx()

    Returns the x coordinates of the left-hand side of w's root window relative to w's parent.

    If w has a border, this is the outer edge of the border. 

.. py:method:: winfo_rooty()

    Returns the y coordinate of the top side of w's root window relative to w's parent.

    If w has a border, this is the top edge of the border. 

.. py:method:: winfo_screenheight()

    Returns the height of the screen in pixels. 

.. py:method:: winfo_screenmmheight()

    Returns the height of the screen in millimeters. 

.. py:method:: winfo_screenmmwidth()

    Returns the width of the screen in millimeters. 

.. py:method:: winfo_screenvisual()

    Returns a string that describes the display's method of color rendition. This is usually 'truecolor' for 16- or 24-bit displays, 'pseudocolor' for 256-color displays. 

.. py:method:: winfo_screenwidth()

    Returns the width of the screen in pixels. 

.. py:method:: winfo_toplevel()

    Returns the top-level window containing w. That window supports all the methods on Toplevel widgets; see Section 25, “Toplevel: Top-level window methods”. 

.. py:method:: winfo_viewable()

    A predicate that returns a True value if w is viewable, that is, if it and all its ancestors in the same Toplevel are mapped. 

.. py:method:: winfo_width()

    Returns the current width of w in pixels. See the remarks on geometry updating under .winfo_geometry(), above. You may prefer to use the .winfo_reqwidth() method, described above; it is always up to date. 

.. py:method:: winfo_x()

    Returns the x coordinate of the left side of w relative to its parent. If w has a border, this is the outer edge of the border. 

.. py:method:: winfo_y()

    Returns the y coordinate of the top side of w relative to its parent. If w has a border, this is the outer edge of the border. 
