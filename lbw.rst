.. _LISTBOX:

******************
The Listbox widget
******************

The purpose of a listbox widget is to display a set of lines of text. Generally they are intended to allow the user to select one or more items from a list. All the lines of text use the same font. If you need something more like a text editor, see Section 24, “The Text widget”.

To create a new listbox widget inside a root window or frame parent:

.. py:class:: Listbox(parent, option, ...)

        This constructor returns the new Listbox widget. Options:

        :arg activestyle:
                This option specifies the appearance of the active line. It may have any of these values:
                'underline': The active line is underlined. This is the default option.

                'dotbox': The active line is enclosed in a dotted line on all four sides. 

                'none': The active line is given no special appearance.

        :arg bg: or background 
                The background color in the listbox.
        :arg bd: or borderwidth 
                The width of the border around the listbox. Default is two pixels. For possible values, Voir :ref:`dimensions`.
        :arg cursor: 
                The cursor that appears when the mouse is over the listbox. Voir :ref:`pointeurs`.
        :arg disabledforeground: 
                The color of the text in the listbox when its state is tk.DISABLED.
        :arg exportselection: 
                By default, the user may select text with the mouse, and the selected text will be exported to the clipboard. To disable this behavior, use exportselection=0.
        :arg font: 
                The font used for the text in the listbox. Voir :ref:`polices`.
        :arg fg: or foreground 
                The color used for the text in the listbox. Voir :ref:`couleurs`.
        :arg height: 
                Number of lines (not pixels!) shown in the listbox. Default is 10.
        :arg highlightbackground: 
                Color of the focus highlight when the widget does not have focus. See Section 53, “Focus: routing keyboard input”.
        :arg highlightcolor: 
                Color shown in the focus highlight when the widget has the focus.
        :arg highlightthickness: 
                Thickness of the focus highlight.
        :arg listvariable:
                A StringVar that is connected to the complete list of values in the listbox (see Section 52, “Control variables: the values behind the widgets”.
                If you call the .get() method of the listvariable, you will get back a string of the form "('v0', 'v1', ...)", where each vi is the contents of one line of the listbox.
                To change the entire set of lines in the listbox at once, call .set(s) on the listvariable, where s is a string containing the line values with spaces between them.
                For example, if listCon is a StringVar associated with a listbox's listvariable option, this call would set the listbox to contain three lines:
                listCon.set('ant bee cicada')
                This call would return the string "('ant', 'bee', 'cicada')":
                listCon.get()
        :arg relief: 
                Selects three-dimensional border shading effects. The default is tk.SUNKEN. For other values, Voir :ref:`reliefs`.
        :arg selectbackground: 
                The background color to use displaying selected text.
        :arg selectborderwidth: 
                The width of the border to use around selected text. The default is that the selected item is shown in a solid block of color selectbackground; if you increase the selectborderwidth, the entries are moved farther apart and the selected entry shows tk.RAISED relief (Voir :ref:`reliefs`).
        :arg selectforeground: 
                The foreground color to use displaying selected text.
        :arg selectmode: 
                Determines how many items can be selected, and how mouse drags affect the selection:
                        tk.BROWSE: Normally, you can only select one line out of a listbox. If you click on an item and then drag to a different line, the selection will follow the mouse. This is the default.
                        tk.SINGLE: You can only select one line, and you can't drag the mouse—wherever you click button 1, that line is selected.
                        tk.MULTIPLE: You can select any number of lines at once. Clicking on any line toggles whether or not it is selected.
                        tk.EXTENDED: You can select any adjacent group of lines at once by clicking on the first line and dragging to the last line. 
        :arg state: 
                By default, a listbox is in the tk.NORMAL state. To make the listbox unresponsive to mouse events, set this option to tk.DISABLED.
        :arg takefocus: 
                Normally, the focus will tab through listbox widgets. Set this option to 0 to take the widget out of the sequence. See Section 53, “Focus: routing keyboard input”.
        :arg width: 
                The width of the widget in characters (not pixels!). The width is based on an average character, so some strings of this length in proportional fonts may not fit. The default is 20.
        :arg xscrollcommand: 
                If you want to allow the user to scroll the listbox horizontally, you can link your listbox widget to a horizontal scrollbar. Set this option to the .set method of the scrollbar. See Section 14.1, “Scrolling a Listbox widget” for more on scrollable listbox widgets.
        :arg yscrollcommand: 
                If you want to allow the user to scroll the listbox vertically, you can link your listbox widget to a vertical scrollbar. Set this option to the .set method of the scrollbar. See Section 14.1, “Scrolling a Listbox widget”.

        A special set of index forms is used for many of the methods on listbox objects:

            If you specify an index as an integer, it refers to the line in the listbox with that index, counting from 0.

            Index tk.END refers to the last line in the listbox.

            Index tk.ACTIVE refers to the selected line. If the listbox allows multiple selections, it refers to the line that was last selected.

            An index string of the form '@x,y' refers to the line closest to coordinate (x,y) relative to the widget's upper left corner. 

        Methods on Listbox objects include:

        .. hlist::
                :columns: 4

                * :py:meth:`activate`
                * :py:meth:`bbox`
                * :py:meth:`curselection`
                * :py:meth:`delete`
                * :py:meth:`get`
                * :py:meth:`index`
                * :py:meth:`insert`
                * :py:meth:`itemcget`
                * :py:meth:`itemconfig`
                * :py:meth:`nearest`
                * :py:meth:`scan_dragto`
                * :py:meth:`scan_mark`
                * :py:meth:`see`
                * :py:meth:`selection_anchor`
                * :py:meth:`selection_clear`
                * :py:meth:`selection_includes`
                * :py:meth:`selection_set`
                * :py:meth:`size`
                * :py:meth:`xview`
                * :py:meth:`xview_moveto`
                * :py:meth:`xview_scroll`
                * :py:meth:`yview`
                * :py:meth:`yview_moveto`
                * :py:meth:`yview_scroll`

        .. py:method:: activate(index)

                Selects the line specifies by the given index. 

        .. py:method:: bbox(index)

                Returns the bounding box of the line specified by index as a 4-tuple (xoffset, yoffset, width, height), where the upper left pixel of the box is at (xoffset, yoffset) and the width and height are given in pixels. The returned width value includes only the part of the line occupied by text.

                If the line specified by the index argument is not visible, this method returns None. If it is partially visible, the returned bounding box may extend outside the visible area. 

        .. py:method:: curselection()

                Returns a tuple containing the line numbers of the selected element or elements, counting from 0. If nothing is selected, returns an empty tuple. 

        .. py:method:: delete(first, last=None)

                Deletes the lines whose indices are in the range [first, last], inclusive (contrary to the usual Python idiom, where deletion stops short of the last index), counting from 0. If the second argument is omitted, the single line with index first is deleted. 

        .. py:method:: get(first, last=None)

                Returns a tuple containing the text of the lines with indices from first to last, inclusive. If the second argument is omitted, returns the text of the line closest to first. 

        .. py:method:: index(i)

                If possible, positions the visible part of the listbox so that the line containing index i is at the top of the widget. 

        .. py:method:: insert(index, *elements)

                Insert one or more new lines into the listbox before the line specified by index. Use tk.END as the first argument if you want to add new lines to the end of the listbox. 

        .. py:method:: itemcget(index, option)

                Retrieves one of the option values for a specific line in the listbox. For option values, see itemconfig below. If the given option has not been set for the given line, the returned value will be an empty string. 

        .. py:method:: itemconfig(index, option=value, ...)

                Change a configuration option for the line specified by index. Option names include:

                        background

                                The background color of the given line. 

                        foreground

                                The text color of the given line. 

                        selectbackground

                                The background color of the given line when it is selected. 

                        selectforeground

                                The text color of the given line when it is selected. 

        .. py:method:: nearest(y)

                Return the index of the visible line closest to the y-coordinate y relative to the listbox widget. 

        .. py:method:: scan_dragto(x, y)

                See scan_mark below. 

        .. py:method:: scan_mark(x, y)

                Use this method to implement scanning—fast steady scrolling—of a listbox. To get this feature, bind some mouse button event to a handler that calls scan_mark with the current mouse position. Then bind the <Motion> event to a handler that calls scan_dragto with the current mouse position, and the listbox will be scrolled at a rate proportional to the distance between the position recorded by scan_mark and the current position. 

        .. py:method:: see(index)

                Adjust the position of the listbox so that the line referred to by index is visible. 

        .. py:method:: selection_anchor(index)

                Place the “selection anchor” on the line selected by the index argument. Once this anchor has been placed, you can refer to it with the special index form tk.ANCHOR.

                For example, for a listbox named lbox, this sequence would select lines 3, 4, and 5:

                        lbox.selection_anchor(3)
                        lbox.selection_set(tk.ANCHOR,5)


        .. py:method:: selection_clear(first, last=None)

                Unselects all of the lines between indices first and last, inclusive. If the second argument is omitted, unselects the line with index first. 

        .. py:method:: selection_includes(index)

                Returns 1 if the line with the given index is selected, else returns 0. 

        .. py:method:: selection_set(first, last=None)

                Selects all of the lines between indices first and last, inclusive. If the second argument is omitted, selects the line with index first. 

        .. py:method:: size()

                Returns the number of lines in the listbox. 

        .. py:method:: xview()

                To make the listbox horizontally scrollable, set the command option of the associated horizontal scrollbar to this method. See Section 14.1, “Scrolling a Listbox widget”. 

        .. py:method:: xview_moveto(fraction)

                Scroll the listbox so that the leftmost fraction of the width of its longest line is outside the left side of the listbox. Fraction is in the range [0,1]. 

        .. py:method:: xview_scroll(number, what)

                Scrolls the listbox horizontally. For the what argument, use either tk.UNITS to scroll by characters, or tk.PAGES to scroll by pages, that is, by the width of the listbox. The number argument tells how many to scroll; negative values move the text to the right within the listbox, positive values leftward. 

        .. py:method:: yview()

                To make the listbox vertically scrollable, set the command option of the associated vertical scrollbar to this method. See Section 14.1, “Scrolling a Listbox widget”. 

        .. py:method:: yview_moveto(fraction)

                Scroll the listbox so that the top fraction of the width of its longest line is outside the left side of the listbox. Fraction is in the range [0,1]. 

        .. py:method:: yview_scroll(number, what)

                Scrolls the listbox vertically. For the what argument, use either tk.UNITS to scroll by lines, or tk.PAGES to scroll by pages, that is, by the height of the listbox. The number argument tells how many to scroll; negative values move the text downward inside the listbox, and positive values move the text up. 
                
Scrolling a Listbox widget
==========================

Here is a code fragment illustrating the creation and linking of a listbox to both a horizontal and a vertical scrollbar::

    self.yScroll = tk.Scrollbar(self, orient=tk.VERTICAL)
    self.yScroll.grid(row=0, column=1, sticky=tk.N+tk.S)

    self.xScroll = tk.Scrollbar(self, orient=tk.HORIZONTAL)
    self.xScroll.grid(row=1, column=0, sticky=tk.E+tk.W)

    self.listbox = tk.Listbox(self,
         xscrollcommand=self.xScroll.set,
         yscrollcommand=self.yScroll.set)
    self.listbox.grid(row=0, column=0, sticky=tk.N+tk.S+tk.E+tk.W)
    self.xScroll['command'] = self.listbox.xview
    self.yScroll['command'] = self.listbox.yview

