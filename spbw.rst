.. _SPINBOX:

***************************************
``Spinbox`` - Saisie/sélection rotative 
***************************************

Le widget ``Spinbox`` sert à donner un moyen à l'utilisateur de sélectionner une valeur parmi un ensemble de valeurs données ou d'en proposer une autre. Cet ensemble de valeurs peut être un intervalle de nombres ou un ensemble fixe de chaînes de caractères.

À l'écran, ce widget possède une zone de visualisation de la valeur courante ainsi qu'une paire de flèches.

* L'utilisateur peut cliquer sur les flèches de manière à passer d'une valeur à une autre. Si la valeur courante est à une extrémité de l'ensemble, vous pouvez configurer le widget de façon à ce que l'appui sur une flèche adéquate positionne la valeur située à l'autre extrémité.

* L'utilisateur peut aussi saisir une valeur directement dans la zone de visualisation de la valeur courante si le widget a le focus qu'il peut obtenir par clic sur la zone de visualisation/saisie. Voir :ref:`FOCUS`.

Pour créer un tel widget comme enfant d'une fenêtre ou d'un cadre nommé ``parent``:

.. py:class:: Spinbox(parent, option, ...)

        Ce constructeur retourne le nouveau widget Spinbox créé. Ses options incluent:

        :arg activebackground: 
                Couleur d'arrière plan utilisée lorsque la souris est au dessus du widget; voir :ref:`couleurs`.
        :arg bg:
                (ou **background**) Couleur d'arrière plan du widget.
        :arg bd:
                (ou **borderwidth**) Épaisseur de la bordure qui entoure le widget; voir :ref:`dimensions`. 1 pixel par défaut.
        :arg buttonbackground: 
                La couleur d'arrière plan utilisée pour les flèches. ``'gray'`` par défaut.
        :arg buttoncursor: 
                Le pointeur de souris à utiliser lorsque la souris est au dessus d'une flèche; voir :ref:`pointeurs`.
        :arg buttondownrelief: 
                Le style de relief utilisé pour l'effet d'enfoncement des flèches; voir :ref:`reliefs`. ``'raised'`` par défaut.
        :arg buttonup: 
                Le style de relief utilisé pour l'effet de relâchement des flèches. ``'raised'`` par défaut.
        :arg command: 
                Utilisez cette option pour préciser une fonction de rappel ou une méthode qui sera appelée lorsque l'utilisateur clique sur l'une des flèches. Notez que cette fonction n'est pas appelée lorsque l'utilisateur saisie la valeur directement.
        :arg cursor: 
                Le pointeur de souris qui est affiché lorsque la souris est située au-dessus de la zone de visualisation/saisie de la valeur.
        :arg disabledbackground: 
                Cette option et la suivante servent à préciser les couleurs d'arrière et d'avant plan utilisées lorsque le widget est dans l'état ``'disabled'``.
        :arg disabledforeground:
        :arg exportselection: 
                Normalement, le texte de la zone de saisie d'un ``Spinbox`` peut être coupé ou collé. Pour désactiver ce comportement, utilisez ``exportselection=True``.
        :arg font: 
                Fonte de caractères à utiliser dans la zone de saisie. Voir :ref:`polices`.
        :arg fg:
                (ou **foreground**) Couleur du texte qui apparaît dans la zone de saisie du widget, et la couleur des flèches.
        :arg format: 
                Utilisez cette option pour contrôler la mise en forme (ou formatage) de la valeur numérique en lien avec les options **from_** et **to**. Par exemple, ``format='%10.4f'`` affichera la valeur avec 10 caractères dont 4 pour les chiffres après la virgule.
        :arg from\_: 
                Utilisez cette option avec l'option **to** (décrite plus loin) pour contraindre les valeurs dans un intervalle numérique. Par exemple, ``from_=1`` et ``to=9`` n'autorisera que des valeurs de l'intervalle [1,9]. Voir aussi l'option **increment** ci-dessous.
        :arg highlightbackground: 
                La couleur de la ligne de mise en valeur du focus lorsque le widget ne l'a pas. Voir :ref:`FOCUS`.
        :arg highlightcolor: 
                La couleur de la ligne de mise en valeur du focus lorsque le widget l'obtient.
        :arg highlightthickness: 
                L'épaisseur de la ligne de mise en valeur du focus. 1 pixels par défaut. Mettre cette valeur à 0 pour supprimer la mise en valeur du focus.
        :arg increment: 
                Lorsque vous contraignez les valeurs dans un intervalle au moyen des options **from_** et **to**, vous pouvez utiliser cette option pour préciser de combien la valeur doit augmenter ou diminuer lorsque l'utilisateur clique sur l'une des flèches. Par exemple, si ``from_=0.0``, ``to=2.0``, et ``increment=0.5``, La flèche haute fera défiler les valeurs 0.0, 0.5, 1.0, 1.5, et 2.0.
        :arg insertbackground: 
                Sert à préciser la couleur du curseur d'insertion affiché dans la zone de saisie du widget.
        :arg insertborderwidth: 
                Sert à contrôler l'épaisseur de la bordure du curseur d'insertion. Par défaut, il n'y a pas de bordure (0). Si vous donnez une valeur non négative à cette option, la bordure produira un effet de relief ``'raised'``.
        :arg insertofftime: 
                Cette option et la suivante servent à contrôler le rythme de clignotement du curseur d'insertion. Elles servent à indiquer la durée de disparition - **insertofftime** - et celle d'apparition - **insertontime** -, en millisecondes, de celui-ci. 
        :arg insertontime:
        :arg insertwidth: 
                Utilisez cette option pour préciser la largeur (horizontal) du curseur d'insertion. 2 pixels par défaut.
        :arg justify: 
                Cette option sert à préciser l'alignement du texte dans la zone de saisie du widget. Les valeurs possibles sont ``'left'``, ``'center'`` ou ``'right'``.
        :arg readonlybackground: 
                Couleur de fond du widget lorsqu'il est dans l'état ``'readonly'``.
        :arg relief: 
                Style de relief pour le widget. ``'sunken'`` par défaut; voir :ref:`reliefs`.
        :arg repeatdelay: 
                Cette option et la suivante servent à configurer la fonction de répétition automatique qui est déclenchée lorsque l'utilisateur clique sans relâcher sur l'une des flèches. Cette fonction démarre après **repeatdelay** millisecondes et **repeatinterval** est la durée en millisecondes entre deux répétitions. Les valeurs par défaut sont respectivement 400 et 100 millisecondes.
        :arg repeatinterval:
        :arg selectbackground: 
                Couleur de fond utilisée pour l'item sélectionné.
        :arg selectborderwidth:
                Épaisseur de la bordure affichée autour de l'item sélectionné.
        :arg selectforeground:
                Couleur du texte pour l'item sélectionné.
        :arg state: 
                État du widget. Les valeurs possibles sont ``'normal'`` (défaut), ``'disabled'`` (le widget n'est plus réactif), ``'active'`` (il est sélectionné) et ``'readonly'``. Dans ce dernier cas, il n'est plus possible d'éditer la valeur directement mais celle-ci peut tout de même être modifiée à l'aide des flèches.
        :arg takefocus: 
                Ce widget est susceptible d'obtenir le focus par défaut (voir :ref:`FOCUS`). Pour supprimer le widget de la séquence de traversée du focus, utilisez ``takefocus=False``.
        :arg textvariable:
                Pour récupérer la valeur actuelle du widget, vous pouvez utiliser sa méthode ``get()`` décrite plus loin, ou vous pouvez configurer cette option avec une variable de contrôle. Voir :ref:`CTRLVARIABLES`.
        :arg to: 
                Sert à préciser la limite supérieure de l'intervalle de valeurs pour la sélection. Voir l'option **from_**, ci-dessus, et aussi l'option **increment**.
        :arg values: 
                Il y a deux façons de préciser les valeurs possibles pour ce widget. La première est de fournir un tuple de chaînes de caractères pour cette option. Par exemple, ``values=('rouge', 'vert', 'bleu')`` délimitera les valeurs possibles du widget à ces trois chaînes. Pour configurer le widget avec un intervalle numérique, reportez-vous à l'option **from_** plus haut.
        :arg width: 
                Utilisez cette option pour préciser le nombre de caractères qu'il est possible d'insérer dans la zone de saisie du widget.
        :arg wrap: 
                Par défaut, lorsque le widget est à une des valeurs limites parmi celles qui ont été configurées, l'appui sur la flèche qui devrait faire sortir de l'intervalle de ces valeurs n'a aucun effet. Si vous utilisez ``wrap=True``, cet appui permet de passer à l'autre extrémité de l'intervalle ce qui permet le parcourt «circulaire» des valeurs.
        :arg xscrollcommand: 
                Utilisez cette option pour associer une barre de défilement à la zone de saisie de ce widget. Pour les détails, voir :ref:`assodefil`.

        Les méthodes qui suivent sont disponibles pour un widget ``Spinbox``:

        .. py:method:: bbox(index)

                    Cette méthode retourne la boîte englobante du caractère de position *index* dans la zone de saisie du widget. Le résultat est un 4-tuple *(x, y, l, h)* où *x* et *y* sont les coordonnées du coin supérieur gauche de cette boîte et *l* et *h* sont respectivement la largeur (*width*) et la hauteur (*height*) en pixels dudit caractère.

        .. py:method:: delete(debut, fin=None)

                    Cette méthode supprime des caractères de la zone de saisie de la ``Spinbox``. Les valeurs *debut* et *fin* sont interprétées conformément aux conventions d'extraction de Python.

        .. py:method:: get()

                    Retourne la valeur actuelle du ``Spinbox`` sous la forme d'une chaîne de caractères même si un intervalle numérique a été précisé pour le widget.

        .. py:method:: icursor(index)

                    Sert à positionner le curseur d'insertion à la position *index* en suivant les conventions standards de Python pour les positions.

        .. py:method:: identify(x, y)

                    Étant donné une position (*x*, *y*) à l'intérieur du widget, cette méthode retourne une chaîne de caractères qui décrit ce qui se trouve à cette position. Les valeurs possibles sont:

                    * ``'entry'`` pour la zone de saisie.

                    * ``'buttonup'`` pour la flèche qui pointe vers le haut.

                    * ``'buttondown'`` pour la flèche qui pointe vers le bas.

                    * ``''`` (une chaîne vide) si la position est en dehors du widget.

        .. py:method:: index(i)

                    Cette méthode retourne la position numérique (l'index) du caractère de la zone de saisie sélectionné par *i*. Les valeurs possibles pour *i* sont:

                    * ``'end'`` pour obtenir la position après le dernier caractère de la zone de saisie.

                    * ``'insert'`` pour obtenir la position du curseur d'insertion.

                    * ``'anchor'`` pour obtenir la position de l'ancre de sélection.

                    * ``'sel.first'`` pour obtenir la position du début de la sélection. Si la sélection n'est pas dans le widget, une erreur de type ``TclError`` est lancée.

                    * ``'sel.last'`` pour obtenir la position situé juste après la fin de la sélection. De même, une erreur de type ``TclError`` est lancée si la sélection n'est pas dans ce widget.

                    * Une chaîne de la forme ``'@x'`` précise une coordonnée horizontale dans ce widget. La valeur de retour est la position du caractère situé à cette position. Si aucun caractère n'est situé à cette position, la position du caractère le plus proche est renvoyé.

        .. py:method:: insert(index, text)

                    Cette méthode insère les caractères de la chaîne *text* à la position *index*. Pour les valeurs de l'argument *index*, reportez-vous à la méthode index() décrite plus tôt.

        .. py:method:: invoke(element)

                    L'appel de cette méthode a le même effet que lorsque l'utilisateur clique sur l'une des flèches. Les arguments possibles sont ``'buttonup'`` pour la flèche qui pointe vers le haut et ``'buttondown'`` pour l'autre.

        .. py:method:: scan_dragto(x)

                    Cette méthode fonctionne de la même façon que la méthode :py:meth:`~Entry.scan_dragto` du widget ``Entry``.

        .. py:method:: scan_mark(x)

                    Cette méthode fonctionne de la même façon que la méthode :py:meth:`~Entry.scan_mark` du widget ``Entry``.

        .. py:method:: selection('from', index)

                    Positionne l'ancre de sélection de ce widget à la position *index*. Pour des valeurs possible de *index*, voir la méthode ``index()`` décrite plus haut. La valeur initiale de l'ancre de sélection est 0.

        .. py:method:: selection('to', index)

                    Sélectionne le texte situé entre l'ancre de sélection et l'*index* indiqué.

        .. py:method:: selection('range', debut, fin)

                    Sélectionne le texte situé entre les index *debut* et *fin*. Pour les valeurs possibles d'*index*, voir la méthode ``index()`` ci-dessus.

        .. py:method:: selection_clear()

                    Efface la sélection. 

        .. py:method:: selection_get()

                    Retourne le texte sélectionné. S'il n'y a pas de sélection, cette méthode lève une exception de type ``TclError``.
