.. _CANEVAS:

************************
Les Canevas (``Canvas``)
************************

Un canevas est une zone rectangulaire destinée à contenir des dessins ou d'autres figures complexes. Vous pouvez y placer des graphiques, du texte, des composants graphiques (`widgets`) ou des cadres (`frames`). Veuillez consulter les sections suivantes pour les méthodes qui servent à créer de tels objet sur un canevas:

* :py:meth:`~Canvas.create_arc` : Une portion d'ellipse. Voir :ref:`arcs`.

* :py:meth:`~Canvas.create_bitmap` : Une image de type bitmap. Voir :ref:`can_bitmaps`.

* :py:meth:`~Canvas.create_image` : Une image «plus riche». Voir :ref:`can_images`.

* :py:meth:`~Canvas.create_line` : Un ou plusieurs segments. Voir :ref:`lignes`.

* :py:meth:`~Canvas.create_oval` : Une ellipse; Utiliser cette méthode pour dessiner des cercles qui sont des cas particuliers d'ellipses. Voir :ref:`ellipses-et-cercles`.

* :py:meth:`~Canvas.create_polygon` : Un polygone. Voir :ref:`polygones`.

* :py:meth:`~Canvas.create_rectangle` : Un rectangle. Voir :ref:`rectangles`.

* :py:meth:`~Canvas.create_text` : Une annotation textuelle. Voir :ref:`textes`.

* :py:meth:`~Canvas.create_window` : Une fenêtre rectangulaire. Voir :ref:`fenêtres`.

Pour créer un objet de type Canvas:

.. py:class:: Canvas(parent, option=valeur, ...)

        Le constructeur retourne le nouveau widget canvas. Ses options sont:

        :arg borderwidth:
                (ou **bd**) Largeur de la bordure du canvas. Voir :ref:`dimensions`.
                La valeur par défaut est deux pixels. 
        :arg background:
                (ou **bg**) Couleur de fond du canvas. La valeur par défaut est un gris léger, à peu près ``'#E4E4E4'``.
        :arg closeenough:
                Un flottant qui précise la distance minimale entre la souris et un item pour considérer qu'elle est dedans. La valeur par défaut est 1.0.
        :arg confine:
                Si True (la valeur par défaut), il n'est pas possible de faire défiler le canvas en dehors de sa zone de visualisation (`scrollregion`), voir plus ci-dessous.
        :arg cursor:
                Pointeur de la souris utilisé sur le canvas. Voir “Cursors”.
        :arg height:
            Hauteur du canvas. Voir “Dimensions”.
        :arg highlightbackground:
                Couleur de la ligne de focus lorsque le canvas n'a pas le focus. Voir “Focus: routing keyboard input”.
        :arg highlightcolor:
                Couleur de la ligne de focus lorsque le canvas a le focus.
        :arg highlightthickness:
                Épaisseur de la ligne de focus. La valeur par défaut est 1.
        :arg relief:
                Le style de relief du canvas. La valeur par défaut est 'flat'. Voir “Relief styles”.
        :arg scrollregion:
                Un tuple ``(w, n, e, s)`` qui défini la zone du canvas accessible par défilement. w désigne le côté gauche, n le bord haut, e le côté droit et s le bord bas.
        :arg selectbackground:
                La couleur de fond utilisée pour afficher l'item sélectionné.
        :arg selectborderwidth:
                L'épaisseur de la bordure de l'item sélectionné.
        :arg selectforeground:
                La couleur d'avant plan utilisée pour mettre en valeur l'item sélectionné.
        :arg takefocus:
                Normalement, le focus (see Section 53, “Focus: routing keyboard input”) est obtenu en utilisant la touche Tab seulement si un gestionnaire d'événement a été prévu pour cela (see Section 54, “Events” for an overview of keyboard bindings). Si vous positionnez la valeur de cette option à 1, le canvas obtiendra le focus de manière ordinaire. Positionnez la à '' pour obtenir le comportement «normal».
        :arg width:
                Largeur du canvas. Voir “Dimensions”.
        :arg xscrollincrement:
                Normalement, on peut faire défiler un canvas horizontalement à n'importe qu'elle position. Vous pouvez obtenir ce comportement en positionnant cette opition à 0. Si vous donnez une valeur positive à cette option, le canvas défile en utilisant des multiples de cette valeur. Elle sera en outre utilisée comme unité de défilement horizontal comme quand l'utilisateur clique sur les flèches situées aux extrémités d'une barre de défilement. Voir “The Scrollbar widget”.
        :arg xscrollcommand:
                Si le canvas est muni d'une barre défilement, positionnez cette option en utilisant la méthode ``set()`` de la barre.
        :arg yscrollincrement:
                Fonctionne de manière similaire à **xscrollincrement**, mais pour un défilement vertical.
        :arg yscrollcommand:
                Fonctionne de manière similaire à **xscrollcommand**, mais pour une barre de défilement vertical.

Le système de coordonnées
=========================

Parce qu'un canevas peut être plus large que sa fenêtre de visualisation et qu'il peut être équipé de barres de défilement afin de le déplacer, il y a deux systèmes de coordonnées pour chaque canvas:

* Les coordonnées d'un point dans la fenêtre de vue; elles sont relatives au bord supérieur gauche de cette fenêtre.

* Les coordonnées d'un point dans le canvas lui-même.

La liste d'affichage
====================

