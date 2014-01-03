**********************
The PanedWindow widget
**********************

 The purpose of the PanedWindow widget is to give the application's user some control over how space is divided up within the application.

A PanedWindow is somewhat like a Frame: it is a container for child widgets. Each PanedWindow widget contains a horizontal or vertical stack of child widgets. Using the mouse, the user can drag the boundaries between the child widgets back and forth.

    You may choose to display handles within the widget. A handle is a small square that the user can drag with the mouse.

    You may choose to make sashes visible. A sash is a bar placed between the child widgets.

    A pane is the area occupied by one child widget. 

To create a new PanedWindow widget as the child of a root window or frame named parent:

    w = tk.PanedWindow(parent, option, ...)

This constructor returns the new PanedWindow widget. Here are the options:

Table 27. PanedWindow widget options
bg or background 	The background color displayed behind the child widgets; see Section 5.3, “Colors”.
bd or borderwidth 	Width of the border around the outside of the widget; see Section 5.1, “Dimensions”. The default is two pixels.
cursor 	The cursor to be displayed when the mouse is over the widget; see Section 5.8, “Cursors”.
handlepad 	Use this option to specify the distance between the handle and the end of the sash. For orient=tk.VERTICAL, this is the distance between the left end of the sash and the handle; for orient=tk.HORIZONTAL, it is the distance between the top of the sash and the handle. The default value is eight pixels; for other values, see Section 5.1, “Dimensions”.
handlesize 	Use this option to specify the size of the handle, which is always a square; see Section 5.1, “Dimensions”. The default value is eight pixels.
height 	Specifies the height of the widget; see Section 5.1, “Dimensions”. If you don't specify this option, the height is determined by the height of the child widgets.
opaqueresize 	This option controls how a resizing operation works. For the default value, opaqueresize=True, the resizing is done continuously as the sash is dragged. If this option is set to False, the sash (and adjacent child widgets) stays put until the user releases the mouse button, and then it jumps to the new position.
orient 	To stack child widgets side by side, use orient=tk.HORIZONTAL. To stack them top to bottom, use orient=tk.VERTICAL.
relief 	Selects the relief style of the border around the widget; see Section 5.6, “Relief styles”. The default is tk.FLAT.
sashpad 	Use this option to allocate extra space on either side of each sash. The default is zero; for other values, see Section 5.1, “Dimensions”.
sashrelief 	This option specifies the relief style used to render the sashes; see Section 5.6, “Relief styles”. The default style is tk.FLAT.
sashwidth 	Specifies the width of the sash; see Section 5.1, “Dimensions”. The default width is two pixels.
showhandle 	Use showhandle=True to display the handles. For the default value, False, the user can still use the mouse to move the sashes. The handle is simply a visual cue.
width 	Width of the widget; see Section 5.1, “Dimensions”. If you don't specify a value, the width will be determined by the sizes of the child widgets.

To add child widgets to a PanedWindow, create the child widgets as children of the parent PanedWindow, but rather than using the .grid() method to register them, use the .add() method on the PanedWindow.

Here are the methods on PanedWindow widgets.

.add(child[, option=value] ...)

    Use this method to add the given child widget as the next child of this PanedWindow. First create the child widget with the PanedWindow as its parent widget, but do not call the .grid() method to register it. Then call .add(child) and the child will appear inside the PanedWindow in the next available position.

    Associated with each child is a set of configuration options that control its position and appearance. See Section 19.1, “PanedWindow child configuration options”. You can supply these configuration options as keyword arguments to the .add() method. You can also set or change their values anytime with the .paneconfig() method, or retrieve the current value of any of these options using the .panecget() method; these methods are described below. 

.forget(child)

    Removes a child widget. 

.identify(x, y

    For a given location (x, y) in window coordinates, this method returns a value that describes the feature at that location.

        If the feature is a child window, the method returns an empty string.

        If the feature is a sash, the method returns a tuple (n, 'sash') where n is 0 for the first sash, 1 for the second, and so on.

        If the feature is a handle, the method returns a tuple (n, 'handle') where n is 0 for the first handle, 1 for the second, and so on. 

.panecget(child, option)

    This method retrieves the value of a child widget configuration option, where child is the child widget and option is the name of the option as a string. For the list of child widget configuration options, see Section 19.1, “PanedWindow child configuration options”. 

.paneconfig(child, option=value, ...)

    Use this method to configure options for child widgets. The options are described in Section 19.1, “PanedWindow child configuration options”. 

.panes()

    This method returns a list of the child widgets, in order from left to right (for orient=tk.HORIZONTAL) or top to bottom (for orient=tk.VERTICAL). 

.remove(child)

    Removes the given child; this is the same action as the .forget() method. 

.sash_coord(index)

    This method returns the location of a sash. The index argument selects the sash: 0 for the sash between the first two children, 1 for the sash between the second and third child, and so forth. The result is a tuple (x, y) containing the coordinates of the upper left corner of the sash. 

.sash_place(index, x, y)

    Use this method to reposition the sash selected by index (0 for the first sash, and so on). The x and y coordinates specify the desired new position of the upper left corner of the sash. Tkinter ignores the coordinate orthogonal to the orientation of the widget: use the x value to reposition the sash for orient=tk.HORIZONTAL, and use the y coordinate to move the sash for option orient=tk.VERTICAL. 
    
PanedWindow child configuration options
=======================================

 Each child of a PanedWindow has a set of configuration options that control its position and appearance. These options can be provided when a child is added with the .add() method, or set with the .paneconfig() method, or queried with the .panecget() methods described above.

Table 28. PanedWindow child widget options
after 	Normally, when you .add() a new child to a PanedWindow, the new child is added after any existing child widgets. You may instead use the after=w option to insert the new widget at a position just after an existing child widget w.
before 	When used as option before=w in a call to the .add() method, places the new widget at a position just before an existing child widget w.
height 	This option specifies the desired height of the child widget; see Section 5.1, “Dimensions”.
minsize 	Use this option to specify a minimum size for the child widget in the direction of the PanedWindow's orientation. For orient=tk.HORIZONTAL, this is the minimum width; for orient=tk.VERTICAL, it is the minimum height. For permissible values, see Section 5.1, “Dimensions”.
padx 	The amount of extra space to be added to the left and right of the child widget; see Section 5.1, “Dimensions”.
pady 	The amount of extra space to be added above and below the child widget; see Section 5.1, “Dimensions”.
sticky 	This option functions like the sticky argument to the .grid() method; see Section 4.1, “The .grid() method”. It specifies how to position a child widget if the pane is larger than the widget. For example, sticky=tk.NW would position the widget in the upper left (“northwest”) corner of the pane.
width 	Desired width of the child widget; see Section 5.1, “Dimensions”. 
