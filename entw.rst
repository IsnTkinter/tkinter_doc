.. _SAISIE:

******************************
Les boîtes de saisie ``Entry``
******************************

Une boîte de saisie ``Entry`` est utile pour permettre à l'utilisateur de modifier une ligne de texte.The purpose of an Entry widget is to let the user see and modify a single line of text.

* Si vous souhaitez afficher plusieurs lignes de textes modifiables, If you want to display multiple lines of text that can be edited, voir “The Text widget”.

* Si vous souhaitez afficher une ou plusieurs lignes de textes qui ne peuvent pas être directement modifiées par l'utilisateur, If you want to display one or more lines of text that cannot be modified by the user, Voir :ref:`Label`.

Quelques définitions:

* La sélection est la région du texte mise en valeur (surlignement) dans une boîte de saisie, s'il y en a une.The selection is a highlighted region of the text in an Entry widget, if there is one.

* Typiquement, la selection est réalisé par l'utilisateur avec la souris, et le texte sélectionné est copié dans le  Typically the selection is made by the user with the mouse, and selected text is copied to the system's clipboard. Cependant, Tkinter vous permet de choisir si oui ou non, la sélection est copié. Vous pouvez aussi réaliser des sélections contrôlé par le programme. However, Tkinter allows you to control whether or not selected text gets copied to the clipboard. You can also select text in an Entry under program control.

* Le curseur d'insertion indique où le texte sera inséré. Il est affiché lorsque l'utilisateur clique sur la boîte saisie. Il apparaît normalement comme une ligne verticale qui clignote dans le composant. Vous pouvez régler finement son apparence de plusieurs façons.The insertion cursor shows where new text will be inserted. It is displayed only when the user clicks the mouse somewhere in the widget. It usually appears as a blinking vertical line inside the widget. You can customize its appearance in several ways.

* Les positions à l'intérieur du texte affiché dans la boîte sont précisées à l'aide d'un index. Il y a plusieurs façons d'exprimer un index:Positions within the widget's displayed text are given as an index. There are several ways to specify an index:

  - En utilisant un entier qui débute en 0 comme pour les chaînes de caractère de Python.As normal Python indexes, starting from 0.

  - La constante ``'end'`` qui se réfère à la position située après le texte en cours.The constant tk.END refers to the position after the existing text.

  - La constante ``'insert'`` qui se réfère à la position courante du curseur d'insertion.The constant tk.INSERT refers to the current position of the insertion cursor.

  - La constante ``'anchor'`` qui se réfère au premier caractère de la sélection courante, s'il y en a une.The constant tk.ANCHOR refers to the first character of the selection, if there is a selection.

  - Vous pouvez avoir besoin de comprendre quel caractère se trouve à une position déterminée par la souris. Pour simplifier cela, vous pouvez utiliser un index à l'aide d'une chaîne de caractères de la forme ``'@n'`` où n est la distance horizontale en pixels entre le côté gauche de la boîte de saisie et la souris. Un tel index déterminera le caractère situé à cette distance horizontale du côté gauche de la boîte. You may need to figure out which character position in the widget corresponds to a given mouse position. To simplify that process, you can use as an index a string of the form '@n', where n is the horizontal distance in pixels between the left edge of the Entry widget and the mouse. Such an index will specify the character at that horizontal mouse position. 

Pour créer une nouvelle boîte de saisie dans une fenêtre principale ou dans un cadre ``parent``:To create a new Entry widget in a root window or frame named parent:

