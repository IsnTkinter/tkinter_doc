***************
The Text widget
***************

Text widgets are a much more generalized method for handling multiple lines of text than the Label widget. Text widgets are pretty much a complete text editor in a window:

    You can mix text with different fonts, colors, and backgrounds.

    You can intersperse embedded images with text. An image is treated as a single character. See Section 24.3, “Text widget images”.

    An index is a way of describing a specific position between two characters of a text widget. See Section 24.1, “Text widget indices”.

    A text widget may contain invisible mark objects between character positions. See Section 24.2, “Text widget marks”.

    Text widgets allow you to define names for regions of the text called tags. You can change the appearance of a tagged region, changing its font, foreground and background colors, and other option. See Section 24.5, “Text widget tags”.

    You can bind events to a tagged region. See Section 54, “Events”.

    You can even embed a text widget in a “window” containing any Tkinter widget—even a frame widget containing other widgets. A window is also treated as a single character. See Section 24.4, “Text widget windows”. 

To create a text widget as the child of a root window or frame named parent:

.. py:class:: Text(parent, option, ...)

        The constructor returns the new Text widget. Options include:

        :arg autoseparators:
                If the undo option is set, the autoseparators option controls whether separators are automatically added to the undo stack after each insertion or deletion (if autoseparators=True) or not (if autoseparators=False). For an overview of the undo mechanism, see Section 24.7, “The Text widget undo/redo stack”.
        :arg bg: or background 
                The default background color of the text widget. See Section 5.3, “Colors”.
        :arg bd: or borderwidth
                The width of the border around the text widget; see Section 5.1, “Dimensions”. The default is two pixels.
        :arg cursor: 
                The cursor that will appear when the mouse is over the text widget. See Section 5.8, “Cursors”.
        :arg exportselection: 
                Normally, text selected within a text widget is exported to be the selection in the window manager. Set exportselection=0 if you don't want that behavior.
        :arg font: 
                The default font for text inserted into the widget. Note that you can have multiple fonts in the widgets by using tags to change the properties of some text. See Section 5.4, “Type fonts”.
        :arg fg: or foreground 
                The color used for text (and bitmaps) within the widget. You can change the color for tagged regions; this option is just the default.
        :arg height: 
                The height of the widget in lines (not pixels!), measured according to the current font size.
        :arg highlightbackground: 
                The color of the focus highlight when the text widget does not have focus. See Section 53, “Focus: routing keyboard input”.
        :arg highlightcolor: 
                The color of the focus highlight when the text widget has the focus.
        :arg highlightthickness: 
                The thickness of the focus highlight. Default is 1. Set highlightthickness=0 to suppress display of the focus highlight.
        :arg insertbackground: 
                The color of the insertion cursor. Default is black.
        :arg insertborderwidth: 
                Size of the 3-D border around the insertion cursor. Default is 0.
        :arg insertofftime: 
                The number of milliseconds the insertion cursor is off during its blink cycle. Set this option to zero to suppress blinking. Default is 300.
        :arg insertontime: 
                The number of milliseconds the insertion cursor is on during its blink cycle. Default is 600.
        :arg insertwidth: 
                Width of the insertion cursor (its height is determined by the tallest item in its line). Default is 2 pixels.
        :arg maxundo:
                This option sets the maximum number of operations retained on the undo stack. For an overview of the undo mechanism, see Section 24.7, “The Text widget undo/redo stack”. Set this option to -1 to specify an unlimited number of entries in the undo stack.
        :arg padx: 
                The size of the internal padding added to the left and right of the text area. Default is one pixel. For possible values, see Section 5.1, “Dimensions”.
        :arg pady: 
                The size of the internal padding added above and below the text area. Default is one pixel.
        :arg relief: 
                The 3-D appearance of the text widget. Default is relief=tk.SUNKEN; for other values, see Section 5.6, “Relief styles”.
        :arg selectbackground: 
                The background color to use displaying selected text.
        :arg selectborderwidth: 
                The width of the border to use around selected text.
        :arg selectforeground: 
                The foreground color to use displaying selected text.
        :arg spacing1: 
                This option specifies how much extra vertical space is put above each line of text. If a line wraps, this space is added only before the first line it occupies on the display. Default is 0.
        :arg spacing2: 
                This option specifies how much extra vertical space to add between displayed lines of text when a logical line wraps. Default is 0.
        :arg spacing3: 
                This option specifies how much extra vertical space is added below each line of text. If a line wraps, this space is added only after the last line it occupies on the display. Default is 0.
        :arg state: 
                Normally, text widgets respond to keyboard and mouse events; set state=tk.NORMAL to get this behavior. If you set state=tk.DISABLED, the text widget will not respond, and you won't be able to modify its contents programmatically either.
        :arg tabs: 
                This option controls how tab characters position text. See Section 24.6, “Setting tabs in a Text widget”.
        :arg takefocus: 
                Normally, focus will visit a text widget (see Section 53, “Focus: routing keyboard input”). Set takefocus=0 if you do not want focus in the widget.
        :arg undo:
                Set this option to True to enable the undo mechanism, or False to disable it. See Section 24.7, “The Text widget undo/redo stack”.
        :arg width: 
                The width of the widget in characters (not pixels!), measured according to the current font size.
        :arg wrap: 
                This option controls the display of lines that are too wide.

                With the default behavior, wrap=tk.CHAR, any line that gets too long will be broken at any character.

                Set wrap=tk.WORD and it will break the line after the last word that will fit.

                If you want to be able to create lines that are too long to fit in the window, set wrap=tk.NONE and provide a horizontal scrollbar. 

        :arg xscrollcommand: 
                To make the text widget horizontally scrollable, set this option to the .set method of the horizontal scrollbar.
        :arg yscrollcommand: 
                To make the text widget vertically scrollable, set this option to the .set method of the vertical scrollbar. 

