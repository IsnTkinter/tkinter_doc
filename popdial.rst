.. _DIALOGS:

**********************************
Fenêtres surgissantes de dialogues
**********************************

Tkinter fourni trois sous modules qui servent à créer des fenêtres surgissantes de dialogue avec l'utilisateur:

* ``tkinter.messagebox``: fourni un assortiment de fenêtres de dialogues courantes pour des tâches simples. 

*  ``tkinter.filedialog``: fenêtre de navigation dans le système de fichier.

*  “The tkColorChooser module”, allows the user to select a color.
    
Le sous-module ``messagebox``
=============================

Après avoir importer le sous-module (avec ``from tkinter.messagebox import *`` ou plus prudemment avec ``import tkinter.messagebox as mb``), vous pouvez créer simplement huit sortes de fenêtres pop-ups en appelant les fonctions données ci-après.

.. list-table::
   :widths: 50 50
   :header-rows: 0

   * - .. image:: img/messagedialog/askokcancel.png 
     - ``askokcancel(title, message, options)``
   * - .. image:: img/messagedialog/askquestion.png
     - ``askquestion(title, message, options)``
   * - .. image:: img/messagedialog/askretrycancel.png
     - ``askretrycancel(title, message, options)``
   * - .. image:: img/messagedialog/askyesno.png
     - ``askyesno(title, message, options)``
   * - .. image:: img/messagedialog/askyesnocancel.png
     - ``askyesnocancel(title, messages, options)``
   * - .. image:: img/messagedialog/showerror.png
     - ``showerror(title, message, options)``
   * - .. image:: img/messagedialog/showinfo.png
     - ``showinfo(title, message, options)``
   * - .. image:: img/messagedialog/showwarning.png
     - ``showwarning(title, message, options)``

Dans chaque cas,l'argument *title* est une chaîne à afficher sur le bord haut de la fenêtre surgissante et l'argument *message* est une chaîne qui sera affichée dans le corps de la fenêtre; vous pouvez mettre des sauts de lignes en utlilisant le caractère spécial ``'\n'``.

Les options sont:

``default``

    Sert à indiquer le bouton qui représente le choix par défaut. Si vous ne précisez pas cette option, le premier bouton sera celui du choix par défaut.Which button should be the default choice? If you do not specify this option, the first button (“OK”, “Yes”, or “Retry”) will be the default choice.

    Pour préciser un bouton par défaut, utilisez ``default=C``, où c est l'une des valeurs ``"cancel"``, ``"ignore"``, ``"ok"``, ``"no"``, ``"retry"`` ou ``"yes"``.

``icon``

    Sert à sélectionner l'icone qui sera affichée sur la fenêtre de dialogue. Les valeurs possibles sont ``error``, ``info``, ``question`` ou ``warning``.

``parent``

    Si vous ne configurez pas cette option, la fenêtre surgissante apparaîtra au-dessus de votre fenêtre principale. Pour la faire apparaître au-dessus d'une fenêtre arbitraire ``w``, utilisez ``parent=w``.

Chacune des fonctions ``ask...`` retourne une valeur qui dépend du bouton sur lequel l'utilisateur a cliqué afin de supprimer la fenêtre surgissante.

* ``askokcancel``, ``askretrycancel``, et ``askyesno`` retournent toutes un booléen: ``True`` si l'utilisateur a cliqué sur le bouton "Ok", "Oui" ou "Ré-essayer", ``False`` s'il a cliqué sur "Non" ou sur "Annuler".

* ``askyesnocancel`` retourne ``True``, ``False``, ou ``None`` selon que l'utilisateur a cliqué sur le bouton "Oui", "Non" ou "Annuler".

* ``askquestion`` retourne une chaîne ``'yes'`` pour "Oui", ou ``'no'`` pour "Non".
    
Le sous-module ``filedialog``
=============================

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

