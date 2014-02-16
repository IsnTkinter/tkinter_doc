.. _MESSAGE:

**************************
``Message`` - Les Messages 
**************************

Ce widget est semblable au widget ``Label`` (voir :ref:`LABEL`), mais il est destiné à l'affichage des messages sur plusieurs lignes. Tout le texte sera affiché dans la même police, si vous avez besoin d'afficher du texte avec plusieurs polices, voir :ref:`TEXT`.

Pour créer un nouveau message comme enfant d'une fenêtre ou d'un cadre nommé ``parent``:

.. py:class:: Message(parent, option, ...)

        Le constructeur renvoie le nouveau widget ``Message``. Ses options sont:

        :arg aspect: 
                Utilisez cette option pour spécifier le rapport largeur sur hauteur en pourcentage. Par exemple, ``aspect=100`` vous donnerait un message en forme de texte dans un carré; avec ``aspect=200``, la zone de texte serait deux fois plus large que haute. La valeur par défaut est 150, c'est-à-dire que le texte apparaît dans une boîte 50% plus large que haute.
        :arg bg: 
                (ou **background**) La couleur de fond derrière le texte, voir :ref:`couleurs`.
        :arg bd: 
                (ou **borderwidth**) Largeur de la bordure autour du widget, voir :ref:`dimensions`. La valeur par défaut est de deux pixels. Cette option est visible uniquement lorsque l'option de relief n'est pas ``'flat'``.
        :arg cursor: 
                Définit le curseur qui s'affiche lorsque la souris est sur le widget, voir :ref:`pointeurs`.
        :arg font: 
                Définit la police utilisée pour afficher le texte dans le widget, voir :ref:`polices`.
        :arg fg: 
                (ou **foreground**) Définit la couleur du texte; voir :ref:`couleurs`.
        :arg highlightbackground: 
                Couleur de mise en valeur du focus quand le widget l’a perdu. Voir :ref:`FOCUS`.
        :arg highlightcolor:
                Couleur de mise en valeur du focus quand le widget l’a obtenu.
        :arg highlightthickness:
                Épaisseur de la ligne de mise en valeur du focus.
        :arg justify: 
                Définit l’alignement de plusieurs lignes de texte: ``'left'`` pour un alignement à gauche, ``'center'`` pour centrer et ``'right'`` pour un alignement à droite.
        :arg padx: 
                Espace horizontal supplémentaire à insérer à gauche et à droite dans l’étiquette. Sa valeur est en pixels.
        :arg pady: 
                Espace vertical supplémentaire à insérer au-dessus et en dessous dans l’étiquette. Sa valeur est en pixels.
        :arg relief: 
                Précise l’apparence de la bordure décorative autour de l’étiquette. Par défaut, vaut ``'flat'``; pour d’autres valeurs, voir :ref:`reliefs`.
        :arg takefocus: 
                Normalement, un message n’obtient pas le focus; voir :ref:`FOCUS`. Utilisez ``takefocus=True`` pour ajouter le widget à la liste de traversée du focus.
        :arg text: 
                La valeur de cette option est le texte qui doit être affiché à l'intérieur du widget.
        :arg textvariable: 
                Pour pouvoir faire varier le texte affiché en même temps que la valeur d’une variable de contrôle de type ``StringVar``, régler cette option avec cette variable. Voir :ref:`CTRLVARIABLES`. La valeur de cette variable est le texte à afficher. Si vous spécifiez les options **text** et **textvariable**, l'option **text** est ignorée.
        :arg width: 
                Utilisez cette option pour spécifier la largeur de la zone de texte dans le widget, en pixels. La largeur par défaut dépend du texte affiché et de la valeur de l'option aspect.
