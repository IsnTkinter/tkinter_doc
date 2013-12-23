********************
Les cadres ``Frame``
********************

 A frame is basically just a container for other widgets.

    Your application's root window is basically a frame.

    Each frame has its own grid layout, so the gridding of widgets within each frame works independently.

    Frame widgets are a valuable tool in making your application modular. You can group a set of related widgets into a compound widget by putting them into a frame. Better yet, you can declare a new class that inherits from Frame, adding your own interface to it. This is a good way to hide the details of interactions within a group of related widgets from the outside world. 

To create a new frame widget in a root window or frame named parent:

    w = Frame(parent, option, ...)

The constructor returns the new Frame widget. Options:

Table 19. Frame widget options
bg or background	The frame's background color. See Section 5.3, “Colors”.
bd or borderwidth	Width of the frame's border. The default is 0 (no border). For permitted values, see Section 5.1, “Dimensions”.
cursor	The cursor used when the mouse is within the frame widget; see Section 5.8, “Cursors”.
height	The vertical dimension of the new frame. This will be ignored unless you also call .grid_propagate(0) on the frame; see Section 4.2, “Other grid management methods”.
highlightbackground	Color of the focus highlight when the frame does not have focus. See Section 53, “Focus: routing keyboard input”.
highlightcolor	Color shown in the focus highlight when the frame has the focus.
highlightthickness	Thickness of the focus highlight.
padx 	Normally, a Frame fits tightly around its contents. To add N pixels of horizontal space inside the frame, set padx=N.
pady 	Used to add vertical space inside a frame. See padx above.
relief	The default relief for a frame is tk.FLAT, which means the frame will blend in with its surroundings. To put a border around a frame, set its borderwidth to a positive value and set its relief to one of the standard relief types; see Section 5.6, “Relief styles”.
takefocus	Normally, frame widgets are not visited by input focus (see Section 53, “Focus: routing keyboard input” for an overview of this topic). However, you can set takefocus=1 if you want the frame to receive keyboard input. To handle such input, you will need to create bindings for keyboard events; see Section 54, “Events” for more on events and bindings.
width	The horizontal dimension of the new frame. See Section 5.1, “Dimensions”. This value be ignored unless you also call .grid_propagate(0) on the frame; see Section 4.2, “Other grid management methods”. 
