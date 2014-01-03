**********************************
Les cases à cocher ``Checkbutton``
**********************************

The purpose of a checkbutton widget (sometimes called “checkbox”) is to allow the user to read and select a two-way choice. The graphic above shows how checkbuttons look in the off (0) and on (1) state in one implementation: this is a screen shot of two checkbuttons using 24-point Times font.

The indicator is the part of the checkbutton that shows its state, and the label is the text that appears beside it.

    You will need to create a control variable, an instance of the IntVar class, so your program can query and set the state of the checkbutton. See Section 52, “Control variables: the values behind the widgets”, below.

    You can also use event bindings to react to user actions on the checkbutton; see Section 54, “Events”, below.

    You can disable a checkbutton. This changes its appearance to “grayed out” and makes it unresponsive to the mouse.

    You can get rid of the checkbutton indicator and make the whole widget a “push-push” button that looks recessed when it is set, and looks raised when it is cleared. 

To create a checkbutton in an existing parent window or frame parent:

.. py:class:: Checkbutton(parent, option, ...)

        The constructor returns a new Checkbutton widget. Options include:

        :arg activebackground: 
                Background color when the checkbutton is under the cursor. See Section 5.3, “Colors”.
        :arg activeforeground: 
                Foreground color when the checkbutton is under the cursor.
        :arg anchor:
                If the widget inhabits a space larger than it needs, this option specifies where the checkbutton will sit in that space. The default is anchor=tk.CENTER. See Section 5.5, “Anchors” for the allowable values. For example, if you use anchor=NW, the widget will be placed in the upper left corner of the space.
        :arg bg: or background
                The normal background color displayed behind the label and indicator. See Section 5.3, “Colors”. For the bitmap option, this specifies the color displayed for 0-bits in the bitmap.
        :arg bitmap:
                To display a monochrome image on a button, set this option to a bitmap; Voir :ref:`bitmaps`.
        :arg bd: or borderwidth
                The size of the border around the indicator. Default is two pixels. For possible values, Voir :ref:`bitmaps`.
        :arg command:
                A procedure to be called every time the user changes the state of this checkbutton.
        :arg compound: 
                Use this option to display both text and a graphic, which may be either a bitmap or an image, on the button. Allowable values describe the position of the graphic relative to the text, and may be any of tk.BOTTOM, tk.TOP, tk.LEFT, tk.RIGHT, or tk.CENTER. For example, compound=tk.LEFT would position the graphic to the left of the text.
        :arg cursor:
                If you set this option to a cursor name (Voir :ref:`pointeurs`).
                the mouse cursor will change to that pattern when it is over the checkbutton.
        :arg disabledforeground:
                The foreground color used to render the text of a disabled checkbutton. The default is a stippled version of the default foreground color.
        :arg font:
                The font used for the text. See Section 5.4, “Type fonts”.
        :arg fg: or foreground
                The color used to render the text. For the bitmap option, this specifies the color displayed for 1-bits in the bitmap.
        :arg height:
                The number of lines of text on the checkbutton. Default is 1.
        :arg highlightbackground:
                color of the focus highlight when the checkbutton does not have focus. See Section 53, “Focus: routing keyboard input”.
        :arg highlightcolor:
                The color of the focus highlight when the checkbutton has the focus.
        :arg highlightthickness:
                The thickness of the focus highlight. Default is 1. Set to 0 to suppress display of the focus highlight.
        :arg image:
                To display a graphic image on the button, set this option to an image object. See Section 5.9, “Images”.
        :arg indicatoron:
                Normally a checkbutton displays as its indicator a box that shows whether the checkbutton is set or not. You can get this behavior by setting indicatoron=1. However, if you set indicatoron=0, the indicator disappears, and the entire widget becomes a push-push button that looks raised when it is cleared and sunken when it is set. You may want to increase the borderwidth value to make it easier to see the state of such a control.
        :arg justify:
                If the text contains multiple lines, this option controls how the text is justified: tk.CENTER, tk.LEFT, or tk.RIGHT.
        :arg offrelief: 
                By default, checkbuttons use the tk.RAISED relief style when the button is off (cleared); use this option to specify a different relief style to be displayed when the button is off. See Section 5.6, “Relief styles” for values.
        :arg offvalue:
                Normally, a checkbutton's associated control variable will be set to 0 when it is cleared (off). You can supply an alternate value for the off state by setting offvalue to that value.
        :arg onvalue:
                Normally, a checkbutton's associated control variable will be set to 1 when it is set (on). You can supply an alternate value for the on state by setting onvalue to that value.
        :arg overrelief: 
                Use this option to specify a relief style to be displayed when the mouse is over the checkbutton; Voir :ref:`reliefs`.
        :arg padx:
                How much space to leave to the left and right of the checkbutton and text. Default is 1 pixel. For possible values, Voir :ref:`dimensions`.
        :arg pady:
                How much space to leave above and below the checkbutton and text. Default is 1 pixel.
        :arg relief:
                With the default value, relief=tk.FLAT, the checkbutton does not stand out from its background. You may set this option to any of the other styles (Voir :ref:`reliefs`).
                , or use relief=tk.SOLID, which gives you a solid black frame around it.
        :arg selectcolor:
                The color of the checkbutton when it is set. Default is selectcolor='red'.
        :arg selectimage:
                If you set this option to an image, that image will appear in the checkbutton when it is set. See Section 5.9, “Images”.
        :arg state:
                The default is state=tk.NORMAL, but you can use state=tk.DISABLED to gray out the control and make it unresponsive. If the cursor is currently over the checkbutton, the state is tk.ACTIVE.
        :arg takefocus:
                The default is that the input focus (see Section 53, “Focus: routing keyboard input”) will pass through a checkbutton. If you set takefocus=0, focus will not pass through it.
        :arg text:
                The label displayed next to the checkbutton. Use newlines ('\n') to display multiple lines of text.
        :arg textvariable:
                If you need to change the label on a checkbutton during execution, create a StringVar (see Section 52, “Control variables: the values behind the widgets”) to manage the current value, and set this option to that control variable. Whenever the control variable's value changes, the checkbutton's annotation will automatically change as well.
        :arg underline:
                With the default value of -1, none of the characters of the text label are underlined. Set this option to the index of a character in the text (counting from zero) to underline that character.
        :arg variable:
                The control variable that tracks the current state of the checkbutton; see Section 52, “Control variables: the values behind the widgets”. Normally this variable is an IntVar, and 0 means cleared and 1 means set, but see the offvalue and onvalue options above.
        :arg width:
                The default width of a checkbutton is determined by the size of the displayed image or text. You can set this option to a number of characters and the checkbutton will always have room for that many characters.
        :arg wraplength:
                Normally, lines are not wrapped. You can set this option to a number of characters and all lines will be broken into pieces no longer than that number.

        Methods on checkbuttons include:

        .. py:method:: deselect()

                Clears (turns off) the checkbutton. 

        .. py:method:: flash()

                Flashes the checkbutton a few times between its active and normal colors, but leaves it the way it started. 

        .. py:method:: invoke()

                You can call this method to get the same actions that would occur if the user clicked on the checkbutton to change its state. 

        .. py:method:: select()

                Sets (turns on) the checkbutton. 

        .. py:method:: toggle()

                Clears the checkbutton if set, sets it if cleared. 
