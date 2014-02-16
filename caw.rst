.. _CANEVAS:

************************
Les Canevas ``Canvas``
************************

Un canevas est une zone rectangulaire destinée à contenir des dessins ou d'autres figures complexes. Vous pouvez y placer des graphiques, du texte, des composants graphiques (*widgets*) ou des cadres (*frames*). Veuillez consulter les sections suivantes pour les méthodes qui servent à créer de tels objet sur un canevas:

* :py:meth:`~Canvas.create_arc` : Une portion d'ellipse. Voir :ref:`arcs`.

* :py:meth:`~Canvas.create_bitmap` : Une image de type bitmap. Voir :ref:`can_bitmaps`.

* :py:meth:`~Canvas.create_image` : Une image «plus riche». Voir :ref:`can_images`.

* :py:meth:`~Canvas.create_line` : Un ou plusieurs segments. Voir :ref:`lignes`.

* :py:meth:`~Canvas.create_oval` : Une ellipse; Utiliser cette méthode pour dessiner des cercles qui sont des cas particuliers d'ellipses. Voir :ref:`ellipses-et-cercles`.

* :py:meth:`~Canvas.create_polygon` : Un polygone. Voir :ref:`polygones`.

* :py:meth:`~Canvas.create_rectangle` : Un rectangle. Voir :ref:`rectangles`.

* :py:meth:`~Canvas.create_text` : Pour insérer du texte. Voir :ref:`textes`.

* :py:meth:`~Canvas.create_window` : Une fenêtre rectangulaire. Voir :ref:`fenêtres`.

Pour créer un objet de type Canvas:

.. py:class:: Canvas(parent, option=valeur, ...)

        Le constructeur retourne le nouveau widget canvas. Ses options sont:

        :arg borderwidth:
                (ou **bd**) Largeur de la bordure du canevas. Voir :ref:`dimensions`.
                La valeur par défaut est 2 pixels. 
        :arg background:
                (ou **bg**) Couleur de fond du canevas. La valeur par défaut est un gris léger, à peu près ``'#E4E4E4'``.
        :arg closeenough:
                Un flottant qui précise la distance minimale entre la souris et un item pour considérer qu'elle est dessus. La valeur par défaut est 1.0.
        :arg confine:
                Si ``True`` (la valeur par défaut), il n'est pas possible de faire défiler le canvas en dehors de sa zone de visualisation (`scrollregion`), voir ci-dessous.
        :arg cursor:
                Pointeur de la souris utilisé sur le canevas. Voir :ref:`pointeurs`.
        :arg height:
            Hauteur du canvas. Voir :ref:`dimensions`.
        :arg highlightbackground:
                Couleur de la ligne de focus lorsque le canevas n'a pas le focus. Voir :ref:`FOCUS`. 
        :arg highlightcolor:
                Couleur de la ligne de focus lorsque le canevas a le focus.
        :arg highlightthickness:
                Épaisseur de la ligne de focus. La valeur par défaut est 1.
        :arg relief:
                Le style de relief du canvas. La valeur par défaut est ``'flat'``. Voir :ref:`reliefs`.
        :arg scrollregion:
                Un tuple ``(w, n, e, s)`` qui définit la zone du canevas accessible par défilement. ``w`` désigne le côté gauche, ``n`` le bord haut, ``e`` le côté droit et ``s`` le bord bas.
        :arg selectbackground:
                La couleur de fond utilisée pour afficher l'item sélectionné.
        :arg selectborderwidth:
                L'épaisseur de la bordure de l'item sélectionné.
        :arg selectforeground:
                La couleur d'avant plan utilisée pour mettre en valeur l'item sélectionné.
        :arg takefocus:
                Normalement, le focus (see Section 53, “Focus: routing keyboard input”) est obtenu en utilisant la touche Tab seulement si un gestionnaire d'événement a été prévu pour cela (see Section 54, “Events” for an overview of keyboard bindings). Si vous positionnez la valeur de cette option à 1, le canevas obtiendra le focus de manière ordinaire. Positionnez la à ``''`` pour obtenir le comportement «normal».
        :arg width:
                Largeur du canevas. Voir :ref:`dimensions`.
        :arg xscrollincrement:
                Normalement, on peut faire défiler un canevas horizontalement à n'importe quelle position. Vous pouvez obtenir ce comportement en positionnant cette option à ``0`` . Si vous donnez une valeur positive à cette option, le canevas défile en utilisant des multiples de cette valeur. Elle sera en outre utilisée comme unité de défilement horizontal comme quand l'utilisateur clique sur les flèches situées aux extrémités d'une barre de défilement. Voir :ref:`SCROLLBAR`. 
        :arg xscrollcommand:
                Si le canevas est muni d'une barre défilement, positionnez cette option en utilisant la méthode ``set()`` de la barre.
        :arg yscrollincrement:
                Fonctionne de manière similaire à **xscrollincrement**, mais pour un défilement vertical.
        :arg yscrollcommand:
                Fonctionne de manière similaire à **xscrollcommand**, mais pour une barre de défilement vertical.

Le système de coordonnées
=========================

Parce qu'un canevas peut être plus large que sa fenêtre de visualisation et qu'il peut être équipé de barres de défilement afin de le déplacer, il y a deux systèmes de coordonnées pour chaque canevas:

* Les coordonnées d'un point dans la fenêtre de vue; elles sont relatives au bord supérieur gauche de cette fenêtre.

* Les coordonnées d'un point dans le canevas lui-même.

La liste d'affichage
====================

