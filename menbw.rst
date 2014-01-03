*****************
Menubutton widget
*****************

 A menubutton is the part of a drop-down menu that stays on the screen all the time. Every menubutton is associated with a Menu widget (see above) that can display the choices for that menubutton when the user clicks on it.

To create a menubutton within a root window or frame parent:

.. py:class:: Menubutton(parent, option, ...)

            The constructor returns the new Menubutton widget. Options:

        :arg activebackground: 
                The background color when the mouse is over the menubutton. See Section 5.3, “Colors”.
        :arg activeforeground: 
                The foreground color when the mouse is over the menubutton.
        :arg anchor:
                This options controls where the text is positioned if the widget has more space than the text needs. The default is anchor=tk.CENTER, which centers the text. For other options, see Section 5.5, “Anchors”. For example, if you use anchor=tk.W, the text would be centered against the left side of the widget.
        :arg bg: or background
                The background color when the mouse is not over the menubutton.
        :arg bitmap:
                To display a bitmap on the menubutton, set this option to a bitmap name; see Section 5.7, “Bitmaps”.
        :arg bd: or borderwidth
                Width of the border around the menubutton. Default is two pixels. For possible values, see Section 5.1, “Dimensions”.
        :arg compound: 
                If you specify both text and a graphic (either a bitmap or an image), this option specifies where the graphic appears relative to the text. Possible values are tk.NONE (the default value), tk.TOP, tk.BOTTOM, tk.LEFT, tk.RIGHT, and tk.CENTER. For example, compound=tk.RIGHT would position the graphic to the right of the text. If you specify compound=tk.NONE, the graphic is displayed but the text (if any) is not.
        :arg cursor:
                The cursor that appears when the mouse is over this menubutton. See Section 5.8, “Cursors”.
        :arg direction:
                Normally, the menu will appear below the menubutton. Set direction=tk.LEFT to display the menu to the left of the button; use direction=tk.RIGHT to display the menu to the right of the button; or use direction='above' to place the menu above the button.
        :arg disabledforeground:
                The foreground color shown on this menubutton when it is disabled.
        :arg fg: or foreground
                The foreground color when the mouse is not over the menubutton.
        :arg font: 
                Specifies the font used to display the text; see Section 5.4, “Type fonts”.
        :arg height:
                The height of the menubutton in lines of text (not pixels!). The default is to fit the menubutton's size to its contents.
        :arg highlightbackground: 
                Color of the focus highlight when the widget does not have focus. See Section 53, “Focus: routing keyboard input”.
        :arg highlightcolor:
                Color shown in the focus highlight when the widget has the focus.
        :arg highlightthickness:
                Thickness of the focus highlight.
        :arg image:
                To display an image on this menubutton, set this option to the image object. See Section 5.9, “Images”.
        :arg justify:
                This option controls where the text is located when the text doesn't fill the menubutton: use justify=tk.LEFT to left-justify the text (this is the default); use justify=tk.CENTER to center it, or justify=tk.RIGHT to right-justify.
        :arg menu:
                To associate the menubutton with a set of choices, set this option to the Menu object containing those choices. That menu object must have been created by passing the associated menubutton to the constructor as its first argument. See below for an example showing how to associate a menubutton and menu.
        :arg padx:
                How much space to leave to the left and right of the text of the menubutton. Default is 1.
        :arg pady:
                How much space to leave above and below the text of the menubutton. Default is 1.
        :arg relief:
                Normally, menubuttons will have tk.RAISED appearance. For other 3-d effects, see Section 5.6, “Relief styles”.
        :arg state:
                Normally, menubuttons respond to the mouse. Set state=tk.DISABLED to gray out the menubutton and make it unresponsive.
        :arg takefocus: 
                Normally, menubuttons do not take keyboard focus (see Section 53, “Focus: routing keyboard input”). Use takefocus=True to add the menubutton to the focus traversal order.
        :arg text:
                To display text on the menubutton, set this option to the string containing the desired text. Newlines ('\n') within the string will cause line breaks.
        :arg textvariable:
                You can associate a control variable of class StringVar with this menubutton. Setting that control variable will change the displayed text. See Section 52, “Control variables: the values behind the widgets”.
        :arg underline:
                Normally, no underline appears under the text on the menubutton. To underline one of the characters, set this option to the index of that character.
        :arg width:
                Width of the menubutton in characters (not pixels!). If this option is not set, the label will be sized to fit its contents.
        :arg wraplength:
                Normally, lines are not wrapped. You can set this option to a number of characters and all lines will be broken into pieces no longer than that number.

Here is a brief example showing the creation of a menubutton and its associated menu with two checkboxes::

    self.mb = tk.Menubutton(self, text='condiments',
                             relief=RAISED)
    self.mb.grid()

    self.mb.menu = tk.Menu(self.mb, tearoff=0)
    self.mb['menu'] = self.mb.menu

    self.mayoVar  = tk.IntVar()
    self.ketchVar = tk.IntVar()
    self.mb.menu.add_checkbutton(label='mayo',
        variable=self.mayoVar)
    self.mb.menu.add_checkbutton(label='ketchup',
        variable=self.ketchVar)

This example creates a menubutton labeled condiments. When clicked, two checkbuttons labeled mayo and ketchup will drop down. 
