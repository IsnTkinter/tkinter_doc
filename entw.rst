.. _SAISIE:

******************************
Les boîtes de saisie ``Entry``
******************************

Une boîte de saisie ``Entry`` est utile pour permettre à l'utilisateur de modifier une ligne de texte.

* Si vous souhaitez afficher plusieurs lignes de textes modifiables,voir “The Text widget”.

* Si vous souhaitez afficher une ou plusieurs lignes de textes qui ne peuvent pas être directement modifiées par l'utilisateur, voir :ref:`Label`.

Quelques définitions:

* La sélection est la région du texte mise en valeur (surlignement) dans une boîte de saisie, s'il y en a une.

* Typiquement, la selection est réalisé par l'utilisateur avec la souris, et le texte sélectionné est copié dans le  presse-papiers du système. Cependant, Tkinter vous permet de choisir si oui ou non, la sélection est copié dans le presse-papiers. Vous pouvez aussi réaliser des sélections contrôlées par le programme.

* Le curseur d'insertion indique où le texte sera inséré. Il est affiché lorsque l'utilisateur clique sur la boîte saisie. Il apparaît normalement comme une ligne verticale qui clignote dans le composant. Vous pouvez régler finement son apparence de plusieurs façons.

* Les positions à l'intérieur du texte affiché dans la boîte sont précisées à l'aide d'un index. Il y a plusieurs façons d'exprimer un index:

  - En utilisant un entier qui débute à 0 comme pour les chaînes de caractère de Python.

  - La constante ``'end'`` qui se réfère à la position située après le texte.

  - La constante ``'insert'`` qui se réfère à la position courante du curseur d'insertion.

  - La constante ``'anchor'`` qui se réfère au premier caractère de la sélection courante, s'il y en a une.

  - Vous pouvez avoir besoin de récupérer le caractère qui se trouve à une position déterminée par la souris. Pour simplifier cela, vous pouvez utiliser un index à l'aide d'une chaîne de caractères de la forme ``'@n'`` où n est la distance horizontale en pixels entre le côté gauche de la boîte de saisie et la souris. Un tel index déterminera le caractère situé à cette distance horizontale du côté gauche de la boîte.

Pour créer une nouvelle boîte de saisie dans une fenêtre principale ou dans un cadre ``parent``:

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
                Pour pouvoir récupérer le texte courant de la boîte de saisie, vous devez configurer cette option avec une instance de ``StringVar``; voir “Control variables: the values behind the widgets”. Vous pouvez alors récupérer ou modifier le texte en utilisant les méthodes ``get()`` ou ``set()`` de cette variable de contrôle ``StringVar``.
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

Pour pouvoir faire défiler le contenu d'une boîte de saisie, il faudra ajouter un peu de code en plus afin d'adapter la fonction de rappel d'une barre de défilement ``Scrollbar`` aux méthodes fournies par la boîte de saisie. Voici quelques fragments de code qui illustre un tel réglage. Premièrement, la création et la liaison de la barre de défilement et de la boîte de saisie::

    entry = Entry(root, width=10)
    entry.grid(row=0, sticky='ew')

    entryScroll = Scrollbar(root, orient='horizontal',
        command=scrollHandler)
    entryScroll.grid(row=1, sticky='ew')
    entry['xscrollcommand'] = entryScroll.set

Ensuite, la définition de la fonction de rappel du code précédent::

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

Dans certaines applications, vous souhaiterez vérifier le contenu d'une boîte de saisie pour vous assurez qu'il est valide selon certains critères nécessaires au bon fonctionnement de votre application. Pour préciser ce qui est valide, vous définirez une fonction de rappel qui vérifiera ce contenu et signalera s'il est oui ou non valide.

Voici la procédure à suivre pour mettre en oeuvre une telle validation.

* Écrire une fonction de rappel qui vérifie le contenu de la boîte saisie et retourne ``True`` s'il est considéré comme valide, ou ``False`` sinon. Si la fonction de rappel retourne ``False``, les tentatives de l'utilisateur pour modifier le contenu de la boîte de saisie seront refusées et le texte restera inchangé.

* Enregistrez cette fonction de rappel: cela consiste à produire un «emballage Tcl» autour de votre fonction Python.

  Supposez que votre fonction de rappel soit ``estOk``. Pour pouvoir associer cette fonction à la boîte de saisie, vous devez utilisez la méthode universelle (valable pour tout widget) ``register(estOk)``. Cette méthode crée «l'emballage Tcl» voulu et retourne une chaîne de caractères que tkinter peut utiliser pour appeler votre fonction.