La liste d'affichage se réfère à la séquence de tous les items qui se trouvent sur le canevas, de l'arrière plan, (*background* - le bas de la liste d'affichage) vers l'avant plan, (*foreground* - le haut de cette liste).

Si deux items se recouvrent, l'item au-dessus de l'autre dans la liste d'affichage désigne celui qui est le plus proche de l'avant plan, c'est à dire qui est vu comme au-dessus de l'autre sur l'affichage. Par défaut, lorsqu'un item est créé, il est placé tout en haut de la liste d'affichage (et donc il apparaît au dessus des items déjà affichés), mais il est possible de ré-ordonner la liste d'affichage.

.. _CANVASidnum:

Les identifiants numériques
===========================

Chaque item affiché sur le canevas possède un identifiant numérique (simple entier) unique, il s'agit de la valeur retournée par le «constructeur» - ``create_*()`` - lors de sa création.

.. _CANVAStags:

Les marques (`tags`)
====================

Une marque, *tag*, est une chaîne de caractères qu'on peut associer à un ou plusieurs items du canevas.

* Une marque peut être associée à autant d'items que l'on veut sur le canvas, 0 inclus.

* Un item peut posséder autant de marques que souhaité, 0 inclus.

Les marques, *tags*, ont de nombreux usages. Par exemple, si vous dessinez une carte sur un canevas et que vous utilisez des textes pour donner le nom des rivières, vous pourriez marquer tous ces items textuels avec ``'rivEtiq'``. Cela vous permettrait d'agir globalement sur les étiquettes en utilisant cette marque afin, par exemple, de changer leur couleur ou de les supprimer.

Identification des items graphiques
===================================

Un argument ``tagOrId`` se réfère à un ou plusieurs items du canevas.

* Si l'argument ``tagOrId`` est un entier, il est considéré comme un identifiant numérique et il s'applique à l'unique item qui le possède. Voir :ref:`CANVASidnum`.

* Si cet argument est une chaîne de caractères, il est interprété comme une marque et sélectionne tous les items qui ont cette marque (s'il y en a). Voir :ref:`CANVAStags`. 

.. _CANVASmeth:  

Méthodes des Canevas
====================

Tous les Canevas disposent de ces méthodes (outre celles qui servent à créer des items et qui sont présentées plus loin):

.. hlist::
  :columns: 4

  * :py:meth:`~Canvas.addtag_above`
  * :py:meth:`~Canvas.addtag_all`
  * :py:meth:`~Canvas.addtag_below`
  * :py:meth:`~Canvas.addtag_closest`
  * :py:meth:`~Canvas.addtag_enclosed`
  * :py:meth:`~Canvas.addtag_overlapping`
  * :py:meth:`~Canvas.addtag_withtag`
  * :py:meth:`~Canvas.bbox`
  * :py:meth:`~Canvas.canvasx`
  * :py:meth:`~Canvas.canvasy`
  * :py:meth:`~Canvas.coords`
  * :py:meth:`~Canvas.dchars`
  * :py:meth:`~Canvas.delete`
  * :py:meth:`~Canvas.dtag`
  * :py:meth:`~Canvas.find_above`
  * :py:meth:`~Canvas.find_all`
  * :py:meth:`~Canvas.find_below`
  * :py:meth:`~Canvas.find_closest`
  * :py:meth:`~Canvas.find_enclosed`
  * :py:meth:`~Canvas.find_overlapping`
  * :py:meth:`~Canvas.find_withtag`
  * :py:meth:`~Canvas.focus`
  * :py:meth:`~Canvas.gettags`
  * :py:meth:`~Canvas.icursor`
  * :py:meth:`~Canvas.index`
  * :py:meth:`~Canvas.insert`
  * :py:meth:`~Canvas.itemcget`
  * :py:meth:`~Canvas.itemconfigure`
  * :py:meth:`~Canvas.move`
  * :py:meth:`~Canvas.postscript`
  * :py:meth:`~Canvas.scale`
  * :py:meth:`~Canvas.scan_dragto`
  * :py:meth:`~Canvas.scan_mark`
  * :py:meth:`~Canvas.select_adjust`
  * :py:meth:`~Canvas.select_clear`
  * :py:meth:`~Canvas.select_from`
  * :py:meth:`~Canvas.select_item`
  * :py:meth:`~Canvas.select_to`
  * :py:meth:`~Canvas.tag_bind`
  * :py:meth:`~Canvas.tag_lower`
  * :py:meth:`~Canvas.tag_raise`
  * :py:meth:`~Canvas.tag_unbind`
  * :py:meth:`~Canvas.type`
  * :py:meth:`~Canvas.xview_moveto`
  * :py:meth:`~Canvas.xview_scroll`
  * :py:meth::w
    `~Canvas.yview_moveto`
  * :py:meth:`~Canvas.yview_scroll`

.. py:method:: Canvas.addtag_above(newTag, tagOrId)

        Appose une nouvelle marque *newTag* à l'item situé juste au-dessus de celui qui est sélectionné par *tagOrId* dans la liste d'affichage. L'argument *newTag*, donné sous la forme d'une chaîne de caractère, est la marque qu'on souhaite apposer.

.. py:method:: Canvas.addtag_all(newTag)

        Attache la marque donnée à tous les items qui sont présents sur le canevas.

.. py:method:: Canvas.addtag_below(newTag, tagOrID)

        Attache la nouvelle marque *newTag* à tous les items situés en-dessous de celui qui est indiqué par l'identifiant numérique ou la marque *tagOrId*. L'argument *newTag* est une chaîne de caractères.

.. py:method:: Canvas.addtag_closest(newTag, x, y, halo=None, start=None)

        Ajoute une marque à l'item le plus proche de la position indiquée par les coordonnées (de la fenêtre de vue). Si un ou plusieurs items sont à la même distance, celui qui est le plus haut dans la liste d'affichage (qui recouvre les autres) est sélectionné.
        Utilisez l'argument *halo* afin d'augmenter la taille effective du point. Par exemple, une valeur de 5 indique le traitement de tous les objets qui recouvrent le disque de centre *(x, y)*.

        Si l'identifiant d'un objet est utilisé pour l'argument *start*, cette méthode marque l'item qui est le plus haut dans la liste d'affichage tout en étant en dessous de celui qui est ainsi identifié.

.. py:method:: Canvas.addtag_enclosed(newTag, x1, y1, x2, y2)

        Ajoute la marque *newTag* à tous les items qui sont complètement recouvert par le rectangle dont le coin supérieur gauche est *(x1, y1)* et le coin inférieur droit est *(x2, y2)*. 

.. py:method:: Canvas.addtag_overlapping(newTag, x1, y1, x2, y2)

        Comme la méthode précédente à cela près que les items marqués sont tous ceux qui ont au moins un point commun avec le rectangle.

.. py:method:: Canvas.addtag_withtag(newTag, tagOrId)

        Ajoute la marque *newTag* à ou aux objets identifiés par *tagOrId*. 

.. py:method:: Canvas.bbox(tagOrId=None)

        Retourne un tuple *(x1, y1, x2, y2)* qui décrit un rectangle qui renferme tous les objets identifiés par *tagOrId*. Si l'argument n'est pas précisé, le rectangle retourné est le plus petit qui contient tous les items présents dans le canevas. Le coin supérieur gauche du rectangle est *(x1, y1)* et son coin inférieur droit est *(x2, y2)*.

.. py:method:: Canvas.canvasx(screenx, gridspacing=None)

        Retourne la coordonnée x du canevas qui correspond à la coordonnée x d'affichage précisée par *screenx*. Si l'argument *gridspacing* est précisé, la valeur de x relative au canevas est arrondi au plus proche multiple de cette valeur.

.. py:method:: Canvas.canvasy(screeny, gridspacing=None)

        Similaire à la méthode précédente mais pour y.

.. py:method:: Canvas.coords(tagOrId, x0, y0, x1, y1, ..., xn, yn)

        Si vous précisez uniquement l'argument *tagOrId*, elle retourne un tuple contenant les coordonnées du plus bas ou de l'unique item précisé par cet argument. Le nombre des coordonnées dépend du type d'item. Dans la plupart des cas, il est de la forme *(x1, y1, x2, y2)* décrivant la boîte englobante (*bounding box*) de l'item.

        Vous pouvez déplacer un item en précisant ses nouvelles coordonnées.

.. py:method:: Canvas.dchars(tagOrId, first=0, last=first)

        Supprime des caractères du ou des items textuels sélectionnés. Tous les caractères situés entre *first* et *last* (inclus) sont supprimés, ces paramètres indiquant une position entière ou la fin du texte via la chaîne ``'end'``. Par exemple, pour un canevas ``C`` et un item de marque ``'I'``, ``C.dchars('I', 1, 1)`` supprime le second caractère.

.. py:method:: Canvas.delete(tagOrId)

        Supprime le ou les items indiqués par *tagOrId*. Il n'y a pas d'erreurs si aucun item ne correspond à *tagOrId*.

.. py:method:: Canvas.dtag(tagOrId, tagToDelete)

        Supprime la marque *tagToDelete* du ou des items sélectionnés par *tagOrId*. 

.. py:method:: Canvas.find_above(tagOrId)

        Retourne l'identifiant numérique de l'item situé juste au dessus de celui qui est sélectionné par *tagOrId*. S'il y en a plusieurs, on utilise le plus haut dans la liste d'affichage. Si l'item précisé par *tagOrId* est le plus haut, la méthode returne un tuple vide ``()``.

.. py:method:: Canvas.find_all()

        Retourne une liste qui contient tous les identifiants numériques de tous les items du canevas, du plus bas au plus haut.

.. py:method:: Canvas.find_below(tagOrId)

        Retourne l'identifiant numérique de l'item situé juste en dessous de celui qui est sélectionné par *tagOrId*. Si plusieurs items correspondent, on obtient le plus bas dans la liste d'affichage. Si l'item sélectionné par *tagOrId* est le plus bas, la méthode retourne un tuple vide ``()``.

.. py:method:: Canvas.find_closest(x, y, halo=None, start=None)

        Retourne un tuple contenant l'identifiant numérique d'un seul item, celui qui est le plus proche du point *(x, y)*. Si plusieurs items sont sélectionnés, c'est celui qui est le plus haut dans la liste d'affichage. Si aucun item n'est sélectionné, retourne une liste vide. Utiliser l'argument *halo* afin d'augmenter la taille effective du point. Tout item situé à une distance inférieur à *halo* de *(x, y)* le coupe. Si *start* est renseigné, en utilisant une marque ou un identifiant (la marque sélectionne l'item le plus bas), l'item le plus proche et situé en-dessous de *start* est choisi.

.. py:method:: Canvas.find_enclosed(x1, y1, x2, y2)

        Retourne la liste des identifiants numériques des items situés entièrement à l'intérieur du rectangle déterminé par *(x1, y1)* (coin supérieur gauche) et *(x2, y2)* (coin inférieur droit). 

.. py:method:: Canvas.find_overlapping(x1, y1, x2, y2)

        Similaire à la méthode précédente, mais sélectionne tous les items qui ont au moins un point commun avec le rectangle.

.. py:method:: Canvas.find_withtag(tagOrId)

        Retourne la liste des identifiants numériques des items sélectionnés par *tagOrId*.

.. py:method:: Canvas.focus(tagOrId=None)

        Donne le focus à l'item sélectionné par *tagOrId*. Si plusieurs sont sélectionnés, donne le focus au premier de la liste d'affichage qui permet un curseur d'insertion. Si aucun item ne satisfait cette condition ou si le canevas n'a pas le focus, le focus n'est pas modifié. Si l'argument est omis, l'identifiant de l'item qui a le focus est retourné ou ``''`` si aucun ne l'a.

.. py:method:: Canvas.gettags(tagOrId)

        Si *tagOrId* est un identifant numérique, elle retourne la liste de toutes les marques qui sont associées à cet item. Si c'est une marque, elle retourne la liste de toutes les marques de l'item le plus bas parmi ceux qui sont sélectionnés.

.. py:method:: Canvas.icursor(tagOrId, index)

        En supposant que l'item sélectionné permette l'insertion de texte et qu'il possède le focus, positionne le curseur d'insertion à la position *index* laquelle est soit un entier ou la chaîne ``'end'``. N'a pas d'effet autrement.

.. py:method:: Canvas.index(tagOrId, specifier)

        Retourne l'index (entier) du *specifier* donné dans l'item textuel sélectionné par *tagOrId* (le plus bas s'il y en a plusieurs). La valeur de retour est une position dans une chaîne qui suit les convention de Python, 0 signifie avant le premier caractère. L'argument *specifier* peut être :

        * ``'insert'``, pour retourner la position courante du curseur d'insertion.

        * ``'end'``, pour retourner la position qui suit le dernier caractère.

        * 'sel.first', pour retourner la position initiale de la zone de sélection. Si une telle zone n'existe pas, tkinter produira une exception du type ``TclError``.

        * ``'sel.last'``, pour retourner la position de la fin de la zone de sélection. De même, tkinter lève une exception si une telle zone n'existe pas.

        * Une chaîne de la forme ``'@x,y'`` pour retourner l'index du caractère situé à la position *(x, y)*. Si cette position est située au-dessus ou à gauche de l'item textuel, la méthode retourne 0. Si elle est située en-dessous ou à droite, la méthode retourne l'index de fin de l'item. 

.. py:method:: Canvas.insert(tagOrId, beforeThis, text)

        Insère la chaîne de caractères *text* dans le ou les items sélectionné par *tagOrId*, à la position déterminée par *beforeThis*: ``'insert'``, ``'end'``, ``'sel.first'`` et ``'sel.last'`` ou un entier (index) ou ``'@x,y'`` (*x* et *y* à remplacer par des entiers).

.. py:method:: Canvas.itemcget(tagOrId, option)

        Retourne la valeur de l'*option* de configuration (précisée par une chaîne de caractères) pour l'item sélectionné (ou pour l'item le plus bas si plusieurs sont sélectionnés par *tagOrId*. C'est très similaire à la méthode ``cget()`` pour les widgets.

.. py:method:: Canvas.itemconfigure(tagOrId, option, ...)

        Si aucune option n'est indiquée, retourne un dictionnaire dont les clés sont les options possibles pour l'item donné par *tagOrId* (ou le plus bas s'il y en a plusieurs). Autrement, modifie la ou les options données sous la forme ``option=valeur``.

.. py:method:: Canvas.move(tagOrId, dx, dy)

        Déplace les items donnés via *tagOrId* en ajoutant *dx* à leurs coordonnées *x* et *dy* à leurs coordonnées *y*.

.. py:method:: Canvas.postscript(option, ...)

        Génère une représentation du contenu actuel du canevas sous la forme d'une image PostScript encapsulé. Ses options sont:

        :arg colormode:
                Utilisez ``'color'`` pour une image couleur, ``'gray'`` pour une image en niveaux de gris, ou ``'mono'`` pour une image en noir et blanc.
        :arg file:
                Pour préciser un fichier dans lequel le code PostScript sera écrit. Si non renseigné, le PostScript est retourné sous la forme d'une chaîne de caractère.
        :arg height:
                Hauteur du canevas à prendre en compte. Par défaut, la hauteur visible du canevas.
        :arg rotate:
                Si ``False``, la page est rendue en mode «portrait»; si ``True``, en mode «paysage».
        :arg x:
        :arg y:
                Précisent les coordonnées du coin supérieur gauche de la zone du canevas à afficher.
        :arg width:
                largeur à prendre en compte. Par défaut, la largeur visible du canevas.

.. py:method:: Canvas.scale(tagOrId, x, y, sx, sy)

        Mise à l'échelle de tous les objets relativement au point de référence ``P=(x, y)``. Les facteurs d'échelle *sx* et *sy* sont basés sur une valeur de 1.0 qui signifie aucune mise à l'échelle. Chaque point des items sélectionnés est déplacé de façon que leurs distances en *x* (resp. en *y*) au point ``P`` sont multipliées par *sx* (resp. *sy*). Cette méthode ne modifie pas la taille des textes mais peut les déplacer.

.. py:method:: Canvas.scan_dragto(x, y, gain=10.0)

        Sert à faire défiler le canevas. voir la méthode :py:meth:`~Canvas.scan_mark()`.

.. py:method:: Canvas.scan_mark(x, y)

        Cette méthode sert à réaliser des défilement rapide du canevas. L'intention est que l'utilisateur puisse faire défiler le canevas par cliquer-glisser c'est à dire en appuyant sur un bouton de la souris (sans relâcher) et en la déplaçant jusqu'au relâchement. Pour réaliser cette fonctionnalité, lier l'événement souris «bouton appuyé» à un gestionnaire qui appelle cette méthode en positionnant *x* et *y* à la position de la souris. Ensuite, lier l'événement ``'<Motion>'`` à un gestionnaire qui, en supposant que le bouton de la souris n'est pas relâché, appelle :py:meth:`~Canvas.scan_dragto(x, y, gain)` en positionnant *x* et *y* aux coordonnées de la souris ; le paramètre *gain* sert à contrôler le rythme du défilement, sa valeur par défaut est ``10.0``. Utiliser une valeur plus grande pour accélérer le défilement.

.. py:method:: Canvas.select_adjust(tagOrId, index)

        Trouve l'extrémité de la selection courante la plus proche du caractère donné par *index* et l'ajuste de façon que la nouvelle sélection contienne ce caractère. L'autre extrémité de la sélection devient le point d'ancrage pour une utilisation ultérieure de :py:meth:`~Canvas.select_to`. Si il n'y avait aucune sélection, se comporte comme la méthode  :py:meth:`~Canvas.select_to`.

        Pour les valeurs possible de *index*, voir :py:meth:`~Canvas.insert`. 

.. py:method:: Canvas.select_clear()

        Supprime la sélection courante (pas ce qui est sélectionné) si elle existe, autrement ne fait rien.

.. py:method:: Canvas.select_from(tagOrId, index)

        Positionne le point d'ancrage de la sélection juste avant le caractère précisé par *index* dans le texte de l'item donné par *tagOrId*. Cette méthode ne modifie pas une sélection existante, elle positionne simplement la marque de fin de sélection pour l'utilisation ultérieur de :py:meth:`~Canvas.select_to`.

.. py:method:: Canvas.select_item()

        S'il y a une sélection de texte dans ce canevas, retourne l'identiant de l'item texte qui contient la sélection. Sinon, retourne ``None``.

.. py:method:: Canvas.select_to(oid, index)

        Positionne la sélection afin qu'elle inclut tous les caractères compris entre l'ancre de la sélection et *index*. La nouvelle sélection contient le caractère à la position *index*. Elle contient le caractère associé à l'ancre de sélection seulement si *index* est supérieur ou égal au point d'ancrage de la sélection. Le point d'ancrage de la sélection est déterminé par la dernière utilisation des méthodes :py:meth:`~Canvas.select_adjust` ou :py:meth:`~Canvas.select_from`.  Si le point d'ancrage de la sélection n'est pas positionné, il est placé à la position *index*.

.. py:method:: Canvas.tag_bind(tagOrId, chevt=None, gestionnaire=None, add=None)

        Lie le gestionnaire d'événement *gestionnaire*, pour l'évenement précisé par *chevt*, à ou aux items *tagOrId*. Si l'argument *add* est une chaîne qui commence par ``'+'``, cette liaison est ajoutée à celles qui ont déjà pu être définies pour cet événement. Autrement, les liaisons précédement définies sont remplacées par celle-ci.  Pour plus d'informations, voir :ref:`EVENTS`. Notez que la liaison aux items n'est pas supprimée par le retrait d'une marque (ni ajoutée en cas de nouveau marquage).

.. py:method:: Canvas.tag_lower(tagOrId, belowThis)

        Déplace les items *tagOrId* juste en-dessous du premier ou seul item indiqué par *belowThis*. S'il y en a plusieurs, leur ordre relatif n'est pas modifié. Cette méthode ne s'applique pas aux items fenêtre, *window*.

.. py:method:: Canvas.tag_raise(tagOrId, aboveThis)

        Déplace les items sélectionnés par *tagOrId* juste au-dessus du premier ou seul item sélectionné par *aboveThis*. S'il y en a plusieurs, leur ordre relatif n'est pas modifié. Cette méthode ne s'applique pas aux items fenêtre, *window*.

.. py:method:: Canvas.tag_unbind(tagOrId, chEvt, gestId=None)

        Supprime la liaison entre le ou les items *tagOrId* et le gestionnaire *gestId* pour la chaîne d'événement *chEvt*. Voir  :ref:`EVENTS`. 

.. py:method:: Canvas.type(tagOrId)

        Retourne le type du premier ou seul item sélectionné par *tagOrdId*. La valeur de retour est l'une des chaînes suivante : ``'arc'``, ``'bitmap'``, ``'image'``, ``'line'``, ``'oval'``, ``'polygon'``, ``'rectangle'``, ``'text'``, or ``'window'``. 

.. py:method:: Canvas.xview_moveto(fraction)

        Cette méthode fait défiler le canevas relativement à sa fenêtre de vue. L'intention est de faire une liaison avec l'option *command* d'une barre de défilement qui aurait été associée à ce canevas. Le défilement est horizontal jusqu'à une position entre 0 et 1 (argument *fraction*): 0.0 pour sa position la plus à gauche et 1.0 pour sa position la plus à droite. 

.. py:method:: Canvas.xview_scroll(n, what)

        Cette méthode fait défiler le canevas à gauche ou à droite. L'argument *what* précise le défilement qui peut être soit ``'units'`` soit ``'pages'``, *n* précise le nombre d'unité du déplacement (vers la droite si positif, vers la gauche autrement). ``'units'`` se réfère à l'option *xscrollincrement* (voir :ref:`SCROLLBAR`). Pour ``'pages'``, *n* est multiplié par 90% de la largeur de la page.

.. py:method:: Canvas.yview_moveto(fraction)

        Même chose que ``xview_moveto`` mais verticalement. 

.. py:method:: Canvas.yview_scroll(n, what)

        Même chose que ``xview_scroll`` mais verticalement.

.. _arcs:

Les arcs
========

Un arc, dans sa forme générale, est une portion d'ellipse. Une ellipse tout entière ou un cercle forment des cas particulier. Reportez-vous à  “Canvas oval objects” pour en savoir plus sur la géométrie des ellipses dessinées.

Pour créer un arc sur un canvas, utiliser :

.. py:method:: Canvas.create_arc(x0, y0, x1, y1, option, ...)

        Le constructeur retourne l'identifiant numérique du nouvel arc créé.

        Le point *(x0, y0)* est le coin supérieur gauche et *(x1, y1)* le coin inférieur droit du rectangle dans lequel s'inscrit l'ellipse. Si le rectangle est un carré, vous obtenez un (arc) de cercle.

        Les options possibles sont: 

        :arg activedash:
                Ces options servent à préciser l'apparence de l'arc lorsque son état est ``'active'``, c'est à dire lorsque la souris le survole. Pour les valeurs possibles, voir les options **dash**, **fill**, **outline**, **outlinestipple**, **stipple**, and **width.** 
        :arg activefill:
        :arg activeoutline:
        :arg activeoutlinestipple:
        :arg activestipple:
        :arg activewidth:
        :arg dash: 
                Sert à réaliser une bordure hachurée autour de l'arc. Utiliser cette option pour préciser un motif de hachure. Voir :ref:`Motifs-brise`.
        :arg dashoffset: 
                Utiliser cette option pour décaler la bordure du motif hachuré à un autre point du cycle. Voir :ref:`Motifs-brise`.
        :arg disableddash: 
                Ces options servent à préciser l'apparence de l'arc lorsque son état est ``'disabled'``.
        :arg disabledfill:
        :arg disabledoutline:
        :arg disabledoutlinestipple:
        :arg disabledstipple:
        :arg disabledwidth:
        :arg extent:
                Largeur angulaire de l'arc en degrés. L'arc commence à l'angle précisé par l'option **start** et s'étend de **extent** degrés dans le sens direct (sens contraire des aiguilles d'une montre).
        :arg fill:
                Par défaut, l'intérieur de l'arc est transparent et vous pouvez obtenir ce comportement avec ``fill=''``. Vous pouvez aussi utiliser une couleur de remplissage. Voir :ref:`couleurs`.
        :arg offset: 
                Utiliser cette option pour modifier le décalage du motif de «pointillé» de l'intérieur de l'arc. Voir :ref:`nuagepts`.
        :arg outline:
                Couleur de la bordure. Par défaut, ``outline='black'``.
        :arg outlineoffset: 
                Utiliser cette option pour ajuster le motif en «pointillé» de la ligne de bordure. Voir :ref:`nuagepts`.
        :arg outlinestipple:
                Utiliser cette option pour une ligne de bordure en pointillé. Le motif est précisé à l'aide d'un bitmap; Voir :ref:`bitmaps`.
        :arg start:
                Angle (en degré), mesuré à partir de l'axe des *x* (dirigé horizontalement et vers la droite), qui précise le point de départ de l'arc. Si cette option n'est pas renseignée, on obtient une ellipse.
        :arg state: 
                ``'normal'`` par défaut. Il vaut ``'active'`` lorsque la souris le survole. Mettre cet option à ``'disabled'`` pour l'empêcher de réagir à la souris, la mettre à ``'hidden'`` pour le rendre invisible.
        :arg stipple: 
                Un bitmap pour indiquer le motif de pointillé à utiliser pour remplir l'intérieur de l'arc. Par défaut, ``stipple=''``, ce qui indique l'utilisation potentielle d'une couleur de remplissage. Une valeur typique serait ``stipple='gray25'``. N'a pas d'effet sauf si une couleur a été indiquée pour l'option **fill** . Voir :ref:`bitmaps`.
        :arg style: 
                Par défaut, l'arc est dessiné avec ses rayons; utiliser ``style='pieslice'`` pour obtenir cela. Pour dessiner l'arc sans ses rayons, utiliser ``style='arc'``. Pour tracer l'arc et sa corde, c'est à dire le segment qui joint ses extrémtités, utiliser ``style='chord'``.
        :arg tags: 
                Si c'est une chaîne seule, elle sert à marquer (*tag*) l'arc. Utiliser un tuple de chaînes pour lui attribuer plusieurs marques. Voir :ref:`CANVAStags`.
        :arg width:
                Largeur de la bordure. Vaut 1 pixel par défaut. Utiliser ``width=0`` Pour rendre la bordure invisible. Voir :ref:`dimensions`. 


.. _can_bitmaps:

Les bitmaps
===========

Un bitmap sur un canevas est une image ayant seulement deux couleurs : la couleur de fond (pour la valeur 0) et la couleur d'avant plan (pour la valeur 1).

Pour créer un item de type bitmap sur un canevas, utiliser:

.. py:method:: Canvas.create_bitmap(x, y, options ...)

        Retourne l'identifiant numérique de l'image bitmap créée sur le canevas appelant.

        *x* et *y* sont les coordonnées du point de référence qui précise où placer le bitmap.

        Les options sont :

        :arg activebackground: 
                Ces options précisent la couleur de fond, le bitmap et la couleur d'avant plan lorsque le bitmap est ``'active'``, c'est à dire lors du survol de la souris.
        :arg activebitmap:
        :arg activeforeground:
        :arg anchor:
                Le bitmap est positionné relativement au point *(x, y)*. La valeur par défaut est ``anchor='center'``, ce qui centre le bitmap sur la position *(x, y)*. Voir :ref:`ancrage` pour les valeurs d'ancrage. Par exemple, si vous indiquez ``anchor='ne'``, le bitmap est positionné de telle sorte que le point *(x, y)* est situé dans le coin supérieur droit (nord est) du bitmap.
        :arg background: 
                La couleur de fond du bitmap (son 0). Sa valeur par défaut est ``background=''`` ce qui veut dire transparent.
        :arg bitmap: 
                Le bitmap à afficher. Voir :ref:`bitmaps`.
        :arg disabledbackground: 
                Ces options précisent la couleur de fond, le bitmap et la couleur d'avant plan utilisés lorsque le bitmap est dans l'état (*state*) ``'disabled'``.
        :arg disabledbitmap:
        :arg disabledforeground:
        :arg foreground: 
                La couleur d'avant plan (son 1) du bitmap. Sa valeur par défaut est ``foreground='black'``.
        :arg state: 
                ``'normal'`` par défaut. Il vaut ``'active'`` lorsque la souris le survole. Mettre cette option à ``'disabled'`` pour l'empêcher de réagir à la souris, la mettre à ``'hidden'`` pour le rendre invisible.
        :arg tags: 
                Si c'est une chaîne seule, elle sert à marquer (*tag*) le bitmap. Utiliser un tuple de chaînes pour lui attribuer plusieurs marques. Voir :ref:`CANVAStags`.

.. _can_images:

Les images
==========

Pour afficher une image sur un canevas, utiliser:

.. py:method:: Canvas.create_image(x, y, option, ...)

        Retourne l'identifiant numérique de l'item image créé sur le canevas appelant.

        L'image est positionnée relativement au point *(x, y)*. Ces options sont :

        :arg activeimage: 
                Image à afficher lorsque la souris survole l'item. Pour les valeurs possibles, voir l'option **image** ci-dessous.
        :arg anchor:
                Par défaut, vaut ``'center'`` ce qui signifie que le texte est centré par rapport à la position *(x, y)*. Voir  :ref:`ancrage` pour les valeurs possibles. Par exemple, si ``anchor='s'``, l'image sera positionnée de sorte que le point *(x, y)* soit situé au milieu de son bord supérieur (sud).
        :arg disabledimage: 
                Image à afficher lorsque l'item est inactif (à l'état ``'disabled'``). Pour les valeurs possibles, voir **image** ci-dessous.
        :arg image:
                L'image à afficher, voir :ref:`images`, pour avoir des informations à propos de la création d'image qui peuvent être chargées dans les canevas.
        :arg state: 
                ``'normal'`` par défaut. Mettre cet option à ``'disabled'`` pour l'empêcher de réagir à la souris, la mettre à ``'hidden'`` pour la rendre invisible.
        :arg tags:
                Si c'est une chaîne seule, elle sert à marquer (*tag*) l'image. Utiliser un tuple de chaînes pour lui attribuer plusieurs marques. Voir :ref:`CANVAStags`.

.. _lignes:

Les lignes
==========

En général, une ligne est une succession de segments connectés les uns aux autres. Pour créer une ligne, utiliser:

.. py:method:: Canvas.create_line(x0, y0, x1, y1, ..., xn, yn, option, ...)

        La ligne est formée de segments qui joignent les points *(x0, y0)*, *(x1, y1)*, … *(xn, yn)*. Les options possibles sont :

        :arg activedash: 
                Ces options servent à préciser l'apparence de la ligne lorsque son état est ``'active'``, c'est à dire lorsque la souris la survole. Pour les valeurs possibles, voir les options **dash**, **fill**, **stipple**, and **width**. 
        :arg activefill:
        :arg activestipple:
        :arg activewidth:
        :arg arrow:
                Par défaut, la ligne n'est pas terminée par une flèche. Utiliser ``arrow='first'`` pour obtenir une flèche au point *(x0, y0)* de la ligne. Utilisez ``arrow='last'`` pour obtenir une flèche à l'autre extrémité. Utilisez ``arrow='both'`` pour en avoir à chaque extrémité.
        :arg arrowshape:
                Un tupe *(d1, d2, d3)* qui décrit la forme des flèches ajoutées par l'option **arrow**. La valeur par défaut est ``(8,10,3)``. Voir :ref:`style-extr`.
        :arg capstyle:
                Utiliser cette option pour préciser la forme des extrémités de la ligne. Voir :ref:`style-extr`. La valeur par défaut est ``'butt'``.
        :arg dash: 
                Pour produire une ligne hachurée, donner une valeur à cette option. Voir :ref:`Motifs-brise`. L'apparence par défaut est une ligne pleine.
        :arg dashoffset: 
                Si vous préciser un motif de hâchure, le comportement par défaut est d'utiliser le motif dès le début de la ligne. Utiliser cette option pour décaler la bordure du motif hachuré à une certaine distance par rapport au début de la ligne. Voir :ref:`Motifs-brise`.
        :arg disableddash: 
                Ces options servent à préciser l'apparence de la ligne lorsque son état est ``'disabled'``.
        :arg disabledfill:
        :arg disabledstipple:
        :arg disabledwidth:
        :arg fill:
                La couleur utilisée pour dessiner la ligne. La valeur par défaut est ``fill='black'``.
        :arg joinstyle: 
                Cette option contrôle l'apparence des jointures des côtés adjacents (lorsqu'il y en a plusieurs) de la ligne. Voir :ref:`style-extr`. La valeur par défaut est ``'round'``.
        :arg offset: 
                Pour les lignes en pointillés, cette option sert à régler finement le motif en cohérence avec ceux des objets adjacents. Voir :ref:`nuagepts`.
        :arg smooth:
                La bordure par défaut est formée de segments pour connecter les points qui définissent la ligne; Utilisez ``smooth=0`` pour obtenir ce comportement. Si vous utilisez ``smooth=1``, vous obtenez une courbe qui passe par ces points. Pour obtenir un segment avec ``smooth=1``, dupliquer les coordonnées de ses extrémités.
        :arg splinesteps:
                Si ``smooth=1``, chaque morceau de la courbe (entre deux points) est rendu à l'aide d'un certain nombre de petits segments. Cette option précise le nombre de segments utilisés pour cela; Sa valeur par défaut est ``splinesteps=12``.
        :arg state: 
                ``'normal'`` par défaut. Il vaut ``'active'`` lorsque la souris survole la ligne. Mettre cette option à ``'disabled'`` pour l'empêcher de réagir à la souris, la mettre à ``'hidden'`` pour la rendre invisible.
        :arg stipple:
                Pour dessiner une ligne en pointillé, indiquez un bitmap qui précise le motif à utiliser, par exemple ``stipple='gray25'``. Voir :ref:`bitmaps` pour les valeurs possibles.
        :arg tags:
                Si c'est une chaîne seule, elle sert à marquer (*tag*) la ligne. Utiliser un tuple de chaînes pour lui attribuer plusieurs marques. Voir :ref:`CANVAStags`.
        :arg width:
                L'épaisseur de la ligne. Vaut 1 pixel par défaut. Voir :ref:`dimensions` pour les valeurs possibles.

.. _ellipses-et-cercles:

Les ellipses et cercles
=======================

Pour créer l'ellipse (ou le cercle) qui s'inscrit dans le rectangle (ou le carré) *(x0, y0)*, *(x1, y1)* où les premières coordonnées sont celles du coin supérieur gauche et les secondes celles du coin inférieur droit, utiliser:

.. py:method:: Canvas.create_oval(x0, y0, x1, y1, option, ...)

        Retourne l'identifiant numérique de l'ellipse créée. Les options sont:

        :arg activedash: 
                Ces options servent à préciser l'apparence du rectangle lorsque son état est ``'active'``, c'est à dire lorsque la souris le survole. Pour les valeurs possibles, voir les options **dash**, **fill**, **outline**, **outlinestipple**, **stipple**, and **width**. 
        :arg activefill:
        :arg activeoutline:
        :arg activeoutlinestipple:
        :arg activestipple:
        :arg activewidth:
        :arg dash: 
                Sert à réaliser une bordure hachurée autour de l'ellipse. Utiliser cette option pour préciser un motif de hachure. Voir :ref:`Motifs-brise`.
        :arg dashoffset: 
                Utiliser cette option pour décaler la bordure du motif hachuré à un autre point du cycle. Voir :ref:`Motifs-brise`.
        :arg disableddash: 
                Ces options servent à préciser l'apparence de l'ellipse lorsque son état est ``'disabled'``.
        :arg disabledfill:
        :arg disabledoutline:
        :arg disabledoutlinestipple:
        :arg disabledstipple:
        :arg disabledwidth:
        :arg fill:
                Par défaut, l'intérieur de l'ellipse  est transparent et vous pouvez obtenir ce comportement avec ``fill=''``. Vous pouvez aussi utiliser une couleur de remplissage. Voir :ref:`couleurs`.
        :arg offset: 
                Utiliser cette option pour modifier le décalage du motif de «pointillé» de l'intérieur de l'ellipse. Voir :ref:`nuagepts`.
        :arg outline:
                Couleur de la bordure. Par défaut, ``outline='black'``.
        :arg outlineoffset: 
                Utiliser cette option pour ajuster le motif de «pointillé» de la ligne de bordure. Voir :ref:`nuagepts`.
        :arg stipple:
                Un bitmap pour indiquer le motif de pointillé à utiliser pour remplir l'intérieur de l'ellipse.  Par défaut, ``stipple=''``, ce qui indique l'utilisation potentielle d'une couleur de remplissage. Une valeur typique serait ``stipple='gray25'``. N'a pas d'effet sauf si une couleur a été indiquée pour l'option **fill**. Voir :ref:`bitmaps`.
        :arg outlinestipple: 
                Utiliser cette option pour une ligne de bordure en pointillé. Le motif est précisé à l'aide d'un bitmap (voir **stipple** ci-dessus); Voir :ref:`bitmaps`.
        :arg state: 
                ``'normal'`` par défaut. Il vaut ``'active'`` lorsque la souris le survole. Mettre cet option à ``'disabled'`` pour l'empêcher de réagir à la souris, la mettre à ``'hidden'`` pour le rendre invisible.
        :arg tags:
                Si c'est une chaîne seule, elle sert à marquer (*tag*) l'ellipse. Utiliser un tuple de chaînes pour lui attribuer plusieurs marques. Voir :ref:`CANVAStags`.
        :arg width:
                Largeur de la bordure. Vaut 1 pixel par défaut. Utiliser ``width=0`` Pour rendre la bordure invisible. Voir :ref:`dimensions`. 

.. _polygones:

Les polygones
=============

Un polygone est une ligne fermée. Ainsi, il possède une ligne de contour (formée de segments) et une zone intérieure. Pour le définir, on utilise une série de points ``[(x0, y0), (x1, y1), … (xn, yn)]``. Le premier point et le dernier sont reliés par un segment afin de le fermer. Pour créer un polygone, utiliser:

.. py:method:: Canvas.create_polygon(x0, y0, x1, y1, ..., option, ...)

        Retourne l'identifiant numérique du polygone créé. Ses options sont:

        :arg activedash: 
                Ces options servent à préciser l'apparence du polygone lorsque son état est ``'active'``, c'est à dire lorsque la souris le survole. Pour les valeurs possibles, voir les options **dash**, **fill**, **outline**, **outlinestipple**, **stipple**, and **width**. 
        :arg activefill:
        :arg activeoutline:
        :arg activeoutlinestipple:
        :arg activestipple:
        :arg activewidth:
        :arg dash: 
                Sert à réaliser une bordure hachurée autour du polygone. Utiliser cette option pour préciser un motif de hâchure. Voir :ref:`Motifs-brise`.
        :arg dashoffset: 
                Utiliser cette option pour décaler la bordure du motif hachuré à un autre point du cycle. Voir :ref:`Motifs-brise`.
        :arg disableddash: 
                Ces options servent à préciser l'apparence du polygone lorsque son état est ``'disabled'``.
        :arg disabledfill:
        :arg disabledoutline:
        :arg disabledoutlinestipple:
        :arg disabledstipple:
        :arg disabledwidth:
        :arg fill:
                Par défaut, l'intérieur du polygone est transparent et vous pouvez obtenir ce comportement avec ``fill=''``. Vous pouvez aussi utiliser une couleur de remplissage. Voir :ref:`couleurs`.
        :arg joinstyle: 
                Cette option contrôle l'apparence des jointures des côtés adjacents du polygone. Voir :ref:`style-extr`.
        :arg offset: 
                Utiliser cette option pour modifier le décalage du motif de «pointillé» de l'intérieur du polygone. Voir :ref:`nuagepts`.
        :arg outline:
                Couleur de la bordure; par défaut, ``outline=''``, ce qui rend la bordure transparente.
        :arg outlineoffset: 
                Utiliser cette option pour ajuster le motif de «pointillé» de la ligne de bordure. Voir :ref:`nuagepts`.
        :arg outlinestipple: 
                Utiliser cette option pour une ligne de bordure en pointillé. Le motif est précisé à l'aide d'un bitmap; Voir :ref:`bitmaps`.
        :arg smooth:
                La bordure par défaut est formée de segments pour connecter les points qui définissent le polygone; Utilisez ``smooth=0`` pour obtenir ce comportement. Si vous utilisez ``smooth=1``, vous obtenez une courbe qui passe par ces points. Pour obtenir un segmente avec ``smooth=1``, dupliquer les coordonnées de ses extrémités.
        :arg splinesteps:
                Si ``smooth=1``, chaque morceau de la courbe (entre deux points) est rendu à l'aide d'un certain nombre de petits segments. Cette option précise le nombre de segments utilisés pour cela; Sa valeur par défaut est ``splinesteps=12``.
        :arg state: 
                ``'normal'`` par défaut. Il vaut ``'active'`` lorsque la souris le survole. Mettre cette option à ``'disabled'`` pour l'empêcher de réagir à la souris, la mettre à ``'hidden'`` pour le rendre invisible.
        :arg stipple:
                Un bitmap pour indiquer le motif de pointillé à utiliser pour remplir l'intérieur du polygone. Par défaut, ``stipple=''``, ce qui indique l'utilisation potentielle d'une couleur de remplissage. Une valeur typique serait ``stipple='gray25'``. N'a pas d'effet sauf si une couleur a été indiquée pour l'option ``fill`` . Voir :ref:`bitmaps`.
        :arg tags:
                Si c'est une chaîne seule, elle sert à marquer (*tag*) le polygone. Utiliser un tuple de chaînes pour lui attribuer plusieurs marques. Voir :ref:`CANVAStags`.
        :arg width:
                Largeur de la bordure. Vaut 1 pixel par défaut. Utiliser ``width=0`` Pour rendre la bordure invisible. Voir :ref:`dimensions`. 

.. _rectangles:

Les rectangles
==============

Un rectangle est défini par deux points : *(x0, y0)* pour son coin supérieur gauche et *(x1, y1)* pour son coin inférieur droit.

Par exemple, un rectangle dont le coin supérieur gauche est *(100,100)* et le coin inférieur droit est *(102,102)* est un carré de deux pixels par deux pixels qui inclut le pixel *(101,101)* mais pas le pixel *(102,102)*.

Les rectangles sont formés deux parties:

* Les bords haut et gauche de la ligne de bordure font partie du rectangle mais pas les bords bas et droit. Par défaut cette bordure est noire et a une épaisseur de 1 pixel.

  Par exemple, considérons le rectangle dont le coin supérieur gauche est *(10,10)* et le coin inférieur droit est *(11,11)*. Si vous annulez la bordure (``width=0``) et utilisez une couleur de remplissage verte (``fill='green'``), vous obtenez un pixel vert à la position *(10, 10)*. Cependant, dans les même conditions, si vous laissez par défaut la valeur de width, vous obtenez quatre pixels noirs aux positions *(10,10)*, *(10,11)*, *(11,10)*, and *(11,11)*.

* L'intérieur du rectangle est la zone délimité par la ligne de bordure. par défaut, il est transparent. 

Pour créer un rectangle sur le canevas: 

.. py:method:: Canvas.create_rectangle(x0, y0, x1, y1, option, ...)

        Retourne l'identifiant numérique du rectangle créé. Ses options sont: 

        :arg activedash: 
                Ces options servent à préciser l'apparence du rectangle lorsque son état est ``'active'``, c'est à dire lorsque la souris le survole. Pour les valeurs possibles, voir les options **dash**, **fill**, **outline**, **outlinestipple**, **stipple**, and **width**. 
        :arg activefill:
        :arg activeoutline:
        :arg activeoutlinestipple:
        :arg activestipple:
        :arg activewidth:
        :arg dash: 
                Sert à réaliser une bordure hachurée autour du rectangle. Utiliser cette option pour préciser un motif de hachure. Voir :ref:`Motifs-brise`.
        :arg dashoffset: 
                Utiliser cette option pour décaler la bordure du motif hachuré à un autre point du cycle. Voir :ref:`Motifs-brise`.
        :arg disableddash: 
                Ces options servent à préciser l'apparence du rectangle lorsque son état est ``'disabled'``.
        :arg disabledfill:
        :arg disabledoutline:
        :arg disabledoutlinestipple:
        :arg disabledstipple:
        :arg disabledwidth:
        :arg fill:
                Par défaut, l'intérieur du rectangle est transparent et vous pouvez obtenir ce comportement avec ``fill=''``. Vous pouvez aussi utiliser une couleur de remplissage. Voir :ref:`couleurs`.
        :arg offset: 
                Utiliser cette option pour modifier le décalage du motif en «pointillé» de l'intérieur du rectangle. Voir :ref:`nuagepts`.
        :arg outline:
                Couleur de la bordure. Par défaut, ``outline='black'``.
        :arg outlineoffset: 
                Utiliser cette option pour ajuster le motif en «pointillé» de la ligne de bordure. Voir :ref:`nuagepts`.
        :arg outlinestipple: 
                Utiliser cette option pour une ligne de bordure en pointillé. Le motif est précisé à l'aide d'un bitmap; Voir :ref:`bitmaps`.
        :arg state: 
                ``'normal'`` par défaut. Il vaut ``'active'`` lorsque la souris le survole. Mettre cette option à ``'disabled'`` pour l'empêcher de réagir à la souris, la mettre à ``'hidden'`` pour le rendre invisible.
        :arg stipple:
                Un bitmap pour indiquer le motif en pointillé à utiliser pour remplir l'intérieur du rectangle. Par défaut, ``stipple=''``, ce qui indique l'utilisation potentielle d'une couleur de remplissage. Une valeur typique serait ``stipple='gray25'``. N'a pas d'effet sauf si une couleur a été indiquée pour l'option ``fill`` . Voir :ref:`bitmaps`.
        :arg tags:
                Si c'est une chaîne seule, elle sert à marquer (*tag*) le rectangle. Utiliser un tuple de chaînes pour lui attribuer plusieurs marques. Voir :ref:`CANVAStags`.
        :arg width:
                Largeur de la bordure. Vaut 1 pixel par défaut. Utiliser ``width=0`` Pour rendre la bordure invisible. Voir :ref:`dimensions`. 

.. _textes:

Les textes
==========

Vous pouvez afficher une ou plusieurs lignes de texte sur un canevas en utilisant:

.. py:method:: Canvas.create_text(x, y, option, ...)

        Retourne l'identifiant numérique de l'objet textuel ainsi créé. Ses options sont:

        :arg activefill: 
                Couleur de remplissage à utiliser lorsque la souris est au-dessus.
        :arg activestipple: 
                Le motif en pointillé à utiliser lorsque le texte est ``'active'`` (au survol de la souris). Pour des valeurs possible, voir l'option **stipple** ci-dessous.
        :arg anchor:
                Par défaut, vaut ``'center'`` ce qui signifie que le texte est centré par rapport à la position *(x,y)*. Voir :ref:`ancrage` pour les valeurs possibles.
        :arg disabledfill: 
                Couleur de remplissage lorsque l'item est dans l'état (state) ``'disabled'``.
        :arg disabledstipple: 
                Le motif en pointillé à utiliser lorsque le texte est ``'disabled'``. Pour des valeurs possibles, voir l'option **stipple** ci-dessous.
        :arg fill:
                Couleur du texte, noir par défaut. Voir :ref:`couleurs`.
        :arg font:
                Utiliser cette option pour changer la police de caractères. Voir :ref:`polices`.
        :arg justify:
                Gère l'alignement en cas d'affichage multiligne : ``'left'`` pour gauche, ``'center'`` pour centré et ``'right'`` pour droit.
        :arg offset: 
                Le décalage du motif en pointillé à utiliser pour le texte. Pour plus d'informations, voir :ref:`nuagepts`.
        :arg state: 
                ``'normal'`` par défaut. Mettre cet option à ``'disabled'`` pour l'empêcher de réagir à la souris, la mettre à ``'hidden'`` pour le rendre invisible.
        :arg stipple:
                Un bitmap qui indique le motif pointillé qui sera utilisé pour le rendu du texte. La valeur par défaut est `` stipple=''``, ce qui indique un rendu «solide». Une valeur typique serait ``stipple='gray25'``. Voir :ref:`bitmaps`.
        :arg tags:
                Si c'est une chaîne seule, elle sert à marquer (*tag*) le texte. Utiliser un tuple de chaînes pour lui attribuer plusieurs marques. Voir :ref:`CANVAStags`.
        :arg text:
                Le texte à afficher sous la forme d'une chaîne de caractères. Utiliser '\n' pour forcer les sauts de ligne.
        :arg width:
                Si aucune valeur n'est indiquée, le texte est affiché dans un rectangle aussi long que la plus longue ligne. Si vous indiquez explicitement une largeur, chaque ligne du texte sera coupée afin de ne pas dépasser cette largeur. Voir :ref:`dimensions`.

Vous pouvez modifier ou récupérer le texte affiché:

* Pour récupérer le texte d'un tel item d'identifiant ``id`` sur un canevas ``can``, utiliser ``can.itemcget(id, 'text')``.

* Pour remplacer le texte d'un tel item par une chaîne ``ch``, utiliser ``can.itemconfigure(id, text=ch)``.

Plusieurs méthodes des canevas vous permettent d'autres manipulations du texte. Voir :ref:`CANVASmeth`, et plus particulièrement :py:meth:`~Canvas.dchars`, :py:meth:`~Canvas.focus`, :py:meth:`~Canvas.icursor`, :py:meth:`~Canvas.index`, et :py:meth:`~Canvas.insert`. 

.. _fenêtres:

Les fenêtres
============

Il est possible de placer n'importe quel widget de tkinter sur un canevas en utilisant un item fenêtre. Une fenêtre est une zone rectangulaire qui peut contenir un widget de tkinter. Le widget doit être un enfant de la même fenêtre principale que le canevas, ou l'enfant d'un widget lui-même situé dans cette fenêtre principale.

Si vous voulez insérer un objet composé de plusieurs widgets sur un canevas, vous pouvez utiliser cette méthode pour placer un cadre (*frame*) dans le canevas et, ensuite, placer d'autres widgets dans ce cadre.

Pour créer une fenêtre dans un canevas, utiliser:

.. py:method:: Canvas.create_window(x, y, option, ...)

        Retourne l'identifiant numérique de la fenêtre créée. Ses options sont:

        :arg anchor:
                Par défaut, vaut ``'center'`` ce qui signifie que la fenêtre est centrée par rapport à la position *(x,y)*. Voir :ref:`ancrage` pour les valeurs possibles.
        :arg height:
                La hauteur de la zone réservée pour la fenêtre. Si non renseignée, la fenêtre s'ajuste à la hauteur de son contenu. Voir :ref:`dimensions` pour les valeurs possibles.
        :arg state: 
                ``'normal'`` par défaut. Mettre cette option à ``'disabled'`` pour empêcher la fenêtre de réagir à la souris, la mettre à ``'hidden'`` pour la rendre invisible.
        :arg tags:
                Si c'est une chaîne seule, elle sert à marquer (*tag*) la fenêtre. Utiliser un tuple de chaînes pour lui attribuer plusieurs marques. Voir :ref:`CANVAStags`.
        :arg width:
                La largeur de la zone réservée pour la fenêtre. Si non renseignée, la fenêtre s'ajuste à la largeur de son contenu.
        :arg window:
                Utiliser ``window=w`` où ``w`` est le widget que vous souhaitez placer sur le canevas. 