.. py:class:: Entry(parent, option, ...)

        Ce constructeur retourne la nouvelle boîte de saisie. Ses options incluent:This constructor returns the new Entry widget. Options include:

        :arg bg:
                (ou **background**) La couleur de fond de la zone de saisie. C'est un gris légé par défaut.round color inside the entry area. Default is a light gray.
        :arg bd: 
                (ou borderwidth) L'épaisseur de la bordure qui entoure la zone de saisie. The width of the border around the entry area; Voir :ref:`dimensions`. Sa valeur est 2 pixels par défaut.
                The default is two pixels.
        :arg cursor:
                The cursor used when the mouse is within the entry widget; Voir :ref:`pointeurs`.
        :arg disabledbackground: 
                The background color to be displayed when the widget is in the tk.DISABLED state. For option values, see bg above.
        :arg disabledforeground: 
                The foreground color to be displayed when the widget is in the tk.DISABLED state. For option values, see fg below.
        :arg exportselection: 
                Par défaut, si vous sélectionnez du texte, il est automatiquement exporté vers le presse-papiers. Pour empêcher cela, utiliser ``exportselection=0``.By default, if you select text within an Entry widget, it is automatically exported to the clipboard. To avoid this exportation, use exportselection=0.
        :arg fg: or foreground
                The color used to render the text. Default is black.
        :arg font:
                The font used for text entered in the widget by the user. Voir :ref:`polices`.
        :arg highlightbackground:
                Color of the focus highlight when the widget does not have focus. See Section 52, “Focus: routing keyboard input”.
        :arg highlightcolor:
                Color shown in the focus highlight when the widget has the focus.
        :arg highlightthickness:
                Thickness of the focus highlight.
        :arg insertbackground:
                Par défaut, le curseur d'insertion (qui indique l'endroit où le texte sera inséré) est noir. Précisez une autre couleur si vous le souhaitez.By default, the insertion cursor (which shows the point within the text where new keyboard input will be inserted) is black. To get a different color of insertion cursor, set insertbackground to any color; Voir :ref:`couleurs`.
        :arg insertborderwidth:
                Par défaut, le curseur d'insertion est un simple rectangle. By default, the insertion cursor is a simple rectangle. Vous pouvez obtenir un effet de relief ``raised`` You can get the cursor with the tk.RAISED relief effect (Voir :ref:`reliefs`) en configurant cette option avec la dimension de la bordure 3-d. Si vous faites cela, assurez-vous que l'option insertwidth vaut au moins le double de cette valeur.by setting insertborderwidth to the dimension of the 3-d border. If you do, make sure that the insertwidth option is at least twice that value.
        :arg insertofftime:
                Par défaut, le curseur d'insertion clignote. Vous pouvez configurez cette option à une valeur en millisecondes pour préciser la durée de sa disparition dans le clignotement. La valeur par défaut est 300. Si vous utilisez ``insertofftime=0``, le curseur ne clignotera plus du tout.By default, the insertion cursor blinks. You can set insertofftime to a value in milliseconds to specify how much time the insertion cursor spends off. Default is 300. If you use insertofftime=0, the insertion cursor won't blink at all.
        :arg insertontime:
                Similaire à l'option insertofftime: durée de son apparition dans le clignotement. 600 millisecondes par défaut.Similar to insertofftime, this option specifies how much time the cursor spends on per blink. Default is 600 (milliseconds).
        :arg insertwidth:
                Normalement, le curseur d'insertion fait 2 pixels de large. Vous pouvez ajuster cela en indiquant une dimension arbitraire.By default, the insertion cursor is 2 pixels wide. You can adjust this by setting insertwidth to any dimension.
        :arg justify:
                This option controls how the text is justified when the text doesn't fill the widget's width. The value can be tk.LEFT (the default), tk.CENTER, or tk.RIGHT.
        :arg readonlybackground: 
                The background color to be displayed when the widget's state option is 'readonly'.
        :arg relief:
                Selects three-dimensional shading effects around the text entry. Voir :ref:`reliefs`.
                The default is relief=tk.SUNKEN.
        :arg selectbackground:
                La couleur de fond utilisée pour le texte sélectionnée.he background color to use displaying selected text. Voir :ref:`couleurs`.
        :arg selectborderwidth:
                La largeur de la bordure qui entoure le texte sélectionné. 1 pixel par défaut.The width of the border to use around selected text. The default is one pixel.
        :arg selectforeground:
                La couleur du texte sélectionné.The foreground (text) color of selected text.
        :arg show:
                Normalement, le texte que l'utilisateur saisie apparaît dans la zone de saisie. Pour une saisie de type mot de passe, indiquer le caractère de remplacement à afficher, souvent show='*'.Normally, the characters that the user types appear in the entry. To make a “password” entry that echoes each character as an asterisk, set show='*'.
        :arg state:
                Use this option to disable the Entry widget so that the user can't type anything into it. Use state=tk.DISABLED to disable the widget, state=tk.NORMAL to allow user input again. Your program can also find out whether the cursor is currently over the widget by interrogating this option; it will have the value tk.ACTIVE when the mouse is over it. You can also set this option to 'disabled', which is like the tk.DISABLED state, but the contents of the widget can still be selected or copied.
        :arg takefocus:
                By default, the focus will tab through entry widgets. Set this option to 0 to take the widget out of the sequence. For a discussion of focus, see Section 53, “Focus: routing keyboard input”.
        :arg textvariable:
                In order to be able to retrieve the current text from your entry widget, you must set this option to an instance of the StringVar class; see Section 52, “Control variables: the values behind the widgets”. You can retrieve the text using v.get(), or set it using v.set(), where v is the associated control variable.
        :arg validate: 
                Vous pouvez utiliser cette option pour indiquer que la boîte utilise une fonction de validation qui sera appelée automatiquement à certains instants. You can use this option to set up the widget so that its contents are checked by a validation function at certain times. Voir :ref:`validation`.
        :arg validatecommand: 
                Une fonction de validation pour la boîte de saisie.A callback that validates the text of the widget. Voir :ref:`validation`.
        :arg width:
                The size of the entry in characters. The default is 20. For proportional fonts, the physical length of the widget will be based on the average width of a character times the value of the width option.
        :arg xscrollcommand:
                If you expect that users will often enter more text than the onscreen size of the widget, you can link your entry widget to a scrollbar. Set this option to the .set method of the scrollbar. For more information, see Section 10.1, “Scrolling an Entry widget”.

        Les méthodes disponibles pour les boîtes de saisie ``Entry`` incluent:Methods on Entry objects include:


        .. py:method:: delete(first, last=None)

                Supprime les caractères de la position ``first`` jusqu'à, mais sans inclure, la position ``last``. Si le deuxième argument n'est pas précisé, seul le caractère à la position ``first`` est supprimé. sans inclure le caractère Deletes characters from the widget, starting with the one at index first, up to but not including the character at position last. If the second argument is omitted, only the single character at position first is deleted. 

        .. py:method:: get()

                Retourne le texte que contient la boîte de saisie lors de son appel.eturns the entry's current text as a string. 

        .. py:method:: icursor(index)

                Déplace le curseur d'instruction juste avant le caractère ayant la position ``index``.Set the insertion cursor just before the character at the given index. 

        .. py:method:: index(index)

                Fait défiler le contenu de la boîte de saisie de telle sorte que le caractère de position index soit à la première position visible à gauche. N'a pas d'effet si le texte tient tout entier dans la boîte de saisie.Shift the contents of the entry so that the character at the given index is the leftmost visible character. Has no effect if the text fits entirely within the entry. 

        .. py:method:: insert(index, s)

                Insère la chaîne de caractères ``s`` juste avant le caractère situé à la position ``index``.Inserts string s before the character at the given index. 

        .. py:method:: scan_dragto(x)

                Voir la méthode scan_mark ci-dessous. 

        .. py:method:: scan_mark(x)

                Use this option to set up fast scanning of the contents of the Entry widget that has a scrollbar that supports horizontal scrolling.

                To implement this feature, bind the mouse's button-down event to a handler that calls scan_mark(x), where x is the current mouse x position. Then bind the <Motion> event to a handler that calls scan_dragto(x), where x is the current mouse x position. The scan_dragto method scrolls the contents of the Entry widget continuously at a rate proportional to the horizontal distance between the position at the time of the scan_mark call and the current position. 

        .. py:method:: select_adjust(index)

                This method is used to make sure that the selection includes the character at the specified index. If the selection already includes that character, nothing happens. If not, the selection is expanded from its current position (if any) to include position index. 

        .. py:method:: select_clear()

                Efface la sélection (sans supprimé son contenu). N'a pas d'effet si il n'y a aucune sélection courante. If there isn't currently a selection, has no effect. 

        .. py:method:: select_from(index)

                Positionne l'index de l'ancre de sélection, 'anchor', à la position du caractère sélectionné par ``index`` et sélectionne ce caractère.Sets the tk.ANCHOR index position to the character selected by index, and selects that character. 

        .. py:method:: select_present()

                Retourne True s'il y a une sélection, False autrement.If there is a selection, returns true, else returns false. 

        .. py:method:: select_range(start, end)

                Pour régler la sélection depuis l'application. Sélectionne le texte de la position ``start`` jusqu'à, mais sans inclure, la position ``end``. la position ``start`` doit être avant la position ``end``. Sets the selection under program control. Selects the text starting at the start index, up to but not including the character at the end index. The start position must be before the end position.

                Pour sélectionner tout le texte de la boîte de saisie ``e``, utiliser ``e.select_range(0, 'end')``.To select all the text in an entry widget e, use e.select_range(0, tk.END). 

        .. py:method:: select_to(index)

                Selects all the text from the tk.ANCHOR position up to but not including the character at the given index. 

        .. py:method:: xview(index)

                Same as .xview(). This method is useful in linking the Entry widget to a horizontal scrollbar. Voir :ref:`Défilement`.

        .. py:method:: xview_moveto(f)

                Positions the text in the entry so that the character at position f, relative to the entire text, is positioned at the left edge of the window. The f argument must be in the range [0,1], where 0 means the left end of the text and 1 the right end. 

        .. py:method:: xview_scroll(number, what)

                Used to scroll the entry horizontally. The what argument must be either tk.UNITS, to scroll by character widths, or tk.PAGES, to scroll by chunks the size of the entry widget. The number is positive to scroll left to right, negative to scroll right to left. For example, for an entry widget e, e.xview_scroll(-1, tk.PAGES) would move the text one “page” to the right, and e.xview_scroll(4, tk.UNITS) would move the text four characters to the left. 