La liste d'affichage se réfère à la séquence de tous les items qui se trouvent sur le canvas, de l'arrière plan, *background* (le bas de la liste d'affichage) vers l'avant plan, *foreground* (le haut de cette liste).

Si deux items se recouvrent, l'item au-dessus de l'autre dans la liste d'affichage désigne celui qui est le plus proche de l'avant plan, c'est à dire qui est vu comme au-dessus de l'autre sur l'affichage. Par défaut, lorsqu'un item est créé, il est placé tout en haut de la liste d'affichage (et donc il apparaît au dessus des items déjà affichés), mais il est possible de ré-ordonner la liste d'affichage.

Les identifiants numériques
===========================

Chaque item affiché sur le canvas possède un identifiant numérique (simple entier) unique, il s'agit de la valeur retournée par le «constructeur» (``create_*()``) lors de sa création.

Les marques (`tags`)
====================

Une marque, `tag`, est une chaîne de caractères qu'on peut associée à un ou plusieurs items du canvas.

* Une marque peut être associée à autant d'items que l'on veut sur le canvas, 0 inclus.

* Un item peut posséder autant de marques que souhaitées, 0 inclus.

Les marques ont de nombreux usages. Par exemple, si vous dessinez une carte sur un canvas et que vous utilisez des textes pour donner le nom des rivières, vous pourriez marquer tous ces items textuels avec 'rivEtiq'. Cela vous permettrait d'agir globalement sur les étiquettes en utilisant cette marque afin, par exemple de changer leur couleur ou de les supprimer.

Identification des items graphiques
===================================

Un argument ``tagOrId`` se réfère à un ou plusieur items du canvas.

* Si l'argument ``tagOrId`` est un entier, il est considéré comme un identifiant numérique et il s'applique à l'unique item qui le possède. Voir “Canvas object IDs”.

* Si cet argument est une chaîne de caractère, il est interprété comme une marque et sélectionne tous les items qui ont cette marque (s'il y en a). Voir “Canvas tags”. 

Méthodes des Canevas
====================

Tous les Canvas disposent de ces méthodes (outre celles qui servent à créer des items et qui sont présentées plus loin):

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
  * :py:meth:`~Canvas.yview_moveto`
  * :py:meth:`~Canvas.yview_scroll`

.. py:method:: Canvas.addtag_above(newTag, tagOrId)

        Appose une nouvelle marque ``newTag`` à l'item situé juste au-dessus de celui qui est sélectionné par `tagOrId` dans la liste d'affichage. l'argument ``newTag``, donné sous la forme d'une chaîne de caractère, est la marque qu'on souhaite apposer.

.. py:method:: Canvas.addtag_all(newTag)

        Attache la marque donné à tous les items qui sont présents sur le canevas.

.. py:method:: Canvas.addtag_below(newTag, tagOrID)

        Attache la nouvelle marque ``newTag`` à tous les items situés en-dessous de celui qui est indiqué par l'identifiant numérique ou la marque ``tagOrId``. L'argument ``newTag`` est une chaîne de caractères.

.. py:method:: Canvas.addtag_closest(newTag, x, y, halo=None, start=None)

        Ajoute une marque à l'item le plus proche de la position indiquée par les coordonnées (de la fenêtre de vue). Si un ou plusieurs items sont à la même distanche, celui qui est le plus haut dans la liste d'affichage (qui recouvre les autres) est sélectionné.
        Utilisez l'argument ``halo`` afin d'augmenter la taille effective du point. Par exemple, une valeur de 5 indique le traitement de tous les objets qui recouvrent le disque de centre `(x, y)`.

        Si l'identifiant d'un objet est utilisé pour l'argument start, cette méthode marque l'item qui est le plus haut dans la liste d'affichage tout en étant en dessous de celui qui est aisni identifié.

.. py:method:: Canvas.addtag_enclosed(newTag, x1, y1, x2, y2)

        Ajoute la marque ``newTag`` à tous les items qui sont recouvert complètement par le rectangle dont le coin supérieur gauche est *(x1, y1)* et le coin inférieur droit est *(x2, y2)*. 

.. py:method:: Canvas.addtag_overlapping(newTag, x1, y1, x2, y2)

        Comme la méthode précédente à cela près que les items marqué sont tous ceux qui ont au moins un point commun avec le rectangle.

.. py:method:: Canvas.addtag_withtag(newTag, tagOrId)

        Ajoute la marque ``newTag`` à (aux) l'objet(s) identifié(s) par ``tagOrId``. 

.. py:method:: Canvas.bbox(tagOrId=None)

        Retourne un tuple ``(x1, y1, x2, y2)`` qui décrit un rectangle qui renferme tous les objets identifiés par ``tagOrId``. Si l'argument n'est pas précisé, le rectangle retourné est le plus petit qui contient tous les items présents dans le canevas. Le coin supérieur gauche du rectangle est *(x1, y1)* et son coin inférieur droit est (x2, y2).

.. py:method:: Canvas.canvasx(screenx, gridspacing=None)

        Retourne la coordonnées x du canevas qui correspond à la coordonnée x d'affichage précisée par ``screenx``. Si l'argument ``gridspacing``est précisé, la valeur de x relative au canevas est arrondi au plus proche multiple de cette valeur.

.. py:method:: Canvas.canvasy(screeny, gridspacing=None)

        Similaire à la méthode précédente mais pour y.

.. py:method:: Canvas.coords(tagOrId, x0, y0, x1, y1, ..., xn, yn)

        Si vous précisez uniquement l'argument ``tagOrId``, elle retourne un tuple contenant les coordonnées du plus en dessous ou de l'unique item précisé par cet argument. Le nombre des coordonnées dépend du type d'item. Dans la plupart des cas, il est de la forme (x1, y1, x2, y2) décrivant la boîte englobant (*bounding box*) de l'item.

        Vous pouvez déplacer un item en précisant ses nouvelles coordonnées.

.. py:method:: Canvas.dchars(tagOrId, first=0, last=first)

        Supprime des caractères d'un ou d'items textuels. Tous les caractères situés entre first et last (inclus) sont supprimés, ces paramètres indiquant une position entière ou la fin du texte via la chaîne ``'end'``. Par exemple, pour un canevas ``C`` et un item de marque ``'I'``, C.dchars('I', 1, 1) supprime le second caractère.

.. py:method:: Canvas.delete(tagOrId)

        Supprime le ou les items indiqués par ``tagOrId``. Il n'y a pas d'erreurs si aucun item ne correspond à ``tagOrId``.

.. py:method:: Canvas.dtag(tagOrId, tagToDelete)

        Supprime la marque ``tagToDelete`` de (ou des) l'item(s) associé(s) à ``tagOrId`` from the object or objects specified by tagOrId. 

.. py:method:: Canvas.find_above(tagOrId)

        Retourne l'identifiant numérique de l'item situé juste au dessus de celui qui est sélectionné par ``tagOrId``. S'il y en a plusieurs, on utilise le plus haut dans la liste d'affichage. Si l'item précisé par ``tagOrId`` est le plus haut, la méthode returne un tuple vide ``()``.

.. py:method:: Canvas.find_all()

        Retourne une liste qui contient tous les identifiants numériques de tous les items du canvas, du plus bas au plus haut.

.. py:method:: Canvas.find_below(tagOrId)

        Retourne l'identifiant numérique de l'item situé juste en dessous de celui qui est associé à ``tagOrId``. Si plusieurs items correspondent, on obtient le plus bas dans la liste d'affichage. Si l'item précisé par ``tagOrId`` est le plus bas, la méthode retourne un tuple vide ``()``.

.. py:method:: Canvas.find_closest(x, y, halo=None, start=None)

        Retourne un tuple contenant l'identifiant numérique d'un seul item, celui qui est le plus proche du point (x, y). Si plusieurs items sont sélectionnés, c'est celui qui est le plus haut dans la liste d'affichage. Si aucun item n'est sélectionné, retourne une liste vide. Utiliser l'argument ``halo`` afin d'augmenter la taille effective du point. Tout item situé à une distance inférieur à ``halo`` de (x, y) le coupe. argument to increase the effective size of the point. For example, halo=5 would treat any object within 5 pixels of (x, y) as overlapping. Si ``start`` est renseigné, en utilisant une marque ou un identifiant (la marque sélectionne l'item le plus bas), l'item le plus proche et situé en-dessous de ``start`` est choisi.

.. py:method:: Canvas.find_enclosed(x1, y1, x2, y2)

        Retourne la liste des identifiants numériques des items situés entièrement à l'intérieur du rectangle déterminé par (x1, y1) (coin supérieur gauche) et (x2,y2) (coin inférieur droit). 

.. py:method:: Canvas.find_overlapping(x1, y1, x2, y2)

        Similaire à la méthode précédente, mais sélectionne tous les items qui ont au moins un point commun avec le rectangle.

.. py:method:: Canvas.find_withtag(tagOrId)

        Retourne la liste des identifiants numériques des items sélectionné par ``tagOrId``.

.. py:method:: Canvas.focus(tagOrId=None)

        Donne le focus à l'item sélectionné par ``tagOrId``. Si plusieurs sont sélectionnés, donne le focus au premier de la liste d'affichage qui permet un curseur d'insertion. Si aucun n'item ne satisfait cette condition ou si le caneva n'a pas le focus, le focus n'est pas modifié. Si l'argument est omis, l'identifiant de l'item qui a le focus est retourné ou ``''`` si aucun ne l'a.

.. py:method:: Canvas.gettags(tagOrId)

        If tagOrId is an object ID, returns a list of all the tags associated with that object. If the argument is a tag, returns all the tags for the lowest object that has that tag. 

.. py:method:: Canvas.icursor(tagOrId, index)

        En supposant que l'item sélectionné permet l'insertion de texte et qu'il a le focus, positionne le curseur d'insertion à la position ``index`` lequel est soit un entier ou la chaîne 'end'. N'a pas d'effet autrement.

.. py:method:: Canvas.index(tagOrId, specifier)

        Retourne l'index (entier) du ``specifier`` donné dans l'item textuel sélection par ``tagOrId`` (le plus bas s'il y en a plusieurs). Returns the integer index of the given specifier in the text item specified by tagOrId (the lowest one that, if tagOrId specifies multiple objects). La valeur de retour est une position dans une chaîne qui suit les convention de Python, 0 signifie avant le premier caractère. L'argument ``specifier`` peut être :

        * 'insert', pour retourner la position courante du curseur d'insertion.

        * 'end', pour retourner la position qui suit le dernier caractère.

        * 'sel.first', pour retourner la position initiale de la zone de sélection. Si une telle zone n'existe pas, tkinter produira une exception du type ``TclError``.

        * 'sel.last', pour retourner la position de la fin de la zone de sélection. De même, tkinter lève une exception si une telle zone n'existe pas.

        * Une chaîne de la forme '@x,y' pour retourner l'index du caractère situé à la position (x, y). Si cette position est située au-dessus ou à gauche de l'item textuel, la méthode retourne 0. Si elle est située en-dessous ou à droite, la méthode retourne l'index de fin de l'item. 

.. py:method:: Canvas.insert(tagOrId, beforeThis, text)

        Insère la chaîne de cararctère `text` dans le ou les items donnés via ``tagOrId``, à la position déterminée par ``beforeThis``: 'insert', 'end', 'sel.first' et 'sel.last' ou un entier (index) ou '@x,y' (x et y à remplacer par des entiers).

.. py:method:: Canvas.itemcget(tagOrId, option)

        Retourne la valeur de l'``option`` de configuration (précisé par une chaîne de caractère) pour l'item sélectionné (ou pour l'item le plus bas si plusieurs sont sélectionnés par ``tagOrId``. C'est très similaire à la méthode ``cget()`` pour les widgets.

.. py:method:: Canvas.itemconfigure(tagOrId, option, ...)

        Si aucune option n'est indiquée, retourne un dictionnaire dont les clés sont les options possibles pour l'item donné par ``tagOrId`` (ou le plus bas s'il y en a plusieurs). Autrement, modifie la ou les options données sous la forme ``option=valeur``.

.. py:method:: Canvas.move(tagOrId, dx, dy)

        Déplace les items donnés via ``tagOrId`` by adding dx à leur coordonnés x et dy à leurs coordonnées y.

.. py:method:: Canvas.postscript(option, ...)

        Generates an Encapsulated PostScript representation of the canvas's current contents. The options include:
        colormode	Use 'color' for color output, 'gray' for grayscale, or 'mono' for black and white.
        file	If supplied, names a file where the PostScript will be written. If this option is not given, the PostScript is returned as a string.
        height	How much of the Y size of the canvas to print. Default is the entire visible height of the canvas.
        rotate	If false, the page will be rendered in portrait orientation; if true, in landscape.
        x	Leftmost canvas coordinate of the area to print.
        y	Topmost canvas coordinate of the area to print.
        width	How much of the X size of the canvas to print. Default is the visible width of the canvas. 

.. py:method:: Canvas.scale(tagOrId, x, y, sx, sy)

        Mise à l'échelle de tous les objets relativement au point de référence ``P=(x, y)``. Les facteurs d'échelle ``sx`` et ``sy`` sont basés sur une valeur de 1.0 qui signifie aucune mise à l'échelle. Chaque point des items sélectionné sont déplacés de façon que leurs distances en x (resp. en y) au point P sont multipliées par sx (resp. sy). Cette méthode ne modifie pas la taille des textes mais peut les déplacer.

.. py:method:: Canvas.scan_dragto(x, y, gain=10.0)

        Sert à faire défiler le canevas. voir la méthode :py:meth:`~Canvas.scan_mark()`.

.. py:method:: Canvas.scan_mark(x, y)

        Cette méthode sert à réaliser des défilement rapide du canevas. L'intention est que l'utilisateur puisse faire défiler le canvas en appuyant sur un bouton de la souris (sans relâcher) et en la déplaçant jusqu'au relâchement. Pour réaliser cette fonctionnalité, lier l'événement souris «bouton appuyé» à un gestionnaire qui appelle cette méthode en positionnant x et y à la position de la souris. Ensuite, lier l'événement '<Motion>' à un gestionnaire qui, en supposant que le bouton de la souris n'est pas relâché, appelle :py:meth:`~Canvas.scan_dragto(x, y, gain)` en positionnant x et y aux coordonnées de la souris ; le paramètre ``gain`` sert à contrôler le rythme du défilement, sa valeur par défaut est 10.0. Utiliser une valeur plus grande pour accélérer le défilement.

.. py:method:: Canvas.select_adjust(tagOrId, index)

        Trouve l'extrémité de la selection courante la plus proche du caractère donné par ``index`` et l'ajuste de façon que la nouvelle sélection contienne ce caractère. L'autre extrémité de la sélection devient le point d'ancrage pour une utilisation ultérieure de :py:meth:`~Canvas.select_to`. Si il n'y avait aucune sélection, se comporte comme la méthode  :py:meth:`~Canvas.select_to`.

        Pour les valeurs possible de ``index``, voir :py:meth:`~Canvas.insert`. 

.. py:method:: Canvas.select_clear()

        Supprime la sélection courante (pas ce qui est sélectionné) si elle existe, autrement ne fait rien.

.. py:method:: Canvas.select_from(tagOrId, index)

        Positionne le point d'ancrage de la sélection juste avant le caractère précisé par ``index`` dans le texte de l'item donné par ``tagOrId``. Cette méthode ne modifie pas une sélection existante, elle positionne simplement la marque de fin de sélection pour l'utilisation ultérieur de :py:meth:`~Canvas.select_to`.

.. py:method:: Canvas.select_item()

        S'il y a une sélection de texte dans ce canevas, retourne l'identiant de l'item texte qui contient la sélection. Sinon, retourne None.

.. py:method:: Canvas.select_to(oid, index)

        Positionne la sélection afin qu'elle inclue tous les caractères compris entre l'ancre de la sélection et ``index``. La nouvelle sélection contient le caractère à la position ``index``. Elle contient le caractère associé à l'ancre de sélection seulement si ``index`` est supérieur ou égal au point d'ancrage de la sélection. Le point d'ancrage de la sélection est déterminé par la dernière utilisation des méthodes :py:meth:`~Canvas.select_adjust` ou :py:meth:`~Canvas.select_from`.  Si le point d'ancrage de la sélection n'était pas positionné, il est placé à la position ``index`, il est placé à la position ``index``.

.. py:method:: Canvas.tag_bind(tagOrId, chevt=None, gestionnaire=None, add=None)

        Lie le gestionnaire d'événement ``gestionnaire``, pour l'évenement précisé par ``chevt``, à ou aux items ``tagOrId``. Si l'argument ``add`` est une chaîne qui commence par '+', cette liaison est ajoutées à celles qui ont déjà pu être défini pour cete événement. Autrement, les liaison précédement définies sont remplacées par celle-ci.  Pour plus d'informations, voir “Events”. Notez que la liaison aux items n'est pas supprimée par la suppression d'une marque (ni ajoutée en cas de nouveau marquage).

.. py:method:: Canvas.tag_lower(tagOrId, belowThis)

        Déplace les items ``tagOrId`` juste en-dessous du premier ou seul item indiqué par ``belowThis``. S'il y en a plusieurs, leur ordre relatif n'est pas modifié. Cette méthode ne s'applique pas aux items fenêtre.

.. py:method:: Canvas.tag_raise(tagOrId, aboveThis)

        Déplace les items sélectionné par ``tagOrId`` juste au-dessus du premier ou seul item sélectionné par ``aboveThis``. S'il y en a plusieurs, leur ordre relatif n'est pas modifié. Cette méthode ne s'applique pas aux items fenêtre.

.. py:method:: Canvas.tag_unbind(tagOrId, chEvt, gestcId=None)

        Supprime la liaison entre le ou les items ``tagOrId`` et le gestionnaire ``gestId`` pour la chaîne d'événement ``chEvt``. Voir  “Events”. 

.. py:method:: Canvas.type(tagOrId)

        Retourne le type du premier ou seul item sélectionné par ``tagOrdId``. La valeur de retour est l'une des chaînes suivante : ``'arc'``, ``'bitmap'``, ``'image'``, ``'line'``, ``'oval'``, ``'polygon'``, ``'rectangle'``, ``'text'``, or ``'window'``. 

.. py:method:: Canvas.xview_moveto(fraction)

        Cette méthode fait défiler le canevas relativement à sa fenêtre de vue. L'intention est de faire une liaison avec l'option command d'un barre de défilement qui aurait été associé à ce canevas. Le défilement est horizontal jusqu'à une position entre 0 et 1 (argument ``fraction``): 0.0 pour sa position la plus à gauche et 1.0 pour sa position la plus à droite. 

.. py:method:: Canvas.xview_scroll(n, what)

        Cette méthode fait défiler le canevas à gauche ou à droite. L'argument ``what`` précise le défilement qui peut être soit 'units' soit 'pages', ``n`` précise le nombre d'unité du déplacement (vers la droite si positif, vers la gauche autrement). 'units' se réfère à l'option ``xscrollincrement`` (voir “The Scrollbar widget”). Pour 'pages', n est multiplier par 90% de la largeur de la page.

.. py:method:: Canvas.yview_moveto(fraction)

        Même chose que xview_moveto mais verticalement. 

.. py:method:: Canvas.yview_scroll(n, what)

        Même chose que xview_scroll mais verticalement.

.. _arcs:

Les arcs
========

Un arc, dans sa forme générale, est une portion d'ellips. Une ellipse tout entière ou un cercle forment des cas particulier. Reportez-vous à  “Canvas oval objects” pour en savoir plus sur la géométrie des ellipses dessinées.

Pour créer un arc sur un canvas, utiliser :

.. py:method:: Canvas.create_arc(x0, y0, x1, y1, option, ...)

        Le constructeur retourne l'identifiant numérique du nouvel arc créé.

        Le point (x0, y0) est le coin supérieur gauche et (x1, y1) le coin inférieur droit du rectangle dans lequel s'inscrit l'ellipse. Si le rectangle est un carré, vous obtenez un (arc) de cercle.

        Les options possibles sont: 

        :arg activedash:
                These options apply when the arc is in the tk.ACTIVE state, that is, when the mouse is over the arc. For example, the activefill option specifies the interior color when the arc is active. For option values, see dash, fill, outline, outlinestipple, stipple, and width, respectively.
        :arg activefill:
        :arg activeoutline:
        :arg activeoutlinestipple:
        :arg activestipple:
        :arg activewidth:
        :arg dash: 
                Dash pattern for the outline. See Section 5.13, “Dash patterns”.
        :arg dashoffset: 
                Dash pattern offset for the outline. See Section 5.13, “Dash patterns”.
        :arg disableddash: 
                These options apply when the arc's state is tk.DISABLED.
        :arg disabledfill:
        :arg disabledoutline:
        :arg disabledoutlinestipple:
        :arg disabledstipple:
        :arg disabledwidth:
        :arg extent:
                Width of the slice in degrees. The slice starts at the angle given by the start option and extends counterclockwise for extent degrees.
        :arg fill:
                By default, the interior of an arc is transparent, and fill='' will select this behavior. You can also set this option to any color and the interior of the arc will be filled with that color.
        :arg offset: 
                Stipple pattern offset for the interior of the arc. See Section 5.14, “Matching stipple patterns”.
        :arg outline:
                The color of the border around the outside of the slice. Default is black.
        :arg outlineoffset: 
                Stipple pattern offset for the outline. See Section 5.14, “Matching stipple patterns”.
        :arg outlinestipple:
                If the outline option is used, this option specifies a bitmap used to stipple the border. Default is black, and that default can be specified by setting outlinestipple=''.
        :arg start:
                Starting angle for the slice, in degrees, measured from +x direction. If omitted, you get the entire ellipse.
        :arg state: 
                This option is tk.NORMAL by default. It may be set to tk.HIDDEN to make the arc invisible or to tk.DISABLED to gray out the arc and make it unresponsive to events.
        :arg stipple: 
                A bitmap indicating how the interior fill of the arc will be stippled. Default is stipple='' (solid). You'll probably want something like stipple='gray25'. Has no effect unless fill has been set to some color.
        :arg style: 
                The default is to draw the whole arc; use style=tk.PIESLICE for this style. To draw only the circular arc at the edge of the slice, use style=tk.ARC. To draw the circular arc and the chord (a straight line connecting the endpoints of the arc), use style=tk.CHORD.
        :arg tags: 
                If a single string, the arc is tagged with that string. Use a tuple of strings to tag the arc with multiple tags. See Section 8.4, “Canvas tags”.
        :arg width:
                Width of the border around the outside of the arc. Default is 1 pixel. 


.. _can_bitmaps:

Les bitmaps
===========

Un bitmap sur un canevas est une image ayant seulement deux couleurs : la couleur de fond (pour la valeur 0) et la couleur d'avant plan (pour la valeur 1).

Pour créer un item de type bitmap sur un canevas, utiliser:


.. py:method:: Canvas.create_bitmap(x, y, options ...)

        Retourne l'identifiant numérique de l'image bitmap créé sur le canevas appelant.

        x et y sont les coordonnées du point de référence qui précise où placer le bitmap.

        Les options sont :

        :arg activebackground: 
                These options specify the background, bitmap, and foreground values when the bitmap is active, that is, when the mouse is over the bitmap.
        :arg activebitmap:
        :arg activeforeground:
        :arg anchor:
                The bitmap is positioned relative to point (x, y). The default is anchor=tk.CENTER, meaning that the bitmap is centered on the (x, y) position. See Section 5.5, “Anchors” for the various anchor option values. For example, if you specify anchor=tk.NE, the bitmap will be positioned so that point (x, y) is located at the northeast (top right) corner of the bitmap.
        :arg background: 
                The color that will appear where there are 0 values in the bitmap. The default is background='', meaning transparent.
        :arg bitmap: 
                The bitmap to be displayed; Voir :ref:`bitmaps`.
        :arg disabledbackground: 
                These options specify the background, bitmap, and foreground to be used when the bitmap's state is tk.DISABLED.
        :arg disabledbitmap:
        :arg disabledforeground:
        :arg foreground: 
                The color that will appear where there are 1 values in the bitmap. The default is foreground='black'.
        :arg state: 
                By default, items are created with state=tk.NORMAL. Use tk.DISABLED to make the item grayed out and unresponsive to events; use tk.HIDDEN to make the item invisible.
        :arg tags: 
                If a single string, the bitmap is tagged with that string. Use a tuple of strings to tag the bitmap with multiple tags. See Section 8.4, “Canvas tags”. 

.. _can_images:

Les images
==========

Pour afficher une image sur un canevas, utiliser:


.. py:method:: Canvas.create_image(x, y, option, ...)

        Retourne l'identifiant numérique de l'item image créé sur le canevas appelant.

        L'image est positionné relativement au point (x, y). Ces options sont :

        :arg activeimage: 
                Image to be displayed when the mouse is over the item. For option values, see image below.
        :arg anchor:
                The default is anchor=tk.CENTER, meaning that the image is centered on the (x, y) position. See Section 5.5, “Anchors” for the possible values of this option. For example, if you specify anchor=tk.S, the image will be positioned so that point (x, y) is located at the center of the bottom (south) edge of the image.
        :arg disabledimage: 
                Image to be displayed when the item is inactive. For option values, see image below.
        :arg image:
                The image to be displayed. See Section 5.9, “Images”, above, for information about how to create images that can be loaded onto canvases.
        :arg state: 
                Normally, image objects are created in state tk.NORMAL. Set this value to tk.DISABLED to make it grayed-out and unresponsive to the mouse. If you set it to tk.HIDDEN, the item is invisible.
        :arg tags:
                If a single string, the image is tagged with that string. Use a tuple of strings to tag the image with multiple tags. See Section 8.4, “Canvas tags”. 

.. _lignes:

Les lignes
==========

En général, une ligne est une succession de segments connectés les uns aux autres. Pour créer une ligne, utiliser:


.. py:method:: Canvas.create_line(x0, y0, x1, y1, ..., xn, yn, option, ...)

        La ligne est formée de segments qui joignent les points (x0, y0), (x1, y1), … (xn, yn). Les options possibles sont :

        :arg activedash: 
                 These options specify the dash, fill, stipple, and width values to be used when the line is active, that is, when the mouse is over it.
        :arg activefill:
        :arg activestipple:
        :arg activewidth:
        :arg arrow:
                The default is for the line to have no arrowheads. Use arrow=tk.FIRST to get an arrowhead at the (x0, y0) end of the line. Use arrow=tk.LAST to get an arrowhead at the far end. Use arrow=tk.BOTH for arrowheads at both ends.
        :arg arrowshape:
                A tuple (d1, d2, d3) that describes the shape of the arrowheads added by the arrow option. Default is (8,10,3).
        :arg capstyle: 
                You can specify the shape of the ends of the line with this option; seeVoir :ref:`style-extr`.
                The default option is tk.BUTT.
        :arg dash: 
                To produce a dashed line, specify this option; Voir :ref:`Motifs-brise`.
                The default appearance is a solid line.
        :arg dashoffset: 
                 If you specify a dash pattern, the default is to start the specified pattern at the beginning of the line. The dashoffset option allows you to specify that the start of the dash pattern occurs at a given distance after the start of the line. See Section 5.13, “Dash patterns”.
        :arg disableddash: 
                The dash, fill, stipple, and width values to be used when the item is in the tk.DISABLED state.
        :arg disabledfill:
        :arg disabledstipple:
        :arg disabledwidth:
        :arg fill:
                The color to use in drawing the line. Default is fill='black'.
        :arg joinstyle: 
                For lines that are made up of more than one line segment, this option controls the appearance of the junction between segments. For more details, Voir :ref:`style-extr`.
                The default style is ROUND
        :arg offset: 
                For stippled lines, the purpose of this option is to match the item's stippling pattern with those of adjacent objects. See Section 5.14, “Matching stipple patterns”..
        :arg smooth:
                If true, the line is drawn as a series of parabolic splines fitting the point set. Default is false, which renders the line as a set of straight segments.
        :arg splinesteps:
                If the smooth option is true, each spline is rendered as a number of straight line segments. The splinesteps option specifies the number of segments used to approximate each section of the line; the default is splinesteps=12.
        :arg state: 
                Normally, line items are created in state tk.NORMAL. Set this option to tk.HIDDEN to make the line invisible; set it to tk.DISABLED to make it unresponsive to the mouse.
        :arg stipple:
                To draw a stippled line, set this option to a bitmap that specifies the stippling pattern, such as stipple='gray25'. See Section 5.7, “Bitmaps” for the possible values.
        :arg tags:
                If a single string, the line is tagged with that string. Use a tuple of strings to tag the line with multiple tags. See Section 8.4, “Canvas tags”.
        :arg width:
                The line's width. Default is 1 pixel. See Section 5.1, “Dimensions” for possible values. 

.. _ellipses-et-cercles:

Les ellipses et cercles
=======================

Pour créer l'ellipse (ou le cercle) qui s'inscrit dans le rectangle (ou le carré) (x0, y0), (x1, y1) où les premières coordonnées sont celles du coin supérieur gauche et les secondes celles du coin inférieur droit, utiliser:

.. py:method:: Canvas.create_oval(x0, y0, x1, y1, option, ...)

        Retourne l'identifiant numérique de l'ellipse créé. Les options sont :

        :arg activedash: 
                These options specify the dash pattern, fill color, outline color, outline stipple pattern, interior stipple pattern, and outline width values to be used when the oval is in the tk.ACTIVE state, that is, when the mouse is over the oval. For option values, see dash, fill, outline, outlinestipple, stipple, and width.
        :arg activefill:
        :arg activeoutline:
        :arg activeoutlinestipple:
        :arg activestipple:
        :arg activewidth:
        :arg dash: 
                To produce a dashed border around the oval, set this option to a dash pattern; Voir :ref:`Motifs-brise`.
        :arg dashoffset: 
                When using the dash option, the dashoffset option is used to change the alignment of the border's dash pattern relative to the oval. See Section 5.14, “Matching stipple patterns”.
        :arg disableddash: 
                These options specify the appearance of the oval when the item's state is tk.DISABLED.
        :arg disabledfill:
        :arg disabledoutline:
        :arg disabledoutlinestipple:
        :arg disabledstipple:
        :arg disabledwidth:
        :arg fill:
                The default appearance of an oval's interior is transparent, and a value of fill='' will select this behavior. You can also set this option to any color and the interior of the ellipse will be filled with that color; Voir :ref:`couleurs`.
        :arg offset: 
                Stipple pattern offset of the interior. See Section 5.14, “Matching stipple patterns”.
        :arg outline:
                The color of the border around the outside of the ellipse. Default is outline='black'.
        :arg outlineoffset: 
                Stipple pattern offset of the border. See Section 5.14, “Matching stipple patterns”.
        :arg stipple:
                A bitmap indicating how the interior of the ellipse will be stippled. Default is stipple='', which means a solid color. A typical value would be stipple='gray25'. Has no effect unless the fill has been set to some color. See Section 5.7, “Bitmaps”.
        :arg outlinestipple: 
                Stipple pattern to be used for the border. For option values, see stipple below.
        :arg state: 
                By default, oval items are created in state tk.NORMAL. Set this option to tk.DISABLED to make the oval unresponsive to mouse actions. Set it to tk.HIDDEN to make the item invisible.
        :arg tags:
                If a single string, the oval is tagged with that string. Use a tuple of strings to tag the oval with multiple tags. See Section 8.4, “Canvas tags”.
        :arg width:
                Width of the border around the outside of the ellipse. Default is 1 pixel; Voir :ref:`dimensions`.
                for possible values. If you set this to zero, the border will not appear. If you set this to zero and make the fill transparent, you can make the entire oval disappear. 

.. _polygones:

Les polygones
=============

Un polygone est une ligne fermé. Ainsi, il possède une ligne de contour (formé de segments) et une zone intérieure. Pour le définir, on utilise une série de opoints [(x0, y0), (x1, y1), … (xn, yn)]. Le premier point et le dernier sont reliés par un segment afin de le fermé. Pour créer un polygone, utiliser:

.. py:method:: Canvas.create_polygon(x0, y0, x1, y1, ..., option, ...)

        Retourne l'identifiant numérique du polygone créé. Ses options sont:

        :arg activedash: 
                These options specify the appearance of the polygon when it is in the tk.ACTIVE state, that is, when the mouse is over it. For option values, see dash, fill, outline, outlinestipple, stipple, and width.
        :arg activefill:
        :arg activeoutline:
        :arg activeoutlinestipple:
        :arg activestipple:
        :arg activewidth:
        :arg dash: 
                Use this option to produce a dashed border around the polygon. See Section 5.13, “Dash patterns”.
        :arg dashoffset: 
                Use this option to start the dash pattern at some point in its cycle other than the beginning. See Section 5.13, “Dash patterns”.
        :arg disableddash: 
                These options specify the appearance of the polygon when its state is tk.DISABLED.
        :arg disabledfill:
        :arg disabledoutline:
        :arg disabledoutlinestipple:
        :arg disabledstipple:
        :arg disabledwidth:
        :arg fill:
                You can color the interior by setting this option to a color. The default appearance for the interior of a polygon is transparent, and you can set fill='' to get this behavior. See Section 5.3, “Colors”.
        :arg joinstyle: 
                This option controls the appearance of the intersections between adjacent sides of the polygon. See Section 5.12, “Cap and join styles”.
        :arg offset: 
                Offset of the stipple pattern in the interior of the polygon. See Section 5.14, “Matching stipple patterns”.
        :arg outline:
                Color of the outline; defaults to outline='', which makes the outline transparent.
        :arg outlineoffset: 
                Stipple offset for the border. See Section 5.14, “Matching stipple patterns”.
        :arg outlinestipple: 
                Use this option to get a stippled border around the polygon. The option value must be a bitmap; Voir :ref:`bitmaps`.
        :arg smooth:
                The default outline uses straight lines to connect the vertices; use smooth=0 to get that behavior. If you use smooth=1, you get a continuous spline curve. Moreover, if you set smooth=1, you can make any segment straight by duplicating the coordinates at each end of that segment.
        :arg splinesteps:
                If the smooth option is true, each spline is rendered as a number of straight line segments. The splinesteps option specifies the number of segments used to approximate each section of the line; the default is splinesteps=12.
        :arg state: 
                By default, polygons are created in the tk.NORMAL state. Set this option to tk.HIDDEN to make the polygon invisible, or set it to tk.DISABLED to make it unresponsive to the mouse.
        :arg stipple:
                A bitmap indicating how the interior of the polygon will be stippled. Default is stipple='', which means a solid color. A typical value would be stipple='gray25'. Has no effect unless the fill has been set to some color. See Section 5.7, “Bitmaps”.
        :arg tags:
                If a single string, the polygon is tagged with that string. Use a tuple of strings to tag the polygon with multiple tags. See Section 8.4, “Canvas tags”.
        :arg width:
                Width of the outline; defaults to 1. See Section 5.1, “Dimensions”. 

.. _rectangles:

Les rectangles
==============

Un rectangle est défini par deux points : (x0, y0) pour son coin supérieur gauche et (x1, y1) pour son coin inférieur droit.

For example, the rectangle specified by top left corner (100,100) and bottom right corner (102,102) is a square two pixels by two pixels, including pixel (101,101) but not including (102,102).

Rectangles are drawn in two parts:

* The outline lies inside the rectangle on its top and left sides, but outside the rectangle on its bottom and right side. The default appearance is a one-pixel-wide black border.

  For example, consider a rectangle with top left corner (10,10) and bottom right corner (11,11). If you request no border (width=0) and green fill (fill='green'), you will get one green pixel at (10,10). However, if you request the same options with a black border (width=1), you will get four black pixels at (10,10), (10,11), (11,10), and (11,11).

* The fill is the area inside the outline. Its default appearance is transparent. 

To create a rectangle object on canvas C:

.. py:method:: Canvas.create_rectangle(x0, y0, x1, y1, option, ...)

        This constructor returns the object ID of the rectangle on that canvas. Options include:

        :arg activedash: 
                These options specify the appearance of the rectangle when its state is tk.ACTIVE, that is, when the mouse is on top of the rectangle. For option values, refer to dash, fill, outline, outlinestipple, stipple, and width below.
        :arg activefill:
        :arg activeoutline:
        :arg activeoutlinestipple:
        :arg activestipple:
        :arg activewidth:
        :arg dash: 
                To produce a dashed border around the rectangle, use this option to specify a dash pattern. See Section 5.13, “Dash patterns”.
        :arg dashoffset: 
                Use this option to start the border's dash pattern at a different point in the cycle; Voir :ref:`Motifs-brise`.
        :arg disableddash: 
                These options specify the appearance of the rectangle when its state is tk.DISABLED.
        :arg disabledfill:
        :arg disabledoutline:
        :arg disabledoutlinestipple:
        :arg disabledstipple:
        :arg disabledwidth:
        :arg fill:
                By default, the interior of a rectangle is empty, and you can get this behavior with fill=''. You can also set the option to a color; Voir :ref:`couleurs`.
        :arg offset: 
                Use this option to change the offset of the interior stipple pattern. See Section 5.14, “Matching stipple patterns”.
        :arg outline:
                The color of the border. Default is outline='black'.
        :arg outlineoffset: 
                Use this option to adjust the offset of the stipple pattern in the outline; see Section 5.14, “Matching stipple patterns”.
        :arg outlinestipple: 
                Use this option to produce a stippled outline. The pattern is specified by a bitmap; Voir :ref:`bitmaps`.
        :arg state: 
                By default, rectangles are created in the tk.NORMAL state. The state is tk.ACTIVE when the mouse is over the rectangle. Set this option to tk.DISABLED to gray out the rectangle and make it unresponsive to mouse events.
        :arg stipple:
                A bitmap indicating how the interior of the rectangle will be stippled. Default is stipple='', which means a solid color. A typical value would be stipple='gray25'. Has no effect unless the fill has been set to some color. See Section 5.7, “Bitmaps”.
        :arg tags:
                If a single string, the rectangle is tagged with that string. Use a tuple of strings to tag the rectangle with multiple tags. See Section 8.4, “Canvas tags”.
        :arg width:
                Width of the border. Default is 1 pixel. Use width=0 to make the border invisible. See Section 5.1, “Dimensions”. 

.. _textes:

Les textes
==========

Vous pouvez afficher une ou plusieurs lignes de texte sur un canevas en utilisant:

.. py:method:: Canvas.create_text(x, y, option, ...)

        Retourne l'identifiant numérique de l'objet textuel ainsi créé. Ses options sont:

        :arg activefill: 
                Couleur de remplissage à utiliser lorsque la souris est au-dessus.
        :arg activestipple: 
                The stipple pattern to be used when the text is active. For option values, see stipple below.
        :arg anchor:
                Par défaut, vaut 'center' ce qui signifie que le texte est centré par rapport à la position (x,y). Voir  “Anchors” pour les valeurs possibles.
        :arg disabledfill: 
                Couleur de remplissage lorsque l'item est dans l'état (state) 'disabled'.
        :arg disabledstipple: 
                The stipple pattern to be used when the text is disabled. For option values, see stipple below.
        :arg fill:
                Couleur du texte, noir par défaut. Voir “Colors”.
        :arg font:
                Utiliser cette option pour changer la police de caractères. Voir “Type fonts”.
        :arg justify:
                Gère l'alignement en cas d'affichage multiligne : 'left' pour gauche, 'center' pour centré et 'right' pour droit.
        :arg offset: 
                The stipple offset to be used in rendering the text. For more information, see Section 5.14, “Matching stipple patterns”.
        :arg state: 
                'normal' par défaut. Mettre cet option à 'disabled' pour l'empêcher de réagir à la souris, la mettre à 'hidden' pour le rendre invisible.
        :arg stipple:
                A bitmap indicating how the text will be stippled. Default is stipple='', which means solid. A typical value would be stipple='gray25'. See Section 5.7, “Bitmaps”.
        :arg tags:
                Si c'est une chaîne seule, elle sert à marquer (tag) la fenêtre. Utiliser un tuple de chaînes pour lui attribuer plusieurs marques. Voir “Canvas tags”.
        :arg text:
                Le texte à afficher sous la forme d'une chaîne de caractères. Utiliser '\n' pour forcer les sauts de ligne.
        :arg width:
                If you don't specify a width option, the text will be set inside a rectangle as long as the longest line. However, you can also set the width option to a dimension, and each line of the text will be broken into shorter lines, if necessary, or even broken within words, to fit within the specified width. See Section 5.1, “Dimensions”.

Vous pouvez modifier ou récupérer le texte affiché:

* Pour récupérer le texte d'un tel item d'identifiant ``id`` sur un canevas ``can``, utiliser ``can.itemcget(id, 'text')``.

* Pour remplacer le texte d'un tel item par un chaîne ``ch``, utiliser ``can.itemconfigure(id, text=ch)``.

Plusieurs méthodes des canevas vous permette d'autre manipulation du texte. Voir “Methods on Canvas widgets”, et plus particulièrement :py:meth:`~Canvas.dchars`, :py:meth:`~Canvas.focus`, :py:meth:`~Canvas.icursor`, :py:meth:`~Canvas.index`, et :py:meth:`~Canvas.insert`. 

.. _fenêtres:

Les fenêtres
============

Il est possible de placer n'importe quel widget de tkinter sur un canevas en utilisant un item fenêtre. Une fenêtre est une zone rectangulaire qui peut contenir un widget de tkinter. Le widget doit être un enfant de la même fenêtre principale que le canevas, ou l'enfant d'un widget lui-même situé dans cette fenêtre principale.

Si vous voulez insérer un objet composé de plusière widget sur un canevas, vous pouvez utiliser cette méthode pour placer un cadre dans le canevas et, ensuite, placer d'autre widgets dans ce cadre.

Pour créer une fenêtre dans un canevas, utiliser:

.. py:method:: Canvas.create_window(x, y, option, ...)

        Retourne l'identifiant numérique de la fenêtre créé. Ses options sont:

        :arg anchor:
                Par défaut, vaut 'center' ce qui signifie que la fenêtre est centrée par rapport à la position (x,y). Voir  “Anchors” pour les valeurs possibles.
        :arg height:
                La hauteur de la zone réservée pour la fenêtre. Si non renseignée, la fenêtre s'ajuste à la hauteur de son contenu. Voir “Dimensions” for possible values.
        :arg state: 
                'normal' par défaut. Mettre cet option à 'disabled' pour empêcher la fenêtre de réagir à la souris, la mettre à 'hidden' pour la rendre invisible.
        :arg tags:
                Si c'est une chaîne seule, elle sert à marquer (tag) la fenêtre. Utiliser un tuple de chaînes pour lui attribuer plusieurs marques. Voir “Canvas tags”.
        :arg width:
                La largeur de la zone réservée pour la fenêtre. Si non renseignée, la fenêtre s'ajuste à la largeur de son contenu.
        :arg window:
                Utiliser ``window=w`` où w est le widget que vous souhaitez placer sur le canevas. 
