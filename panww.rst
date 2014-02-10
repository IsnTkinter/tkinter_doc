.. _PANEDWINDOW:

**********************************************
Le widget ``PanedWindow`` ou fenêtre à paneaux
**********************************************

Une fenêtre à paneaux ou widget ``PanedWindow`` sert à donner à l'utilisateur un moyen de contrôle sur la façon dont l'espace est distribué à l'intérieur de l'application.

Une fenêtre à paneaux ``PanedWindow`` est similaire à un cadre (``Frame``): c'est un conteneur pour des widgets enfants. Chaque fenêtre à paneaux contient un empilement horizontal ou vertical de widgets enfants. En utilisant la souris, l'utilisateur peut déplacer les frontières situés entre deux widgets enfants dans un sens ou un autre relativement à la direction d'empilement.

* Vous pouvez choisir d'afficher ou non des poignés à l'intérieur du widget. Une poignée est figurée par un petit carré qui sert d'aide visuelle pour repérer la ligne de séparation entre deux widgets.

* Vous pouvez choisir de rendre les lignes de séparation - *sash* - visibles. Ces barres sont placés entre deux widgets enfants et elles peuvent être déplacées à l'aide de la souris.

* Un paneau est la zone de la fenêtre occupée par un widget enfant.

Pour créer une nouvelle fenêtre à paneaux comme enfant d'une autre fenêtre ou d'un cadre nommé ``parent``:

.. py:class:: PanedWindow(parent, option, ...)

        Ce constructeur retourne la nouvelle fenêtre à paneaux ``PanedWindow`` créée. Voici les options disponibles:

        :arg bg:
                (ou **background**) La couleur d'arrière plan utilisée derrière les widgets enfants; voir “Colors”.
        :arg bd:
                (ou **borderwidth**) La largeur de la bordure du widget; 2 pixels par défaut. Voir “Dimensions”.
        :arg cursor: 
                Le pointeur de souris utilisé lorsque la souris est au-dessus de la fenêtre; voir “Cursors”.
        :arg handlepad: 
                Utilisez cette option pour préciser la distance à laquelle est placée la poignée (*handle*) sur sa ligne de séparation (*sash*) relativement au bord gauche de cette ligne pour un empilement vertical (``orient='vertical'``) ou au bord haut pour un empilement horizontal (``orient='horizontal'``). La valeur par défaut est 8 pixels.
        :arg handlesize: 
                Utilisez cette option pour préciser la taille de la poignée qui a toujours une forme carrée. Sa valeur par défaut est 8 pixels.
        :arg height: 
                La hauteur du widget. Si aucune valeur n'est indiquée, elle est déterminée par les hauteurs des widgets enfants.
        :arg opaqueresize: 
                Cette option sert à contrôler les opérations de redistribution de l'espace. Par défaut sa valeur est ``True`` et la redistribution de l'espace est réalisée de manière continue au fur et à mesure que l'utilisateur déplace une ligne de séparation. Si cette option est réglée avec la valeur ``False``, le redimensionnement effectif n'est réalisé que lorsque l'utilisateur relâche le bouton de la souris.
        :arg orient: 
                Pour empiler les widgets enfants de la gauche vers la droite, utiliser la valeur ``'horizontal'``. Pour les empiler de haut en bas, utiliser ``'vertical'``.
        :arg relief: 
                Sert à indiquer le relief de la bordure de la fenêtre; voir “Relief styles”. La valeur par défaut est ``'flat'``.
        :arg sashpad: 
                Utilisez cette option pour réserver un espace supplémentaire de chaque côtés des lignes de séparation entre les widgets enfants. Sa valeur par défaut est 0.
        :arg sashrelief: 
                Sert à préciser le relief des lignes de séparation (*sashes*) entre les widgets enfants; voir “Relief styles”. Sa valeur par défaut est ``'flat'``.
        :arg sashwidth: 
                Sert à préciser l'épaisseur des lignes de séparations. 2 pixels par défaut.
        :arg showhandle: 
                Utilisez ``showhandle=True`` pour afficher les poignées. La valeur par défaut est ``False`` mais l'utilisateur peut toujours déplacer les lignes de séparation entre les widgets enfants. La poignée est simplement une aide visuelle.
        :arg width: 
                La largeur de la fenêtre. Si vous ne précisez pas sa valeur, elle sera déterminée par les largeurs des widgets enfants qu'elle contient.

        Pour ajouter des widgets enfants à un fenêtre à paneaux, créez les comme enfant de cette fenêtre, mais, au lieu de les placer en utilisant un gestionnaire de positionnement comme ``grid()`` ou ``pack()``, utilisez la méthode add() de la fenêtre à paneaux.

        Voici les méthodes disponibles pour les fenêtre à paneaux ou widget ``PanedWindow``:

        .. py:method:: add(enfant, option=valeur ...)

                    Utilisez cette méthode pour ajouter le widget *enfant* donné après ceux qui ont déjà été éventuellement ajoutés à cette fenêtre. Commencez par créer le widget *enfant* en utilisant cette fenêtre comme parent, mais n'utilisez aucun gestionnaire de positionnement comme ``grid()`` ou ``pack()`` pour le placer. Ensuite, appelez ``add(enfant)`` et celui-ci apparaîtra dans la fenêtre après tous les autres (s'il y en a).

                    Afin de contrôler l'apparence et la position du widget *enfant*, précisez au moment de l'appel certaines options. Voir “PanedWindow child configuration options”. Vous pouvez modifier ces options de manière dynamique en utilisant la méthode ``paneconfig()`` ou récupérer leur valeur en utilisant la méthode ``panecget()``; ces méthodes sont décrites un peu plus loin.

        .. py:method:: forget(enfant)

                    Supprime le widget *enfant* donné en argument.

        .. py:method:: identify(x, y)

                    Pour une position donnée *(x, y)* relative à la fenêtre, cette méthode retourne une valeur qui décrit l'élément graphique situé à cette position.

                    * si l'élément graphique est un widget enfant ou une sous-fenêtre qui le contient, la méthode retourne une chaîne vide.

                    * s'il s'agit d'une ligne de séparation entre deux widgets enfants, la valeur de retour est un 2-tuple ``(n,'sash')`` où ``n`` est 0 pour la première ligne, 1 pour la deuxième et ainsi de suite.

                    * s'il s'agit d'une poignée, la valeur de retour est un 2-tuple ``(n,'handle')`` où ``n`` a la même signication que pour les lignes de démarcation.

        .. py:method:: panecget(enfant, option)

                    Sert à récupérer la valeur actuelle, pour le widget *enfant*, de l'*option* précisée en deuxième argument à l'aide d'une chaîne de carctères. Pour connaître la liste des options possibles, voir “PanedWindow child configuration options”. 

        .. py:method:: paneconfig(enfant, option=value, ...)

                    Sert à configurer les options du widget *enfant* pour cette fenêtre. Les options disponibles sont décrites plus loin, voir “PanedWindow child configuration options”. 

        .. py:method:: panes()

                    Retourne la liste des widgets enfants de la fenêtre (de la gauche vers la droite ou du haut vers le bas selon son orientation).

        .. py:method:: remove(enfant)

                    Supprime l'*enfant* donné; c'est la même action que celle qu'on obtient avec la méthode ``forget()``.

        .. py:method:: sash_coord(index)

                    Retourne la position du la ligne de séparation de numéro *index*. La ligne de démarcation d'*index* 0 est celle qui sépare les deux premiers widgets enfants, celle d'*index* 1 celle qui sépare le second et le troisième; et ainsi de suite. La valeur de retour est un tupe *(x, y)* qui contient les coordonnées du bord supérieur gauche de la ligne de démarcation (qui est en fait un rectangle très fin).

        .. py:method:: sash_place(index, x, y)

                    Utilisez cette méthode pour repositionner la ligne de démarcation *index*. *x* et *y* précisent les nouvelles coordonnées du coin supérieur gauche de la ligne de démarcation *index*. Tkinter ignore la valeur de la coordonnée perpendiculaire à l'orientation de la fenêtre: *x* est la valeur utile pour repositionner une ligne de démarcation d'une fenêtre avec ``orient=horizontal`` et *y* celle qui agit effectivement pour ``orient=vertical``.
    