.. _Défilement:

Défilement du contenu
=====================

Pour pouvoir faire défiler le contenu d'une boîte de saisie, il faudra ajouter un peu de code en plus afin d'adapter la fonction de rappelle d'une barre de défilement ``Scrollbar`` aux méthodes fournies par la boîte de saisie. Voici quelques fragments de code qui illustre le réglage. Première, la création et la liaison de la barre de défilement et de la boîte de saisie.Making an Entry widget scrollable requires a little extra code on your part to adapt the Scrollbar widget's callback to the methods available on the Entry widget. Here are some code fragments illustrating the setup. First, the creation and linking of the Entry and Scrollbar widgets::

    entry = Entry(root, width=10)
    entry.grid(row=0, sticky='ew')

    entryScroll = Scrollbar(root, orient='horizontal',
        command=scrollHandler)
    entryScroll.grid(row=1, sticky='ew')
    entry['xscrollcommand'] = entryScroll.set

Voici la fonction de rappel du code précédent Here's the adapter function referred to above::

    def scrollHandler(L):
        op, howMany = L[0], L[1]

        if op == 'scroll':
            units = L[2]
            entry.xview_scroll(howMany, units)
        elif op == 'moveto':
            entry.xview_moveto(howMany)


.. _validation:

Gérer la validation
===================

In some applications, you will want to check the contents of an Entry widget to make sure they are valid according to some rule that your application must enforce. You define what is valid by writing a callback function that checks the contents and signals whether it is valid or not.

Here is the procedure for setting up validation on a widget.

* Write a callback function that checks the text in the Entry and returns True if the text is valid, or False if not. If the callback returns False, the user's attempt to edit the text will be refused, and the text will be unchanged.

* Register the callback function. In this step, you will produce a Tcl wrapper around a Python function.

* Suppose your callback function is a function named isOkay. To register this function, use the universal widget method .register(isOkay). This method returns a character string that Tkinter can use to call your function.

* When you call the Entry constructor, use the validatecommand option in the Entry constructor to specify your callback, and use the validate option to specify when the callback will be called to validate the text in the callback. The values of these options are discussed in more detail below. 

Here are the values of the validate option and what they mean.

``'focus'``

        Validate whenever the Entry widget gets or loses focus (see Section 53, “Focus: routing keyboard input”). 

``'focusin'``

        Validate whenever the widget gets focus. 

``'focusout'``

    Validate whenever the widget loses focus. 

``'key'``

    Validate whenever any keystroke changes the widget's contents. 

``'all'``

    Validate in all the above situations. 

``'none'``

    Turn off validation. This is the default option value. Note that this is the string 'none', not the special Python value None. 

The value of the validatecommand option depends on what arguments you would like your callback to receive.

* Perhaps the only thing the callback needs to know is what text currently appears in the Entry. If that is the case, it can use the .get() method of the textvariable associated with the widget to retrieve that text.

* In this case, all you need is the option “validatecommand=f”, where f is the name of your callback function.

* Tkinter can also provide a number of items of information to the callback. If you would like to use some of these items, when you call the Entry constructor, use the option validatecommand=(f, s1, s2, ...), where f is the name of your callback function, and each additional si is a substitution code. For each substitution code that you provide, the callback will receive a positional argument containing the appropriate value. 

Here are the substitution codes.

Table 18. Callback substitution codes
'%d' 	Action code: 0 for an attempted deletion, 1 for an attempted insertion, or -1 if the callback was called for focus in, focus out, or a change to the textvariable.
'%i' 	When the user attempts to insert or delete text, this argument will be the index of the beginning of the insertion or deletion. If the callback was due to focus in, focus out, or a change to the textvariable, the argument will be -1.
'%P' 	The value that the text will have if the change is allowed.
'%s' 	The text in the entry before the change.
'%S' 	If the call was due to an insertion or deletion, this argument will be the text being inserted or deleted.
'%v' 	The current value of the widget's validate option.
'%V' 	The reason for this callback: one of 'focusin', 'focusout', 'key', or 'forced' if the textvariable was changed.
'%W' 	The name of the widget.

Here is a small example. Suppose you want your callback to receive the '%d' to find out why it was called; '%i' to find out where the insertion or deletion would occur; and '%S' to find out what is to be inserted or deleted. Your method might look like this::

    def isOkay(self, why, where, what):
        ...

Next you use the universal .register() method to wrap this function. We assume that self is some widget::

    okayCommand = self.register(isOkay)

To set up this callback, you would use these two options in the Entry constructor::

    self.w = Entry(self, validate='all',
         validatecommand=(okayCommand, '%d', '%i', '%S'), ...)

Suppose that the Entry currently contains the string 'abcdefg', and the user selects 'cde' and then presses Backspace. This would result in a call isOkay(0, 2, 'cde'): 0 for deletion, 2 for the position before 'c', and 'cde' for the string to be deleted. If isOkay() returns True, the new text will be 'abfg'; if it returns False, the text will not change.

The Entry widget also supports an invalidcommand option that specifies a callback function that is called whenever the validatecommand returns False. This command may modify the text in the widget by using the .set() method on the widget's associated textvariable. Setting up this option works the same as setting up the validatecommand. You must use the .register() method to wrap your Python function; this method returns the name of the wrapped function as a string. Then you will pass as the value of the invalidcommand option either that string, or as the first element of a tuple containing substitution codes. 