Text widget indices
===================

An index is a general method of specifying a position in the content of a text widget. An index is a string with one of these forms:

'line.column'
        The position just before the given column (counting from zero) on the given line (counting from one). Examples: '1.0' is the position of the beginning of the text; '2.3' is the position before the fourth character of the second line. 

'line.end'
        The position just before the newline at the end of the given line (counting from one). So, for example, index '10.end' is the position at the end of the tenth line. 

tk.INSERT
        The position of the insertion cursor in the text widget. This constant is equal to the string 'insert'. 

tk.CURRENT
        The position of the character closest to the mouse pointer. This constant is equal to the string 'current'. 

tk.END
        The position after the last character of the text. This constant is equal to the string 'end'. 

tk.SEL_FIRST
        If some of the text in the widget is currently selection (as by dragging the mouse over it), this is the position before the start of the selection. If you try to use this index and nothing is selected, a tk.TclError exception will be raised. This constant is equal to the string 'sel.first'. 

tk.SEL_LAST
        The position after the end of the selection, if any. As with SEL_FIRST, you'll get a tk.TclError exception if you use such an index and there is no selection. This constant is equal to the string 'sel.last'. 

'markname'
        You can use a mark as an index; just pass its name where an index is expected. See Section 24.2, “Text widget marks”. 

'tag.first'
        The position before the first character of the region tagged with name tag; see Section 24.5, “Text widget tags”. 

'tag.last'
        The position after the last character of a tagged region. 

'@x,y'
        The position before the character closest to the coordinate (x, y). 

embedded-object
        If you have an image or window embedded in the text widget, you can use the PhotoImage, BitmapImage, or embedded widget as an index. See Section 24.3, “Text widget images” and Section 24.4, “Text widget windows”. 

In addition to the basic index options above, you can build arbitrary complex expressions by adding any of these suffixes to a basic index or index expression:

\+ n chars
        From the given index, move forward n characters. This operation will cross line boundaries.

        For example, suppose the first line looks like this:

        abcdef

        The index expression “1.0 + 5 chars” refers to the position between e and f. You can omit blanks and abbreviate keywords in these expressions if the result is unambiguous. This example could be abbreviated “1.0+5c”. 