Options de configuration des enfants d'un ``PanedWindow``
=========================================================

Chaque enfant d'une fenêtre à paneaux ou ``PanedWindow`` dispose d'un jeu d'options de configuration qui permet de contrôler sa position et son apparence dans la fenêtre. Ces options peuvent être précisées au moment de leur ajout à l'aide de la méthode ``add()``, ou de manière dynamique avec la méthode ``paneconfig()``; il est aussi possible de récupérer les valeurs de ces options au moyen de la méthode ``panecget()``. Toutes ces méthodes sont décrites plus haut.

**after**
        Par défaut, lorsque vous ajoutez un enfant dans la fenêtre, il est ajouté à la suite des enfants précédemment ajoutés. En utilisant ``after=w`` où ``w`` désigne un enfant déjà présent dans la fenêtre, celui-ci sera ajouté à la suite de ``w`` (repoussant ainsi ceux qui viennent après).
**before**
        Similaire à l'option précédente, mais place le nouvel enfant avant celui qu'on précise pour cette option.
**height**
        Sert à préciser la hauteur désirée pour le widget enfant; voir “Dimensions”.
**minsize**
        Utilisez cette option pour indiquer une taille minimale pour le widget enfant dans la direction d'orientation de la fenêtre à paneaux. Pour ``orient='horizontal'``, c'est la largeur minimum; pour ``orient='vertical'``, c'est la hauteur minimum.
**padx**
        Espace supplémentaire horizontal à ajouter à gauche et à droite du widget enfant.
**pady**
        Espace supplémentaire verticale à ajouter au-dessus et en dessous du widget enfant.
**sticky**
        Cette option a le même rôle que l'argument de même nom de la méthode ``grid()``. Elle sert à préciser comment positionner l'enfant si le paneau qui le contient est plus large que celui-ci. Par exemple, ``sticky="nw"`` positionnera le widget dans le coin supérieur gauche (nord ouest) du paneau.
**width**
        La largeur désirée pour le widget enfant.
