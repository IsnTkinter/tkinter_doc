.. _MESSAGE:

******************
The Message widget
******************

 This widget is similar to the Label widget (see Section 12, “The Label widget”), but it is intended for displaying messages over multiple lines. All the text will be displayed in the same font; if you need to display text with more than one font, see Section 24, “The Text widget”.

To create a new Message widget as the child of a root window or frame named parent:

.. py:class:: Message(parent, option, ...)

        This constructor returns the new Message widget. Options may be any of these:

        :arg aspect: 
                Use this option to specify the ratio of width to height as a percentage. For example, aspect=100 would give you a text message fit into a square; with aspect=200, the text area would be twice as wide as high. The default value is 150, that is, the text will be fit into a box 50% wider than it is high.
        :arg bg: or background 
                The background color behind the text; see Section 5.3, “Colors”.
        :arg bd: or borderwidth 
                Width of the border around the widget; see Section 5.1, “Dimensions”. The default is two pixels. This option is visible only when the relief option is not tk.FLAT.
        :arg cursor: 
                Specifies the cursor that appears when the mouse is over the widget; see Section 5.8, “Cursors”.
        :arg font: 
                Specifies the font used to display the text in the widget; see Section 5.4, “Type fonts”.
        :arg fg: or foreground 
                Specifies the text color; see Section 5.3, “Colors”.
        :arg highlightbackground: 
                Color of the focus highlight when the widget does not have focus. See Section 53, “Focus: routing keyboard input”.
        :arg highlightcolor:
                Color shown in the focus highlight when the widget has the focus.
        :arg highlightthickness:
                Thickness of the focus highlight.
        :arg justify: 
                Use this option to specify how multiple lines of text are aligned. Use justify=tk.LEFT to get a straight left margin; justify=tk.CENTER to center each line; and justify=tk.RIGHT to get a straight right margin.
        :arg padx: 
                Use this option to add extra space inside the widget to the left and right of the text. The value is in pixels.
        :arg pady: 
                Use this option to add extra space inside the widget above and below the text. The value is in pixels.
        :arg relief: 
                This option specifies the appearance of the border around the outside of the widget; see Section 5.6, “Relief styles”. The default style is tk.FLAT.
        :arg takefocus: 
                Normally, a Message widget will not acquire focus (see Section 53, “Focus: routing keyboard input”). Use takefocus=True to add the widget to the focus traversal list.
        :arg text: 
                The value of this option is the text to be displayed inside the widget.
        :arg textvariable: 
                If you would like to be able to change the message under program control, associate this option with a StringVar instance (see Section 52, “Control variables: the values behind the widgets”). The value of this variable is the text to be displayed. If you specify both text and textvariable options, the text option is ignored.
        :arg width: 
                Use this option to specify the width of the text area in the widget, in pixels. The default width depends on the displayed text and the value of the aspect option. 
