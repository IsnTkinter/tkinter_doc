.. _DIALOGS:

**************
Pop-up dialogs
**************

Tkinter provides three modules that can create pop-up dialog windows for you:

* Section 55.1, “The tkMessageBox dialogs module”, provides an assortment of common pop-ups for simple tasks.

* Section 55.2, “The tkFileDialog module”, allows the user to browse for files.

* Section 55.3, “The tkColorChooser module”, allows the user to select a color.
    
The tkMessageBox dialogs module
===============================

Once you import the tkMessageBox module, you can create any of these seven common types of pop-up menu by calling functions from this table.
Screen shot of askokcancel. 	.askokcancel(title, message, options)

.. list-table::
   :widths: 50 50
   :header-rows: 0

   * - Screen shot of askquestion. 
     - ``.askquestion(title, message, options)``
   * - Screen shot of askretrycancel. 
     - ``.askretrycancel(title, message, options)``
   * - Screen shot of askyesno. 
     - ``.askyesno(title, message, options)``
   * - Screen shot of showerror. 
     - ``.showerror(title, message, options)``
   * - Screen shot of showinfo. 
     - ``.showinfo(title, message, options)``
   * - Screen shot of showwarning. 
     - ``.showwarning(title, message, options)``

In each case, the title is a string to be displayed in the top of the window decoration. The message argument is a string that appears in the body of the pop-up window; within this string, lines are broken at newline ('\n') characters.

The option arguments may be any of these choices.

``default``

    Which button should be the default choice? If you do not specify this option, the first button (“OK”, “Yes”, or “Retry”) will be the default choice.

    To specify which button is the default choice, use default=C, where C is one of these constants defined in tkMessageBox: CANCEL, IGNORE, OK, NO, RETRY, or YES. 

``icon``

    Selects which icon appears in the pop-up. Use an argument of the form icon=I where I is one of these constants defined in tkMessageBox: ERROR, INFO, QUESTION, or WARNING. 

``parent``

    If you don't specify this option, the pop-up appears above your root window. To make the pop-up appear above some child window W, use the argument parent=W. 

Each of the “ask...” pop-up functions returns a value that depends on which button the user pushed to remove the pop-up.

* askokcancel, askretrycancel, and askyesno all return a bool value: True for “OK” or “Yes” choices, False for “No” or “Cancel” choices.

* askquestion returns u'yes' for “Yes”, or u'no' for “No”.
    
The tkFileDialog module
=======================

The tkFileDialog module provides two different pop-up windows you can use to give the user the ability to find existing files or create new files.

.. py:method:: skopenfilename(option=value, ...)

    Intended for cases where the user wants to select an existing file. If the user selects a nonexistent file, a popup will appear informing them that the selected file does not exist. 

.. py:method:: sksaveasfilename(option=value, ...)

    Intended for cases where the user wants to create a new file or replace an existing file. If the user selects an existing file, a pop-up will appear informing that the file already exists, and asking if they really want to replace it. 

The arguments to both functions are the same:

``defaultextension=s``

    The default file extension, a string starting with a period ('.'). If the user's reply contains a period, this argument has no effect. It is appended to the user's reply in case there are no periods.

    For example, if you supply a defaultextension='.jpg' argument and the user enters 'gojiro', the returned file name will be 'gojiro.jpg'. 

``filetypes=[(label1, pattern1), (label2, pattern2), ...]``

    A list of two-element tuples containing file type names and patterns that will select what appears in the file listing. In the screen picture below, note the pull-down menu labeled “Files of type:”. The filetypes argument you supply will populate this pull-down list. Each pattern is a file type name (“PNG” in the example) and a pattern that selects files of a given type (“(\*.png)” in the example). 

``initialdir=D``

    The path name of the directory to be displayed initially. The default directory is the current working directory. 

``initialfile=F``

    The file name to be displayed initially in the “File name:” field, if any. 

``parent=W``

    To make the pop-up appear over some window W, supply this argument. The default behavior is that the pop-up will appear over your application's root window. 

``title=T``

    If specified, T is a string to be displayed as the pop-up window's title. 

If the user selects a file, the returned value is the complete path name of the selected file. If the user uses the Cancel button, the function returns an empty string.

Here is an example:

The tkColorChooser module
=========================

To give your application's user a popup they can use to select a color, import the tkColorChooser module and call this function:

.. code-block:: python

        result = tkColorChooser.askcolor(color, option=value, ...)

Arguments are:

``color``

    The initial color to be displayed. The default initial color is a light gray. 

``title=text``

    The specified text appears in the pop-up window's title area. The default title is “Color”. 

``parent=W``

    Make the popup appear over window W. The default behavior is that it appears over your root window. 

If the user clicks the OK button on the pop-up, the returned value will be a tuple `(triple, color)`, where triple is a tuple (R, G, B) containing red, green, and blue values in the range [0,255] respectively, and color is the selected color as a regular Tkinter color object.

If the users clicks Cancel, this function will return (None, None).

Here's what the popup looks like on the author's system:

