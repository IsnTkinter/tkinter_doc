.. _LISTBOX:

*********************
Le widget ``Listbox``
*********************

Un widget ``ListBox`` - liste de sélection - sert à présenter une liste de textes dans un cadre. Généralement, il s'agit de permettre à l'utilisateur de sélectionner une ou plusieurs lignes dans la liste. Toutes les lignes utilisent la même police de caractère. Si vous avez besoin de quelquechose qui ressemble plus à un éditeur de texte, reportez vous à “The Text widget”.

Pour créer un widget ``Listbox`` à l'intérieur d'une fenêtre mère ou d'un cadre désigné par ``parent``:

.. py:class:: Listbox(parent, option, ...)

        Ce constructeur retourne la nouvelle liste de sélection créée. Ses options incluent:

        :arg activestyle:
                Cette option sert à préciser l'apparence de la ligne active. Elle peut prendre l'une de ces valeurs: ``'underline'`` - la ligne active est souslignée (valeur par défaut) ; ``'dotbox'`` - La ligne active est mise en valeur par une ligne pointillée ; ``'none'`` - aucune mise en valeur.
        :arg bg: 
                (ou *background*) La couleur de fond de la liste de sélection.
        :arg bd: 
                (ou *borderwidth*) La largeur de la bordure de la liste de sélection. 2 pixels par défaut. Pour les valeurs possibles, voir :ref:`dimensions`.
        :arg cursor: 
                La cursor utilisée lorsque la souris survole le widget. Voir :ref:`pointeurs`.
        :arg disabledforeground: 
                La couleur du texte lorsque l'état du widget est ``'disabled'``.
        :arg exportselection: 
                Par défaut, l'utilisateur peut sélectionner le texte à la souris qui est alors copier dans le presse-papier. Pour désactiver ce comportement, utiliser ``exportselection=0``.
        :arg font: 
                La police de caractère utilisée pour le texte de la liste de sélection. Voir :ref:`polices`.
        :arg fg: 
                (ou *foreground*) La couleur utilisée pour le texte. Voir :ref:`couleurs`.
        :arg height: 
                Nombre de lignes (pas en pixels!) montrées dans la liste de sélection. 10 par défaut.
        :arg highlightbackground: 
                Couleur de la ligne de focus lorsque le widget ne l'a pas. Voir “Focus: routing keyboard input”.
        :arg highlightcolor: 
                Couleur de la ligne de focus lorsque le widget l'obtient.
        :arg highlightthickness: 
                Epaisseur de la ligne de focus.
        :arg listvariable:
                Une ``StringVar`` qui est associée à la liste de sélection dans son ensemble (Voir “Control variables: the values behind the widgets”. L'appel de la méthode get() de cette variable de contrôle retourne une chaîne de la forme ``"('t0', 't1', ...)"`` où chaque ti est le contenu d'une ligne de la boîte de sélection. Pour modifier toutes les lignes de la boîte, appelez la méthode set(s) sur la boîte, où s est une chaîne qui contient les valeurs de chaque ligne séparés avec des espaces entre elles. Par exemple, si ``listCon`` est une ``StringVar`` associé à l'option *listvariable* d'une boîte de sélection, l'appel ``listCon.set('un deux trois')`` remplira la boîte avec trois lignes et l'appel ``listCon.get()`` retournera ``"('un', 'deux', 'trois')"``.
        :arg relief: 
                Sert à régler le relief de la bordure. 'sunken' par défaut. Pour d'autres valeurs, voir :ref:`reliefs`.
        :arg selectbackground: 
                La couleur de fond utilisée pour la ligne sélectionnée.
        :arg selectborderwidth: 
                L'épaisseur de la bordure de la ligne de texte sélectionnée. 0 par défaut. Elle est utilisée pour produire un effet de relief 'raised' plus ou moins fort autour du texte sélectionné (Voir :ref:`reliefs`).
        :arg selectforeground: 
                La couleur du texte sélectionné.
        :arg selectmode:
                Détermine le nombre d'items qu'il est possible de sélectionner et la gestion du cliquer-glisser sur la sélection. 'browse' -  Valeur par défaut, le cliquer-glisser modifie la sélection. 'single' - Une seule ligne peut être sélectionné et il n'est pas possible de déplacer la sélection par cliquer-glissé. 'multiple' - Vous pouvez sélectionner plusieurs ligne à la fois. Le fait de cliquer sur une ligne déjà sélectionnée la déselectionne et vice versa. 'extended' - vous pouvez sélectionner des lignes adjacentes par cliquer-glissé. 
        :arg state: 
                Par défaut, une liste de sélection est dans l'état 'normal'. Pour désactiver la liste relativement à la souris, mettre la valeur 'disabled'.
        :arg takefocus: 
                Ce widget obtient le focus normalement. Mettre 0 pour sortir ce widget de le liste du traversée du focus. Voir “Focus: routing keyboard input”.
        :arg width: 
                La largeur du widget mesurée en caractères (non en pixels). La largeur effective est basée sur la largeur moyenne des caractères de la fonte utilisée. 20 par défaut.
        :arg xscrollcommand: 
                Si vous souhaitez que l'utilisateur puisse faire défiler la liste horizontalement, vous pouvez lier votre liste de sélection à une barre de défilement horizontale. Configurer cette option avec la méthode set() de la barre de défilement. Voir “Scrolling a Listbox widget” pour plus d'informations.
        :arg yscrollcommand: 
                Similaire à l'option précédente mais pour un défilement vertical.

        Les méthodes des listes de sélection utilisent fréquement des indexes:

        * If you specify an index as an integer, it refers to the line in the listbox with that index, counting from 0.

        * Index tk.END refers to the last line in the listbox.

        * Index tk.ACTIVE refers to the selected line. If the listbox allows multiple selections, it refers to the line that was last selected.

         * An index string of the form '@x,y' refers to the line closest to coordinate (x,y) relative to the widget's upper left corner. 

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