\- n chars
        Similar to the previous form, but the position moves backwards n characters. 

\+ n lines
        Moves n lines past the given index. Tkinter tries to leave the new position in the same column as it was on the line it left, but if the line at the new position is shorter, the new position will be at the end of the line. 

\- n lines
        Moves n lines before the given index. 

linestart
        Moves to the position before the first character of the given index. For example, position “current linestart” refers to the beginning of the line closest to the mouse pointer. 

lineend
        Moves to the position after the last character of the given index. For example, position “sel.last lineend” refers to the end of the line containing the end of the current selection. 

wordstart
        The position before the beginning of the word containing the given index. For example, index “11.44 wordstart” refers to the position before the word containing position 44 on line 11.

        For the purposes of this operation, a word is either a string of consecutive letter, digit, or underbar (_) characters, or a single character that is none of these types.
    
Text widget marks
=================

A mark represents a floating position somewhere in the contents of a text widget.

    You handle each mark by giving it a name. This name can be any string that doesn't include whitespace or periods.

    There are two special marks. tk.INSERT is the current position of the insertion cursor, and tk.CURRENT is the position closest to the mouse cursor.

    Marks float along with the adjacent content. If you modify text somewhere away from a mark, the mark stays at the same position relative to its immediate neighbors.

    Marks have a property called gravity that controls what happens when you insert text at a mark. The default gravity is tk.RIGHT, which means that when new text is inserted at that mark, the mark stays after the end of the new text. If you set the gravity of a mark to tk.LEFT (using the text widget's .mark_gravity() method), the mark will stay at a position just before text newly inserted at that mark.

    Deleting the text all around a mark does not remove the mark. If you want to remove a mark, use the .mark_unset() method on the text widget. 

Refer to Section 24.8, “Methods on Text widgets”, below, to see how to use marks.

Text widget images
==================

You can put an image or bitmap into a text widget. It is treated as a single character whose size is the natural size of the object. See Section 5.9, “Images” andSection 5.7, “Bitmaps”.

Images are placed into the text widget by calling that widget's .image_create() method. See below for the calling sequence and other methods for image manipulation.

Images are manipulated by passing their name to methods on the text widget. You can give Tkinter a name for an image, or you can just let Tkinter generate a default name for that image.

An image may appear any number of times within the same Text widget. Each instance will carry a unique name. This names can be used as an index.

Text widget windows
===================

You can put any Tkinter widget—even a frame containing other widgets—into a text widget. For example, you can put a fully functional button or a set of radiobuttons into a text widget.

Use the .window_create() method on the text widget to add the embedded widget. For the calling sequence and related methods, see Section 24.8, “Methods on Text widgets”. 

Text widget tags
================

There are lots of ways to change both the appearance and functionality of the items in a text widget. For text, you can change the font, size, and color. Also, you can make text, widgets, or embedded images respond to keyboard or mouse actions.

To control these appearance and functional features, you associate each feature with a tag. You can then associate a tag with any number of pieces of text in the widget.

    The name of a tag can be any string that does not contain white space or periods.

    There is one special predefined tag called SEL. This is the region currently selected, if any.

    Since any character may be part of more than one tag, there is a tag stack that orders all the tags. Entries are added at the end of the tag list, and later entries have priority over earlier entries.

    So, for example, if there is a character c that is part of two tagged regions t1 and t2, and t1 is deeper in the tag stack than t2, and t1 wants the text to be green and t2 wants it to be blue, c will be rendered in blue because t2 has precedence over t1.

    You can change the ordering of tags in the tag stack. 

Tags are created by using the .tag_add() method on the text widget. See Section 24.8, “Methods on Text widgets”, below, for information on this and related methods.

Setting tabs in a Text widget
=============================

The tabs option for Text widgets gives you a number of ways to set tab stops within the widget.

    The default is to place tabs every eight characters.

    To set specific tab stops, set this option to a sequence of one or more distances. For example, setting tabs=('3c', '5c', '12c') would put tab stops 3, 5, and 12cm from the left side. Past the last tab you set, tabs have the same width as the distance between the last two existing tab stops. So, continuing our example, because 12c-5c is 7 cm, if the user keeps pressing the Tab key, the cursor would be positioned at 19cm, 26cm, 33cm, and so on.

    Normally, text after a tab character is aligned with its left edge on the tab stop, but you can include any of the keywords tk.LEFT, tk.RIGHT, tk.CENTER, or tk.NUMERIC in the list after a distance, and that will change the positioning of the text after each tab.

        A tk.LEFT tab stop has the default behavior.

        A tk.RIGHT tab stop will position the text so its right edge is on the stop.

        A tk.CENTER tab will center the following text on the tab stop.

        A tk.NUMERIC tab stop will place following text to the left of the stop up until the first period ('.') in the text—after that, the period will be centered on the stop, and the rest of the text will positioned to its right. 

    For example, setting tabs=('0.5i', '0.8i', tk.RIGHT, '1.2i', tk.CENTER, '2i', tk.NUMERIC) would set four tab stops: a left-aligned tab stop half an inch from the left side, a right-aligned tab stop 0.8″ from the left side, a center-aligned tab stop 1.2″ from the left, and a numeric-aligned tab stop 2″ from the left.
    
The Text widget undo/redo stack
===============================

The Text widget has a built-in mechanism that allows you to implement undo and redo operations that can cancel or reinstate changes to the text within the widget.

Here is how the undo/redo stack works:

    Every change to the content is recorded by pushing entries onto the stack that describe the change, whether an insertion or a deletion. These entries record the old state of the contents as well as the new state: if a deletion, the deleted text is recorded; if an insertion, the inserted text is recorded, along with a description of the location and whether it was an insertion or a deletion.

    Your program may also push a special record called a separator onto the stack.

    An undo operation changes the contents of the widget to what they were at some previous point. It does this by reversing all the changes pushed onto the undo/redo stack until it reaches a separator or until it runs out of stack.

    However, note that Tkinter also remembers how much of the stack was reversed in the undo operation, until some other editing operation changes the contents of the widget.

    A redo operation works only if no editing operation has occurred since the last undo operation. It re-applies all the undone operations. 

For the methods used to implement the undo/redo stack, see the .edit_redo, .edit_reset, .edit_separator, and .edit_undo methods in Section 24.8, “Methods on Text widgets”. The undo mechanism is not enabled by default; you must set the undo option in the widget.

Methods on Text widgets
=======================

These methods are available on all text widgets:

.. py:method:: Text.bbox(index)

            Returns the bounding box for the character at the given index, a 4-tuple (x, y, width, height). If the character is not visible, returns None. Note that this method may not return an accurate value unless you call the .update_idletasks() method (see Section 26, “Universal widget methods”). 

.. py:method:: Text.compare(index1, op, index2)

            Compares the positions of two indices in the text widget, and returns true if the relational op holds between index1 and index2. The op specifies what comparison to use, one of: '<', '<=', '==', '!=', '>=', or '>'.

            For example, for a text widget t, t.compare('2.0', '<=', END) returns true if the beginning of the second line is before or at the end of the text in t. 

.. py:method:: Text.delete(index1, index2=None)

            Deletes text starting just after index1. If the second argument is omitted, only one character is deleted. If a second index is given, deletion proceeds up to, but not including, the character after index2. Recall that indices sit between characters. 

.. py:method:: Text.dlineinfo(index)

            Returns a bounding box for the line that contains the given index. For the form of the bounding box, and a caution about updating idle tasks, see the definition of the .bbox method above. 

.. py:method:: Text.edit_modified(arg=None)

            Queries, sets, or clears the modified flag. This flag is used to track whether the contents of the widget have been changed. For example, if you are implementing a text editor in a Text widget, you might use the modified flag to determine whether the contents have changed since you last saved the contents to a file.

            When called with no argument, this method returns True if the modified flag has been set, False if it is clear. You can also explicitly set the modified flag by passing a True value to this method, or clear it by passing a False value.

            Any operation that inserts or deletes text, whether by program actions or user actions, or an undo or redo operation, will set the modified flag. 

.. py:method:: Text.edit_redo()

            Performs a redo operation. For details, see Section 24.7, “The Text widget undo/redo stack”. 

.. py:method:: Text.edit_reset()

            Clears the undo stack. 

.. py:method:: Text.edit_separator()

            Pushes a separator onto the undo stack. This separator limits the scope of a future undo operation to include only the changes pushed since the separator was pushed. For details, see Section 24.7, “The Text widget undo/redo stack”. 

.. py:method:: Text.edit_undo()

            Reverses all changes to the widget's contents made since the last separator was pushed on the undo stack, or all the way to the bottom of the stack if the stack contains no separators. For details, see Section 24.7, “The Text widget undo/redo stack”. It is an error if the undo stack is empty. 

.. py:method:: Text.image_create(index[, option=value, ...])

            This method inserts an image into the widget. The image is treated as just another character, whose size is the image's natural size.

            The options for this method are shown in the table below. You may pass either a series of option=value arguments, or a dictionary of option names and values.
            align	This option specifies how the image is to be aligned vertically if its height is less than the height of its containing line. Values may be top to align it at the top of its space; center to center it; bottom to place it at the bottom; or baseline to line up the bottom of the image with the text baseline.
            image	The image to be used. See Section 5.9, “Images”.
            name	You can assign a name to this instance of the image. If you omit this option, Tkinter will generate a unique name. If you create multiple instances of an image in the same Text widget, Tkinter will generate a unique name by appending a “#” followed by a number.
            padx	If supplied, this option is a number of pixels of extra space to be added on both sides of the image.
            pady	If supplied, this option is a number of pixels of extra space to be added above and below the image. 

.. py:method:: Text.get(index1, index2=None)

            Use this method to retrieve the current text from the widget. Retrieval starts at index index1. If the second argument is omitted, you get the character after index1. If you provide a second index, you get the text between those two indices. Embedded images and windows (widgets) are ignored. If the range includes multiple lines, they are separated by newline ('\n') characters. 

.. py:method:: Text.image_cget(index, option)

            To retrieve the current value of an option set on an embedded image, call this method with an index pointing to the image and the name of the option. 

.. py:method:: Text.image_configure(index, option, ...)

            To set one or more options on an embedded image, call this method with an index pointing to the image as the first argument, and one or more option=value pairs.

            If you specify no options, you will get back a dictionary defining all the options on the image, and the corresponding values. 

.. py:method:: Text.image_names()

            This method returns a tuple of the names of all the text widget's embedded images. 

.. py:method:: Text.index(i)

            For an index i, this method returns the equivalent position in the form 'line.char'. 

.. py:method:: Text.insert(index, text, tags=None)

            Inserts the given text at the given index.

            If you omit the tags argument, the newly inserted text will be tagged with any tags that apply to the characters both before and after the insertion point.

            If you want to apply one or more tags to the text you are inserting, provide as a third argument a tuple of tag strings. Any tags that apply to existing characters around the insertion point are ignored. Note: The third argument must be a tuple. If you supply a list argument, Tkinter will silently fail to apply the tags. If you supply a string, each character will be treated as a tag. 

.. py:method:: Text.mark_gravity(mark, gravity=None)

            Changes or queries the gravity of an existing mark; see Section 24.2, “Text widget marks”, above, for an explanation of gravity.

            To set the gravity, pass in the name of the mark, followed by either tk.LEFT or tk.RIGHT. To find the gravity of an existing mark, omit the second argument and the method returns tk.LEFT or tk.RIGHT. 

.. py:method:: Text.mark_names()

            Returns a sequence of the names of all the marks in the window, including tk.INSERT and tk.CURRENT. 

.. py:method:: Text.mark_next(index)

            Returns the name of the mark following the given index; if there are no following marks, the method returns an empty string.

            If the index is in numeric form, the method returns the first mark at that position. If the index is a mark, the method returns the next mark following that mark, which may be at the same numerical position. 

.. py:method:: Text.mark_previous(index)

            Returns the name of the mark preceding the given index. If there are no preceding marks, the method returns an empty string.

            If the index is in numeric form, the method returns returns the last mark at that position. If the index is a mark, the method returns the preceding mark, which may be at the same numerical position. 

.. py:method:: Text.mark_set(mark, index)

            If no mark with name mark exists, one is created with tk.RIGHT gravity and placed where index points. If the mark already exists, it is moved to the new location.

            This method may change the position of the tk.INSERT or tk.CURRENT indices. 

.. py:method:: Text.mark_unset(mark)

            Removes the named mark. This method cannot be used to remove the tk.INSERT or tk.CURRENT marks. 

.. py:method:: Text.scan_dragto(x, y)

            See .scan_mark, below. 

.. py:method:: Text.scan_mark(x, y)

            This method is used to implement fast scrolling of a Text widget. Typically, a user presses and holds a mouse button at some position in the widget, and then moves the mouse in the desired direction, and the widget moves in that direction at a rate proportional to the distance the mouse has moved since the button was depressed. The motion may be any combination of vertical or horizontal scrolling.

            To implement this feature, bind a mouse button down event to a handler that calls .scan_mark(x, y), where x and y are the current mouse position. Then bind the <Motion> event to a handler that calls .scan_dragto(x, y), where x and y are the new mouse position. 

.. py:method:: Text.search(pattern, index, option, ...)

            Searches for pattern (which can be either a string or a regular expression) in the buffer starting at the given index. If it succeeds, it returns an index of the 'line.char' form; if it fails, it returns an empty string.

            The allowable options for this method are:
            backwards 	Set this option to True to search backwards from the index. Default is forwards.
            count 	If you set this option to an IntVar control variable, when there is a match you can retrieve the length of the text that matched by using the .get() method on that variable after the method returns.
            exact	Set this option to True to search for text that exactly matches the pattern. This is the default option. Compare the regexp option below.
            forwards	Set this option to True to search forwards from the index. This is the default option.
            regexp 	Set this option to True to interpret the pattern as a Tcl-style regular expression. The default is to look for an exact match to pattern. Tcl regular expressions are a subset of Python regular expressions, supporting these features: . ^ [c1…] (…) * + ? e1|e2
            nocase 	Set this option to 1 to ignore case. The default is a case-sensitive search.
            stopindex 	To limit the search, set this option to the index beyond which the search should not go. 

.. py:method:: Text.see(index)

            If the text containing the given index is not visible, scroll the text until that text is visible. 

.. py:method:: Text.tag_add(tagName, index1, index2=None)

            This method associates the tag named tagName with a region of the contents starting just after index index1 and extending up to index index2. If you omit index2, only the character after index1 is tagged. 

.. py:method:: Text.tag_bind(tagName, sequence, func, add=None)

            This method binds an event to all the text tagged with tagName. See Section 54, “Events”, below, for more information on event bindings.

            To create a new binding for tagged text, use the first three arguments: sequence identifies the event, and func is the function you want it to call when that event happens.

            To add another binding to an existing tag, pass the same first three arguments and '+' as the fourth argument.

            To find out what bindings exist for a given sequence on a tag, pass only the first two arguments; the method returns the associated function.

            To find all the bindings for a given tag, pass only the first argument; the method returns a list of all the tag's sequence arguments. 

.. py:method:: Text.tag_cget(tagName, option)

            Use this method to retrieve the value of the given option for the given tagName. 

.. py:method:: Text.tag_config(tagName, option, ...)

            To change the value of options for the tag named tagName, pass in one or more option=value pairs.

            If you pass only one argument, you will get back a dictionary defining all the options and their values currently in force for the named tag.

            Here are the options for tag configuration:
            background 	The background color for text with this tag. Note that you can't use bg as an abbreviation.
            bgstipple 	To make the background appear grayish, set this option to one of the standard bitmap names (see Section 5.7, “Bitmaps”). This has no effect unless you also specify a background.
            borderwidth 	Width of the border around text with this tag. Default is 0. Note that you can't use bd as an abbreviation.
            fgstipple 	To make the text appear grayish, set this option a bitmap name.
            font 	The font used to display text with this tag. See Section 5.4, “Type fonts”.
            foreground 	The color used for text with this tag. Note that you can't use the fg abbreviation here.
            justify 	The justify option set on the first character of each line determines how that line is justified: tk.LEFT (the default), tk.CENTER, or tk.RIGHT.
            lmargin1 	How much to indent the first line of a chunk of text that has this tag. The default is 0. See Section 5.1, “Dimensions”for allowable values.
            lmargin2 	How much to indent successive lines of a chunk of text that has this tag. The default is 0.
            offset 	How much to raise (positive values) or lower (negative values) text with this tag relative to the baseline. Use this to get superscripts or subscripts, for example. For allowable values, see Section 5.1, “Dimensions”.
            overstrike 	Set overstrike=1 to draw a horizontal line through the center of text with this tag.
            relief 	Which 3-D effect to use for text with this tag. The default is relief=tk.FLAT; for other possible values see Section 5.6, “Relief styles”.
            rmargin 	Size of the right margin for chunks of text with this tag. Default is 0.
            spacing1 	This option specifies how much extra vertical space is put above each line of text with this tag. If a line wraps, this space is added only before the first line it occupies on the display. Default is 0.
            spacing2 	This option specifies how much extra vertical space to add between displayed lines of text with this tag when a logical line wraps. Default is 0.
            spacing3 	This option specifies how much extra vertical space is added below each line of text with this tag. If a line wraps, this space is added only after the last line it occupies on the display. Default is 0.
            tabs 	How tabs are expanded on lines with this tag. See Section 24.6, “Setting tabs in a Text widget”.
            underline 	Set underline=1 to underline text with this tag.
            wrap 	How long lines are wrapped in text with this tag. See the description of the wrap option for text widgets, above. 

.. py:method:: Text.tag_delete(tagName, ...)

            To delete one or more tags, pass their names to this method. Their options and bindings go away, and the tags are removed from all regions of text. 

.. py:method:: Text.tag_lower(tagName, belowThis=None)

            Use this method to change the order of tags in the tag stack (see Section 24.5, “Text widget tags”, above, for an explanation of the tag stack). If you pass two arguments, the tag with name tagName is moved to a position just below the tag with name belowThis. If you pass only one argument, that tag is moved to the bottom of the tag stack. 

.. py:method:: Text.tag_names(index=None)

            If you pass an index argument, this method returns a sequence of all the tag names that are associated with the character after that index. If you pass no argument, you get a sequence of all the tag names defined in the text widget. 

.. py:method:: Text.tag_nextrange(tagName, index1, index2=None)

            This method searches a given region for places where a tag named tagName starts. The region searched starts at index index1 and ends at index index2. If the index2 argument is omitted, the search goes all the way to the end of the text.

            If there is a place in the given region where that tag starts, the method returns a sequence [i0, i1], where i0 is the index of the first tagged character and i1 is the index of the position just after the last tagged character.

            If no tag starts are found in the region, the method returns an empty string. 

.. py:method:: Text.tag_prevrange(tagName, index1, index2=None)

            This method searches a given region for places where a tag named tagName starts. The region searched starts before index index1 and ends at index index2. If the index2 argument is omitted, the search goes all the way to the end of the text.

            The return values are as in .tag_nextrange(). 

.. py:method:: Text.tag_raise(tagName, aboveThis=None)

            Use this method to change the order of tags in the tag stack (see Section 24.5, “Text widget tags”, above, for an explanation of the tag stack). If you pass two arguments, the tag with name tagName is moved to a position just above the tag with name aboveThis. If you pass only one argument, that tag is moved to the top of the tag stack. 

.. py:method:: Text.tag_ranges(tagName)

            This method finds all the ranges of text in the widget that are tagged with name tagName, and returns a sequence [s0, e0, s1, e1, …], where each si is the index just before the first character of the range and ei is the index just after the last character of the range. 

.. py:method:: Text.tag_remove(tagName, index1, index2=None)

            Removes the tag named tagName from all characters between index1 and index2. If index2 is omitted, the tag is removed from the single character after index1. 

.. py:method:: Text.tag_unbind(tagName, sequence, funcid=None)

            Remove the event binding for the given sequence from the tag named tagName. If there are multiple handlers for this sequence and tag, you can remove only one handler by passing it as the third argument. 

.. py:method:: Text.window_cget(index, option)

            Returns the value of the given option for the embedded widget at the given index. 

.. py:method:: Text.window_configure(index, option)

            To change the value of options for embedded widget at the given index, pass in one or more option=value pairs.

            If you pass only one argument, you will get back a dictionary defining all the options and their values currently in force for the given widget. 

.. py:method:: Text.window_create(index, option, ...)

            This method creates a window where a widget can be embedded within a text widget. There are two ways to provide the embedded widget:

            you can use pass the widget to the window option in this method, or

            you can define a procedure that will create the widget and pass that procedure as a callback to the create option. 

            Options for .window_create() are:
            align 	Specifies how to position the embedded widget vertically in its line, if it isn't as tall as the text on the line. Values include: align=tk.CENTER (the default), which centers the widget vertically within the line; align=tk.TOP, which places the top of the image at the top of the line; align=tk.BOTTOM, which places the bottom of the image at the bottom of the line; and align=tk.BASELINE, which aligns the bottom of the image with the text baseline.
            create 	A procedure that will create the embedded widget on demand. This procedure takes no arguments and must create the widget as a child of the text widget and return the widget as its result.
            padx 	Extra space added to the left and right of the widget within the text line. Default is 0.
            pady 	Extra space added above and below the widget within the text line. Default is 0.
            stretch 	This option controls what happens when the line is higher than the embedded widget. Normally this option is 0, meaning that the embedded widget is left at its natural size. If you set stretch=1, the widget is stretched vertically to fill the height of the line, and the align option is ignored.
            window 	The widget to be embedded. This widget must be a child of the text widget. 

.. py:method:: Text.window_names()

            Returns a sequence containing the names of all embedded widgets. 

.. py:method:: Text.xview(tk.MOVETO, fraction)

            This method scrolls the text widget horizontally, and is intended for binding to the command option of a related horizontal scrollbar.

            This method can be called in two different ways. The first call positions the text at a value given by fraction, where 0.0 moves the text to its leftmost position and 1.0 to its rightmost position. 

.. py:method:: Text.xview(tk.SCROLL, n, what)

            The second call moves the text left or right: the what argument specifies how much to move and can be either tk.UNITS or tk.PAGES, and n tells how many characters or pages to move the text to the right relative to its image (or left, if negative). 

.. py:method:: Text.xview_moveto(fraction)

            This method scrolls the text in the same way as .xview(tk.MOVETO, fraction). 

.. py:method:: Text.xview_scroll(n, what)

            Same as .xview(tk.SCROLL, n, what). 

.. py:method:: Text.yview(tk.MOVETO, fraction)

            The vertical scrolling equivalent of .xview(tk.MOVETO,…). 

.. py:method:: Text.yview(tk.SCROLL, n, what)

            The vertical scrolling equivalent of .xview(tk.SCROLL,…). When scrolling vertically by tk.UNITS, the units are lines. 

.. py:method:: Text.yview_moveto(fraction)

            The vertical scrolling equivalent of .xview_moveto(). 

.. py:method:: Text.yview_scroll(n, what)

            The vertical scrolling equivalent of .xview_scroll(). 
    
