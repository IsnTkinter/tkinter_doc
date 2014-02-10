.. _SCROLLBAR:

***********************************************
Le widget ``Scrollbar`` ou barre de défilement
***********************************************

Bon nombre de widgets, comme par exemple les listes de sélection (``Listbox``) et les canevas (``Canvas``), peuvent se comporter comme des fenêtres de visualisation d'une aire virtuelle plus large. Vous pouvez associer à de tels widgets des barres de défilement pour donner un moyen à l'utilisateur de faire glisser la vue et d'accéder aux zones actuellement hors de celle-ci. Voici une capture d'écran qui montre un champ de saisie (``Entry``) muni d'une barre de défilement.

* Une barre de défilement peut être orientée horizontalement (comme celle montrée ci-dessus), ou verticalement. Un widget qui possède deux dimensions de défilement, comme un ``Canvas`` ou une ``Listbox``, peut être muni de deux barres de défilement: horizontale et verticale.

* Le curseur, ou poigné de glissement, est le petit rectangle surélevé qui indique la position courante de défilement.

* Les deux petits triangles à chaque extrémité de la barre sont utilisés pour modifier la position par petits pas. Celui de gauche est nommé ``'arrow1'`` et celui de droite ``'arrow2'``.

* Les zones de glissements situées entre les triangles et le curseur sont appelées ``'trough1'`` et ``'trough2'`` (de la gauche vers la droite ou du haut vers le bas selon l'orientation de la barre).

* La taille et la position du curseur, relativement à la longueur totale de la barre, montre la taille et la position de la portion actuellement visible du widget relativement à sa taille totale. Par exemple, si une barre de défilement verticale est associée à une liste de sélection (``Listbox``) et que son curseur occupe 25% (1/4) de la barre tout en ayant son extrémité haute au milieu de celle-ci, cela signife que la moitié du contenu de la liste est hors de la vue au dessus, un quart est hors de la vue en dessous et un quart de ce contenu est actuellement visible.

* Pour une barre de défilement horizontale, cliquer sur le bouton 1 (gauche) de la souris tout en étant au-dessus du triangle gauche déplace la vue vers la gauche d'une unité. Un déplacement vers la droite d'une même quantité se produit si on clique sur le triangle droit. Un comportement similaire a lieu pour une barre verticale. Pour connaître précisément cette quantité de mouvement, reportez-vous à la documentation des widgets utilisés.

* L'utilisateur peut cliquer-glisser le curseur en utilisant le bouton 1 ou 2 (gauche ou milieu) de la souris afin de déplacer la vue.

* Cliquer gauche sur l'aire de glissement de la barre provoque un saut d'une page de la vue (dans la direction de la barre).

* Cliquer avec le bouton du milieu de la souris sur l'aire de glissement amène la vue à l'une de ses extrémités: tout en haut, en bas, à gauche, à droite.

La position normalisée de la barre de défilement est un nombre de l'intervalle fermé [0.0, 1.0] qui détermine la position du curseur. 0.0 se réfère à la position la plus à gauche d'une barre horizontale, et à la position la plus haute d'une barre verticale.

Pour créer une nouvelle barre de défilement ``Scrollbar`` comme enfant d'une fenêtre ou d'un cadre nommé parent:

.. py:class:: Scrollbar(parent, option, ...)

        Le constructeur retourne le nouveau widget ``Scrollbar`` créé. Ses options incluent:

        :arg activebackground: 
                La couleur du curseur et des flèches lorsque la souris est au dessus de l'un d'eux. Voir “Colors”.
        :arg activerelief: 
                Le relief utilisé pour afficher le curseur lorsque la souris est au dessus. Sa valeur par défaut est ``'raised'``.
        :arg bg: 
                (ou **background**) La couleur du curseur et des flèches lorsque la souris n'est pas au dessus.
        :arg bd: 
                (ou **borderwidth**) La largeur de la bordure 3d qui entoure la zone de glissement et aussi celle de l'effet 3d du curseur et des flèches. Par défaut, il n'y a pas de bordure autour de la zone de glissement, et celle des flèches et du curseur vaut 2 pixels. Pour des valeurs possibles, voir “Dimensions”.
        :arg command: 
                Une fonction à appeler à chaque fois que le curseur de la barre de défilement a été déplacé. Pour plus de détails sur la façon dont cette fonction est appelée, voir “The Scrollbar command callback”.
        :arg cursor: 
                Le curseur utilisée lorsque la souris est au dessus de la barre. Voir “Cursors”.
        :arg elementborderwidth: 
                L'épaisseur de la bordure des flèches et du curseur. Sa valeur par défaut est -1 ce qui signifie que c'est la valeur de l'option **borderwidth** qui est utilisée.
        :arg highlightbackground: 
                La couleur de la ligne de mise en valeur du focus lorsque la barre de défilement ne l'a pas. Voir “Focus: routing keyboard input”.
        :arg highlightcolor: 
                La couleur de la ligne de mise en valeur du focus lorsque la barre de défilement l'obtient.
        :arg highlightthickness: 
                L'épaisseur de la ligne de mise en valeur du focus. 1 par défaut. Mettre cette option à 0 pour supprimer la mise en valeur du focus.
        :arg jump: 
                Sert à contrôler ce qui arrive lorsque l'utilisateur déplace le curseur. Par défaut ``jump=0`` et chaque petit déplacement du curseur produit un appel de la fonction associée à l'option **command**. Si vous réglez cette option avec la valeur 1, la fonction de rappel ne sera pas appelée tant que l'utilisateur n'aura pas relâché le bouton de la souris.
        :arg orient: 
                Configurez cette option avec la valeur ``'horizontal'`` pour une barre de défilement horizontale et ``'vertical'`` pour une barre de défilement verticale.
        :arg relief: 
                Sert à contrôler le relief du widget; sa valeur par défaut est ``'sunken'``. Cette option n'a pas d'effet sur le système Windows.
        :arg repeatdelay: 
                Cette option contrôle la durée, en millisecondes, à partir de laquelle le curseur commence à être déplacé de manière répétive dans la direction d'un clic gauche tenui, à la souris, sur la zone de défilement. Sa valeur par défaut est 300 millisecondes.
        :arg repeatinterval: 
                Cette option contrôle la durée, en millisecondes, qui s'écoule entre deux déplacements automatiques du curseur lorsque l'utilisateur fait un clic prolongé sur la zone de défilement. Sa valeur par défaut est 100 millisecondes.
        :arg takefocus: 
                Ce widget obtient normalement le focus; voir “Focus: routing keyboard input”. Utilisez ``takefocus=0`` si vous souhaitez empêcher cela. Lorsqu'une barre de défilement obtient le focus, on peut la déplacer à l'aide des flèches du clavier.
        :arg troughcolor: 
                La couleur de la zone de glissement de la barre.
        :arg width: 
                La largeur de la barre, dans la direction *y* si elle est horizontale, dans la direction *x* si elle est verticale. Sa valeur par défaut est 16.

        Les méthodes d'une barre de défilement ``Scrollbar`` incluent:

        .. py:method:: activate(element=None)

                    Si aucun argument n'est fournie, cette méthode retourne l'une des chaînes ``'arrow1'``, ``'arrow2'``, ``'slider'``, ou ``''``, selon la position courante de la souris. La chaîne vide est retourné si le curseur n'est pas actuellement au dessus du curseur ou d'une des deux flèches.

                    Pour mettre en valeur un de ces éléments (en utilisant les valeurs des options **activerelief** et **activebackground**), appelez cette méthode avec l'une des chaînes indiquées plus haut.

        .. py:method:: delta(dx, dy)

                    Étant donné un mouvement de *dx* pixels selon *x* et de *dy* pixels selon *y*, cette méthode retourne un flottant qui devrait être ajouté à la valeur normalisée correspondante de la position courante du curseur afin qu'il effectue le même mouvement.

        .. py:method:: fraction(x, y)

                    Étant donné une position *(x, y)*, cette méthode retourne la valeur normalisée (dans l'intervalle [0.0, 1.0]) de la position du curseur qui serait la plus proche de cette position.

        .. py:method:: get()

                    Retourne un 2-tuple ``(a, b)`` qui décrit la position courante du curseur. ``a`` appartient à [0, 1] et correspond au bord gauche ou haut du curseur selon l'orientation de la barre. ``b`` se rapporte à son bord droit ou bas. Par exemple, si le curseur s'étend de la moitié au trois quart de la barre de défilement, vous obtiendriez (0.5,0.75).

        .. py:method:: identify(x, y)

                    Retourne une chaîne de caractères qui précise la partie de la barre de défilement située à la position *(x, y)*. Les valeurs de retour possibles sont ``'arrow1'``, ``'trough1'``, ``'slider'``, ``'trough2'``, ``'arrow2'``, ou la chaîne vide ``''`` si cette position ne correpond à aucun composant de la barre.

        .. py:method:: set(deb, fin)

                    Pour munir un widget ``w`` d'une barre de défilement, configurer son option **xscrollcommand** ou **yscrollcommand** avec cette méthode. Les arguments ont la même signification que les valeurs retournées par la méthode ``get()`` décrite plus tôt. De cette façon, le widget ``w`` est en mesure d'avertir la barre de défilement de la portion de sa zone d'affichage actuellement visible afin que la barre soit ajustée en conséquence. Notez que le déplacement du curseur ne produit pas pour autant le glissement de la zone visible du widget ``w``.
    
Fonction de rappel d'une barre de défilement
============================================

Lorsque l'utilisateur manipule la barre de défilement, celle-ci appelle la fonction de rappel - notée *command* ci-après - qui a été associée à son option **command**. Les arguments transmis à la fonction dépendent de ce qu'à fait l'utilisateur:

Lorsque l'utilisateur déplace le curseur d'une unité vers la gauche ou vers le haut, en cliquant par exemple sur la flèche gauche ou haute, l'appel de *command* est du type::

        command('scroll', -1, 'units')

ou qu'il déplace le curseur d'une unité vers la droite ou vers le bas, les arguments sont::

        command('scroll', 1, 'units')

Lorsqu'il effectue un mouvement d'une page vers la gauche ou vers le haut::

        command('scroll', -1, 'pages')

vers la droite ou vers le bas::

        command('scroll', 1, 'pages')

Lorqu'il déplace le curseur jusqu'à la position normalisée *f* de l'intervalle [0,1] (0 tout à gauche ou tout en haut, 1 tout à droite ou tout en bas), l'appel est de la forme::

        command('moveto', f)

Ces séquences d'appels sont conformes aux arguments attendus par les méthodes ``xview()`` et ``yview()`` des canevas (``Canvas``), listes de sélection (``Listbox``), et du widget de texte (``Text``). Les champs de saisis n'ont pas de méthode xview(). Voir “Scrolling an Entry widget”. 

Associer une barre de défilement à un autre widget
==================================================

Voici un fragment de code qui montre la création d'un canevas muni de barres de défilement horizontale et verticale::

    canv = Canvas(root, width=600, height=400,
        defilregion=(0, 0, 1200, 800))
    canv.grid(row=0, column=0)

    defilY = Scrollbar(root, orient='vertical',
        command=canv.yview)
    defilY.grid(row=0, column=1, sticky='ns')

    defilX = Scrollbar(self, orient='horizontal',
        command=canv.xview)
    defilX.grid(row=1, column=0, sticky='ew')

    canv['xscrollcommand'] = defilX.set
    canv['yscrollcommand'] = defilY.set

Notes:

    L'association fonctionne dans les deux sens. L'option **xscrollcommand** du canevas doit être associée à la méthode ``set()`` de la barre de défilement horizontale et l'option **command** de cette même barre de défilement doit être associée à la méthode ``xview()`` du canvas. Même chose pour la barre de défilement verticale.

    L'option **sticky** du gestionnaire de positionnement ``grid()`` utilisé pour positionner les barres de défilement les force à s'étendre assez pour s'ajuster aux dimensions du canevas.