* Lorsque vous appelez le constructeur de la boîte de saisie ``Entry``, utilisez son option **validatecommand** pour préciser votre fonction de validation (par l'intermédiaire de la chaîne retournée par ``register()``, et utilisez son option **validate** pour préciser les circonstances de l'appel de la fonction de validation. Les valeurs de ces options sont discutées avec plus de détails ci-dessous.

Voici les valeurs admissibles pour l'option **validate** et leur signification.Here are the values of the validate option and what they mean.

``'focus'``

        La validation est déclenchée à chaque fois que la boîte de saisie obtient ou perd le focus (voir “Focus: routing keyboard input”). 

``'focusin'``

        Elle est déclenchée lorsque la boîte de saisie obtient le focus.

``'focusout'``

        Elle est déclenchée lorsque la boîte perd le focus.

``'key'``

        Elle est déclenchée à chaque fois que l'appui sur une touche modifie le contenu.

``'all'``

        Lorsque l'une quelconque des situations précédentes a lieu.

``'none'``

        Désactive la validation. C'est la valeur par défaut de l'option. Notez que c'est la chaîne de caractère 'none', non la valeur spéciale de Python ``None``. 

La valeur de l'option **validatecommand** dépend des arguments que vous souhaitez transmettre à la fonction de validation.option depends on what arguments you would like your callback to receive.

* Peut-être que la seule chose dont à besoin votre fonction de validation est le texte qui apparaît actuellement dans la boîte de saisie. Si c'est le cas, elle peut utiliser la méthode ``get()`` de la variable de contrôle qui a servi à configuer l'option **textvariable** de la boîte de saisie. Perhaps the only thing the callback needs to know is what text currently appears in the Entry. If that is the case, it can use the .get() method of the textvariable associated with the widget to retrieve that text.

  Dans ce cas, il suffit d'indiquer ``validatecommand=f``, où ``f`` est le nom de votre fonction de validation.

* Tkinter peut aussi fournir un certain nombre d'informations à votre fonction de validation. Si vous souhaitez utiliser cela, lors de l'appel du constructeur de la boîte de saisie, utilisez l'option ``validatecommand=(f, s1, s2, ...)``, où ``f`` est le nom «enregistré» de votre fonction de rappel, et chaque élément ``si`` additionnel un code de substitution. Pour chaque code de substitution fourni, la fonction de rappel reçoit un argument positionnel qui contient la valeur appropriée.

Voici les codes de substitution possibles.

Table 18. Callback substitution codes
'%d' 	Code d'action: 0 pour une tentative de suppression, 1 pour une tentative d'insertion ou -1 si l'appel a eu lieu par gain ou perte du focus, ou par modification de la variable de contrôle **textvariable**.
'%i' 	Lorque l'utilisateur tente d'insérer ou de supprimer du texte, cet argument sera la position (index) du début (cas d'une sélection) de l'insertion ou suppression. Si l'appel a eu lieu par gain ou perte de focus, ou par modification de la variable de contrôle **textvariable**, l'argument vaut -1.
'%P' 	La valeur que le texte aurait si la modification avait lieu.
'%s' 	Le texte dans la boîte de saisie avant le changement.
'%S' 	Si l'appel est du à une insertion ou une suppression, l'argument sera le texte à insérer ou à supprimer.
'%v' 	The current value of the widget's validate option.
'%V' 	La raison de l'appel, parmi: ``'focusin'``, ``'focusout'``, ``'key'``, ou ``'forced'`` si la variable de contrôle **textvariable** a été modifiée.
'%W' 	Le nom de la boîte de saisie.

Voici un petit exemple. Supposez que vous souhaitiez que votre fonction de validation reçoive le ``'%d'`` pour déterminer les circonstances de son appel; ``'%i'`` pour déterminer où l'ajout ou la suppresion doit avoir lieu; et ``'%S'`` pour déterminer ce qui doit être insérer ou supprimer. Votre fonction pourrait ressembler à cela::

    def estOK( pourquoi, ou, quoi):
        ...

Ensuite, vous utilisez la méthode universelle ``register()`` pour «emballer» cette fonction. Nous supposons que ``w`` est un widget arbitraire::

    okCommand = w.register(estOK)

Pour activer cette fonction de rappel, vous aurez besoin d'utiliser ces deux options du constructeur ``Entry``::

    saisi = Entry(root, validate='all',
         validatecommand=(okCommand, '%d', '%i', '%S'), ...)

Supposez que la boîte de saisie contienne actuellement la chaîne ``'abcdefg'``, et que l'utilisateur sélectionne ``'cde'`` puis appui sur la touche Retour Arrière. Il s'ensuivrait l'appelle estOK(0, 2, 'cde'): 0 pour indiquer la suppression, 2 pour la position avant le 'c' et 'cde' pour la chaîne à détruire. Si estOK() retourne True, le nouveau texte est ``'abfg'``; sinon, le texte est inchangé.

Le widget ``Entry`` possède aussi une option **invalidcommand** qui sert à préciser une fonction de rappel qui est appelée à chaque fois que la fonction de validation retourne False. Cette commande peut modifier le texte de la boîte de saisie en utilisant la méthode ``set()`` de la variable de contrôle qui a servi à configurer l'option ``textvariable``. Le réglage de cette option fonctionne de la même façon que celle de l'option **validatecommand**. Vous devez utiliser la méthode universelle ``register()`` pour envelopper votre fonction; cette méthode retourne le nom de la fonction envelopper sous la forme d'une chaîne de caractère. Ensuite, passez cette valeur à l'option **invalidcommand** soit directement, soit comme le premier élément d'un tuple qui contient les codes de substitutions qui vous intéresse.
