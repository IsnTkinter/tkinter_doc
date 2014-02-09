.. _TEXT:

******************
Le widget ``Text``
******************

Un widget de type ``Text`` est une manière bien plus générale de traiter un texte multiligne que celle qu'offre un widget étiquette (``Label``). Ce widget ressemble plus à un éditeur de texte complet dans une fenêtre.

* Vous pouvez mélanger différentes fontes, couleurs de texte et couleurs d'arrière plan.

* Vous pouvez intercaler des images dans le texte. Une image est traitée comme un caractère unique. Voir “Text widget images”.

* Un index est un entier qui sert à préciser une position entre deux caractères. Voir “Text widget indices”.

* Un widget ``Text`` peut contenir des marqueurs invisibles situés entre deux caractères. Voir “Text widget marks”.

* Un widget ``Text`` vous permet de définir des noms pour des portions de textes appelés *tags*. Vous pouvez modifier l'apparence de telles portions de textes en utilisant ces *tags*, en modifiant sa fonte, sa couleur d'avant plan ou d'arrière plan et d'autres options de présentation. Voir “Text widget tags”.

* Vous pouvez aussi lier des gestionnaire d'événement sur des portions de textes marqués (à l'aide d'un *tag*). Voir “Events”.

* Vous pouvez même insérer You can even embed a text widget in a “window” containing any Tkinter widget—even a frame widget containing other widgets. A window is also treated as a single character. See Section 24.4, “Text widget windows”. 

Pour créer un widget ``Text`` comme enfant d'une fenêtre ou d'un cadre ``parent``:

.. py:class:: Text(parent, option, ...)

        Ce constructeur retourne le nouveau widget ``Text`` créé. Ses options incluent:

        :arg autoseparators:
                Si l'option **undo** est positionné, l'option **autoseparators** contrôle si des séparateurs sont automatiquement ajoutés à la pile de l'historique de retour (*undo*) après chaque insertion ou suppression (si autoseparators=True) ou non (si autoseparator=False). Pour une vue d'ensemble du mécanisme d'historique, voir la section “The Text widget undo/redo stack”.
        :arg bg: 
                (ou **background**) La couleur d'arrière plan du widget. Voir “Colors”.
        :arg bd: 
                (ou **borderwidth**) L'épaisseur de la bordure du widget. 2 pixels par défaut. Voir “Dimensions”.
        :arg cursor: 
                Le pointeur de souris utilisée lorsque celle-ci est au dessus du widget. Voir “Cursors”.
        :arg exportselection: 
                Par défaut, le texte sélectionné à l'intérieur du widget est exporté vers le presse-papier du sytème. Utilisez exportselection=0 pour supprimer ce comportement.
        :arg font: 
                La fonte de caractères par défaut utilisées pour le texte saisi dans le widget. Notez que vous pouvez utiliser plusieurs polices de caractères dans ce widget en utilisant les *tags* pour modifier les propriétés de portions de texte. Voir “Type fonts”.
        :arg fg: 
                (ou **foreground**) La couleur utilisée pour le texte (et les bitmaps) dans le widget. Vous pouvez modifier la couleur pour des portions de textes tagués; cette option fournie juste une couleur par défaut.
        :arg height: 
                La hauteur du widget en nombre de lignes (non en pixels!). La mesure dépend de la fonte de caractère courante.
        :arg highlightbackground: 
                La couleur de la ligne de mise en valeur du focus lorsque le widget ne l'a pas. Voir “Focus: routing keyboard input”.
        :arg highlightcolor: 
                La couleur de la ligne de mise en valeur du focus lorsque le widget l'obtient.
        :arg highlightthickness: 
                L'épaisseur de la ligne de mise en valeur du focus. 1 pixel pas défaut. Utilisez highlightthickness=0 pour supprimer la mise en valeur du focus.
        :arg insertbackground: 
                La couleur du curseur d'insertion. 'black' par défaut.
        :arg insertborderwidth: 
                L'épaisseur de la bordure 3d autour du curseur d'insertion. 0 par défaut.
        :arg insertofftime: 
                Cette option et la suivante contrôle le clignotement du curseur d'insertion. la première est la durée en millisecondes de disparition et la seconde sa durée d'appartion dans le clignotement. Les valeurs par défaut sont respectivement 300 et 600.
        :arg insertontime: 
        :arg insertwidth: 
                La largeur du curseur d'insertion (sa hauteur est déterminée par le plus haut élément de la ligne courante). 2 pixels par défaut.
        :arg maxundo:
                Cette option sert à régler le nombre maximum d'opérations mémorisées dans l'historique. Pour une vue d'ensemble du mécanisme de gestion de l'historique, voir “The Text widget undo/redo stack”. Utilisez la valeur -1 pour préciser un nombre illimité d'opérations mémorisées.
        :arg padx: 
                La taille des marges internes gauche et droite de la zone de texte. 1 pixels par défaut. Voir “Dimensions”.
        :arg pady: 
                La taille des marges internes haute et basse de la zone de texte. 1 pixels par défaut.
        :arg relief: 
                Le style de la bordure 3d du widget. 'sunken' par défaut. Pour d'autre valeurs, voir “Relief styles”.
        :arg selectbackground: 
                La couleur d'arrière plan utilisée pour le texte sélectionné.
        :arg selectborderwidth: 
                L'épaisseur de la bordure qui entoure le texte sélectionné.
        :arg selectforeground: 
                La couleur du texte sélectionné.
        :arg spacing1: 
                Cette option précise la quantité d'espace vertical supplémentaire à mettre au dessus de chaque ligne de texte. Si la ligne est enveloppé (*wrap*) c'est à dire qu'un ou des retours de ligne sont automatiquement insérés pour que la ligne n'excède pas la longueur de la fenêtre, cet espace est ajouté avant la première ligne seulement. Sa valeur par défaut est 0.
        :arg spacing2: 
                Cette option précise la quantité d'espace vertical a ajouter entre deux lignes lorsque la ligne dont elles font partie a été enveloppé (*wrap* - voir l'option précédente pour les détails). Sa valeur par défaut est 0.
        :arg spacing3: 
                Cette option précise la quantité d'espace vertical supplémentaire à mettre en dessous de chaque «vrai» ligne de texte. Sa valeur par défaut est 0.
        :arg state: 
                Par défaut, un widget ``Text`` réagit aux saisies clavier ainsi qu'à la souris, c'est l'état 'normal'. Si vous utilisez state='disabled', le widget ne réagira plus et l'utilisateur ne pourra plus ajouté de contenu (ni vous par programmation).
        :arg tabs: 
                Cette option contrôle la façon dont le caractère Tab positionne le texte. Voir “Setting tabs in a Text widget”.
        :arg takefocus: 
                Par défaut, ce widget obtient le focus normalement (voir “Focus: routing keyboard input”). Utilisez takefocus=0 si vous souhaitez désactiver ce comportement.
        :arg undo:
                Mettre cette option à True pour activer le mécanisme d'historique, ou à False pour le désactiver. Voir “The Text widget undo/redo stack”.
        :arg width: 
                La largeur du widget exprimée en nombre de caractères (non en pixels!), conformément à la police de caractères courante.
        :arg wrap: 
                Cette option contrôle l'affichage des lignes trop longues. Le comportement par défaut, wrap='char', est d'insérer des sauts de ligne logique au niveau d'un caractère arbitraire. Utilisez wrap='word' et les sauts de lignes seront insérés après le dernier mot qui tient dans la ligne. Enfin, utilisez wrap='none' si vous ne souhaitez pas que des sauts de ligne soit insérés et équipez le widget d'une barre de défilement horizontale.
        :arg xscrollcommand: 
                Pour associer à ce widget une barre de défilement horizontale, configurez cette option avec la méthode set() de la barre de défilement.
        :arg yscrollcommand: 
                Similaire à l'option précédente mais pour un défilement vertical.

Les index
=========

Un index est une chaîne de caractère qui sert à préciser une position dans le contenu d'un widget ``Text``. Cette chaîne de caractères est de la forme:

``'ligne.colonne'``
        La position situé juste avant la *colonne* indiqué (en comptant à partir de 0) sur la *ligne* donnée (en comptant à partir de 1). Par exemples: '1.0' est la position de démarrage du texte; '2.3' est la position située juste avant le quatrième caractère de la deuxième ligne.

``'ligne.end'``
        La position situé juste avant le caractère de saut de ligne de la *ligne* indiquée (en comptant à partir de 1). Ainsi, par exemple, l'index '10.end' est la position situé à la fin de la dixième ligne de texte.

``'insert'``
        La position du curseur d'insertion.

``'current'``
        La position du caractère qui est le proche de la position du pointeur de la souris.

``'end'``
        La position situé juste après le dernier caractère du texte.

``'sel.first'``
        Si une portion de texte est actuellement sélectionné (comme en cliquant-glissant la souris sur celui-ci), il s'agit de la position situé juste avant le début de la sélection. Si vous essayez d'utiliser cet index et que rien n'est sélectionné, une exception de type TclError est levée.

``'sel.last'``
        La position situé juste après la fin de la sélection s'il y en a une. Une exception du même type que pour 'sel.first' est levée s'il n'y en a pas.

``'nom_marque'``
        Vous pouvez utiliser une marque comme index; utilisez simplement son nom là où un index est attendus. Voir “Text widget marks”. 

``'tag.first'``
        La position avant le premier caractère de la région de texte marqué avec *tag*. Voir “Text widget tags”. 

``'tag.last'``
        La position après le dernier caractère de la région de texte marqué avec *tag*.

``'@x,y'``
        La position située juste avant le caractère le plus proche de la position (*x*, *y*).

``objet-embarque``
        Si vous avez embarqué une image ou une fenêtre dans le widget ``Text``, vous pouvez utilisez sa référence comme un index. Voir “Text widget images” et “Text widget windows”. 

En supplément de ces différents moyens de base pour préciser un index, vous pouvez construire des expressions arbitrairement complexes en ajoutant l'un de ces suffixes à un index basique ou à une expression d'index:

``\+ n chars``
        Pour l'index donné, se déplacer vers l'avant de *n* caractères. Cette opérations peut faire changer de ligne. Par exemple, supposez que la première ligne soit «abcdef», l'expression d'index '1.0 + 5 chars' désigne la position située entre le e et le f. Vous pouvez abbréger les mots clés et omettre les blancs dans de tels expressions tant que le résultat n'est pas ambigu. Cette expression d'index pourrait s'abbréger '1.0+5c'.

``\- n chars``
        Similaire à la forme précédente mais le mouvement se fait vers l'arrière.

``\+ n lines``
        Déplacement de n lignes vers le bas par rapport à l'index donné. Tkinter essais de laisser la nouvelle position dans la même colonne que celle qu'elle avait dans la ligne de départ, mais si la ligne de la nouvelle position est trop courte, la nouvelle position sera en fin de ligne.

``\- n lines``
        Similaire à la précédente, mais le déplacement se fait vers le haut.

``linestart``
        Déplacement à la position situé avant le premier caractère de la ligne d'index donné. Par exemple, la position 'current linestart' se rapporte au début de la ligne qui est la plus proche de la position actuelle de la souris.

``lineend``
        Déplacement à la position situé après le dernier caractère (qui n'est pas un saut de ligne) de la ligne d'index donné. Par exemple, 'sel.last lineend' se rapporte à la fin de la ligne qui possède le caractère de fin de la sélection courante.

``wordstart``
        La position situé avant le début du mot qui contient la position d'index donné. Par exemple, '11.44 wordstart' se rapporte à la position juste avant le 45ème caractère de la ligne 11. Dans ce contexte, un mot est soit une chaîne composée de lettres, de chiffres ou du caractère (_) ou un seule caractères qui n'est d'aucun de ces types. 
    
Les marques
===========

Une marque représente une position flottante (ou glissante) quelquepart dans le contenu d'un widget ``Text``

* Pour gérer chaque marque, vous lui donner un nom. Ce nom peut être n'importe quelle chaîne de caractère qui ne contient ni espace, ni point.

* Il y a deux marques spéciales. 'insert' qui est la position courante du curseur et 'current' qui est la position la plus proche du pointeur de la souris.

* Les marques glissent en même temps que le contenu adjacent. Si vous ajoutez du texte en amont d'une marque, la marque conserve la même position relativement aux contenus immédiatement voisins.

* Les marques possèdent une propriété dite de «gravité» qui contrôle ce qui arrive lorsque vous insérer du texte à la position marquée. La gravité par défaut est 'right', ce qui signifie que lorsque vous insérer du texte sur la marque, celle-ci reste à la fin du texte inséré. Si vous réglez la gravité à 'left' (en utilisant la méthode mark_gravity() du widget de texte), la marque restera à la position située juste avant le texte inséré sur celle-ci.

* Supprimer du texte autour d'une marque ne supprime pas la marque. Pour supprimer une marque, utilisez la méthode mark_unset() du widget texte.

Reportez-vous à “Methods on Text widgets”, ci-desssous, pour comprendre comment utiliser les marques.

Les images
==========

Vous pouvez mettre une image ou un bitmap à l'intérieur du widget ``Text``. Elle sera traitée comme un caractère unique dont la taille est celle de l'objet. Voir “Images” et “Bitmaps”.

Les images sont placées dans le texte en appelant la méthode image_create() du widget ``Text``. Voir plus loin pour la séquence d'appel et d'autres méthodes pour manipuler les images.

On manipule les images en fournissant leur nom à des méthodes du widget ``Text``. Vous pouvez préciser à Tkinter le nom d'une image ou le laisser en produire un par défaut.

Une image peut apparaître un nombre arbitraire de fois dans le même widget de texte. Chaque instance de l'image aura un nom unique. Ces nom peuvent être utilisés comme index.

Les fenêtres
============

Vous pouvez mettre n'importe quel widget de Tkinter - même un cadre qui contient d'autres widgets - à l'intérieur du widget ``Text``. Par exemple, vous pouvez y mettre un bouton parfaitement opérationnel ou un ensemble de boutons radios.

Pour cela, utilisez la méthode window_create() du widget texte. Pour la séquence d'appel et d'autres méthodes utiles dans ce contexte, voir “Methods on Text widgets”. 

Les tags
========

Il y a un grand nombre de moyens pour changer à la fois l'apparence et les fonctionnalités des éléments qui se trouve dans un widget ``Text``. Pour le texte, vous pouvez modifier sa fonte, taille et couleur. De plus, vous pouvez rendre des portions de texte, les widgets ou les images embarquées réactive au clavier ou aux action de la souris.

Afin de contrôler ces caractéristiques relatives à l'apparence ou aux fonctionnalités, vous associez à chaque caractéristique un tag. Vous pouvez associer un tag avec autant de portions de texte que souhaités.

* Le nom d'un tag peut être n'importe quelle chaîne de caractères pourvu qu'elle ne contienne ni espace, ni point.

* Il y a un tag prédéfini nommé 'sel'. Il se rapporte à la région définie par la sélection courante s'il y en a une.

* Puisque chaque caractère peut faire partie d'un ou de plusieurs tags, ces tags sont ordonnés dans une liste. Chaque nouveau tag est ajouté à la fin de cette liste de sorte que les derniers entrés ont la priorité sur ceux qui ont été entrés plus tôt.

* Ainsi, par exemple, si un caractère ``c`` fait partie de deux régions tagués ``t1`` et ``t2``, que ``t1`` est situé avant ``t2`` dans la liste ordonné des tags, et que ``t1`` défini une couleur de texte verte tandis que ``t2`` défini une couleur bleu, alors ``c`` sera affiché en bleu car ``t2`` a la priortié sur ``t1``.

* Vous pouvez modifiez à tout moment l'ordre des tags dans la liste des tags.

Les tags sont créés en utilisant la méthode tag_add() du widget text. Reportez-vous à “Methods on Text widgets”, ci-dessous, pour des informations sur cela et d'autres méthodes utiles dans ce contexte.

Régler les tabulations
======================

L'utilisation de la touche tabulation permet de faire avancer le curseur jusqu'à une position déterminée par un taquet de tabulation ou, à défaut, de créer une certaine quantité d'espaces blanches. En appuyant simultanément sur la touche Maj on obtient l'effet inverse, d'où les deux flèches de sens opposés généralement représentées sur la touche.

L'option **tabs** du widget ``Text`` vous donne plusieurs possibilités pour déterminer l'emplacement des taquets de tabulation à l'intérieur du widget texte.

* Le comportement par défaut est de placer un taquet de tabulation tous les 8 caractères.

* Pour préciser un jeu de taquets de tabulation, réglez cette option avec un tuple d'une ou plusieurs distances. Par exemple, le réglage tabs=('3c', '5c', '12c') place des taquets de tabulations à 3, 5 et 12 cm du bord gauche de la page. Après le dernier taquet de tabulation qui vous avez explicitement positionné, l'espace entre deux taquets de tabulation sera le même que celui qui sépare les deux derniers taquets de tabulation du réglage. Ainsi, pour continuer notre exemple, et parcque 12c-5c=7 cm, si l'utilisateur appui de nouveau sur la touche tab, le curseur sera positionné à 19cm, puis à 26cm, 33cm et ainsi de suite.

* Normalement, le texte situé après un caractère de tabulation est aligné de sorte que son côté gauche soit sur le taquet de tabulation, mais vous pouvez inclure l'un des mots clés qui suivent dans cette liste afin de modifier la position du texte situé après une tabulation:

  + Un taquet de tabulation avec ``'left'`` a le comportement par défaut.

  + Avec ``'right'`` , le texte sera positionné de telle sorte que son bord droit soit sur le taquet de tabulation.

  + Avec ``'center'``, le texte est centré sur le taquet de tabulation.

  + Avec ``'numeric'``, le texte est positionné en plaçant le premier . qu'il contient sur le taquet de tabulation.

* Par exemple, le réglage tabs=('2c', '4.5c', 'right', '9c', 'center', '13c', 'numeric') positionnera quatre taquets de tabulation: le premier à 2 cm du bord gauche de la page avec un alignement à gauche du texte, le second à 4.5 cm du bord avec un text aligné à droite, le troisième à 9cm du bord avec un alignement au centre et le quatrième à 13cm du bord avec un alignement sur le séparateur décimal. Si l'utilisateur insère de nouvelle tabulation, elles apparaîtrons à 13-9=4cm les unes des autres avec le dernier alignement de la liste c'est à dire 'numeric'.
    
Gestion de l'historique
=======================

Le widget ``Text`` possède un mécanisme intégré qui vous permet d'implémenter un historique et ses opérations de retour arrière ou de retour avant. Ces opérations servent à annuler ou à remettre en l'état les modifications du contenu du widget.

Voici comment fonctionne la pile d'historique:

* Chaque modification du contenu est enregistré en insérant une entrée en haut de la pile qui décrit la modification comme une insertion ou une suppression. Ces entrées enregistrent l'état passé du contenu aussi bien que son état présent: Le texte supprimé ou inséré est enregistré avec sa position et la modalité: suppression ou insertion.

* Votre programme peut aussi mettre en haut de la pile une entrée spéciale appelée séparateur.

* Une opération «retour arrière» modifie le contenu de l'éditeur dans l'état où il se trouvait à un certain point. Pour réaliser cela, l'éditeur reprend une à une les entrées de la pile (du haut vers le bas) tout en les rejouant jusqu'au moment où il atteint un séparateur ou le fond de la pile.

* Il faut ajouter que Tkinter mémorise combien d'entrées de la pile ont été rétablies dans l'opération de retour arrière, jusqu'à ce que d'autres opérations d'édition aient modifié le contenu de l'éditeur.

* Une opération de «retour avant» ne peut fonctionner que si l'éditeur n'a pas été modifié depuis la dernière opération de «retour arrière». Dans ce cas, il réapplique toutes les opérations précédemment annulées.

Les méthodes utilisées pour implémenter la pile d'historique sont principalement edit_redo, edit_separator, et edit_undo décrites dans "Methods on Text widgets”. Le mécanisme d'historique n'est pas activé par défaut; vous devez mettre à True l'option **undo** du widet ``Text`` pour l'activer.

Méthodes du widget ``Text``
===========================

Les méthodes qui suivent sont disponibles sur tout widget de type ``Text``:

.. hlist::
        :columns: 4

        * :py:meth:`~Text.bbox`
        * :py:meth:`~Text.compare`
        * :py:meth:`~Text.delete`
        * :py:meth:`~Text.dlineinfo`
        * :py:meth:`~Text.edit_modified`
        * :py:meth:`~Text.edit_redo`
        * :py:meth:`~Text.edit_reset`
        * :py:meth:`~Text.edit_separator`
        * :py:meth:`~Text.edit_undo`
        * :py:meth:`~Text.image_create`
        * :py:meth:`~Text.get`
        * :py:meth:`~Text.image_cget`
        * :py:meth:`~Text.image_configure`
        * :py:meth:`~Text.image_names`
        * :py:meth:`~Text.index`
        * :py:meth:`~Text.insert`
        * :py:meth:`~Text.mark_gravity`
        * :py:meth:`~Text.mark_names`
        * :py:meth:`~Text.mark_next`
        * :py:meth:`~Text.mark_previous`
        * :py:meth:`~Text.mark_set`
        * :py:meth:`~Text.mark_unset`
        * :py:meth:`~Text.scan_dragto`
        * :py:meth:`~Text.scan_mark`
        * :py:meth:`~Text.search`
        * :py:meth:`~Text.see`
        * :py:meth:`~Text.tag_add`
        * :py:meth:`~Text.tag_bind`
        * :py:meth:`~Text.tag_cget`
        * :py:meth:`~Text.tag_config`
        * :py:meth:`~Text.tag_delete`
        * :py:meth:`~Text.tag_lower`
        * :py:meth:`~Text.tag_names`
        * :py:meth:`~Text.tag_nextrange`
        * :py:meth:`~Text.tag_prevrange`
        * :py:meth:`~Text.tag_raise`
        * :py:meth:`~Text.tag_ranges`
        * :py:meth:`~Text.tag_remove`
        * :py:meth:`~Text.tag_unbind`
        * :py:meth:`~Text.window_cget`
        * :py:meth:`~Text.window_configure`
        * :py:meth:`~Text.window_create`
        * :py:meth:`~Text.window_names`
        * :py:meth:`~Text.xview`
        * :py:meth:`~Text.xview`
        * :py:meth:`~Text.xview_moveto`
        * :py:meth:`~Text.xview_scroll`
        * :py:meth:`~Text.yview`
        * :py:meth:`~Text.yview`
        * :py:meth:`~Text.yview_moveto`
        * :py:meth:`~Text.yview_scroll`

.. py:method:: Text.bbox(index)

            Retourne la boîte englobante du caractère d'*index* donné, comme un 4-tuple (x, y, largeur, hauteur). Si le caractère n'est pas visible, la valeur de retour est None. Remarquez que cette méthode peut retourner une valeur imprécise tant que vous n'avez pas appeler la méthode update_idletasks() (voir “Universal widget methods”). 

.. py:method:: Text.compare(index1, op, index2)

            Compare les position de deux index du widget texte, et retourne True si la relation précisé par *op* entre les deux index est vérifiée. L'argument *op* sert à préciser la comparaison à effectuer: '<', '<=', '==', '!=', '>=', ou '>'.

            Par exemple, pour un widget de texte ``t``, ``t.compare('2.0', '<=', 'end')`` retourne True si le début de la deuxième ligne est situé avant la fin du texte contenu dans ``t``.

.. py:method:: Text.delete(index1, index2=None)

            Supprime le texte qui situé juste après *index1*. Si le deuxième argument est omis, seul un caractère est supprimé. Sinon, la suppression porte sur tout les caractères situé strictement entre les positions index1 et index2. Faites attention qu'un index désigne une position entre deux caractères.

.. py:method:: Text.dlineinfo(index)

            Retourne la boîte englobante pour la ligne qui contient la position d'*index* donné. Voir la méthode index() ci-dessus pour prendre connaissance de la forme de la valeur de retour ainsi que du besoin éventuel de rafraîchir certaines tâches assoupies (*idle tasks*).

.. py:method:: Text.edit_modified(arg=None)

            Récupére, positionne ou efface le drapeau des modifications. Ce drapeau est utilisé pour surveillé les modifications éventuelles du contenu. Par exemple, si vous programmez un éditeur de texte dans un widget texte, vous pourriez utiliser le drapeau des modification pour déterminer si le contenu a été modifié depuis la dernière fois où il a été sauvegardé dans un fichier.Queries, sets, or clears the modified flag. This flag is used to track whether the contents of the widget have been changed. For example, if you are implementing a text editor in a Text widget, you might use the modified flag to determine whether the contents have changed since you last saved the contents to a file.

            Lorsque cette méthode est appelée sans argument, elle retourne True si le drapeau des modifications a été positionné, False sinon. Vous pouvez explicitement positionner ce drapeau en utilisant True comme argument ou le désactivé en utilisant False.

            Toute opération qui modifie le contenu de l'éditeur positionne ce drapeau, que ce soit une insertion ou suppression de texte, de manière programmé ou suite aux actions de l'utilisateur ou encore à un retour arrière dans l'historique.

.. py:method:: Text.edit_redo()

            Annule un retour arrière dans l'historique (*redo*). Pour plus de détails, voir “The Text widget undo/redo stack”. 

.. py:method:: Text.edit_reset()

            Efface l'historique.

.. py:method:: Text.edit_separator()

            Ajoute un séparateur sur la pile de gestion de l'historique. Ce séparateur limite le champ d'application d'une opération de retour arrière dans l'historique de façon à inclure les seuls changement qui se sont produit après que le séparateur ait été placé dans la pile. Pour plus de détails, voir “The Text widget undo/redo stack”. 

.. py:method:: Text.edit_undo()

            Annule toute les modifications du contenu de l'éditeur qui ont eu lieu après l'insertion d'un séparateur dans la pile de gestion de l'historique (ou jusqu'au debut de la pile s'il n'y a pas de séparateur). Pour plus de détails, voir “The Text widget undo/redo stack”. Une erreur est levée si la pile était vide au moment de l'appel.

.. py:method:: Text.image_create(index[, option=value, ...])

            Cette méthode sert à insérer une image dans l'éditeur juste après la position précisé par l'*index*. Une image est traitée de la même façon qu'un caractère dont la taille serait celle de l'image.

            Les options pour cette méthode sont données ci-après. Vous pouvez transmettre une séries d'arguments de la forme option=valeur, ou un dictionnaire que qui contient les noms d'options comme clés.
            
            **align**
                    Cette option précise l'alignement vertical de son image si sa hauteur est inférieure à la hauteur de la ligne qui la contient. Les valeurs possible sont 'top' pour un alignement en haut, 'center' pour un centrage vertical; 'bottom' pour la placer tout en bas; ou 'baseline' pour aligner le bas de l'image avec la ligne de base du texte.
            **image**
                    L'image à utiliser. Voir “Images”.
            **name**
                    Vous pouvez donner un nom à cet instance de l'image. Si vous ne renseignez pas cette option, Tkinter produira un nom unique pour cet instance. Si vous créez de multiples instances d'une même image dans le même widget de texte, Tkinter produira un nom unique en ajoutant la lettre "#" suivi d'un nombre.
            **padx**
                    Sert à indiquer un espace supplémentaire (en pixels) à ajouter à gauche et à droite de l'image.
            **pady**
                    Sert à indiquer un espace supplémentaire (en pixels) à ajouter au dessus et en dessous de l'image.

.. py:method:: Text.get(index1, index2=None)

            Utilisez cette méthode pour récupérer le texte situé actuellement entre les position *index1* et *index2*. Si le deuxième argument est omis, la méthode retourne le caractère situé juste après la position *index1*. Les images ou fenêtre embarqués sont ignorés. Si l'intervalle contient plusieurs lignes, elles sont séparées par des caractères spéciaux '\n'.

.. py:method:: Text.image_cget(index, option)

            Sert à récupérer la valeur d'une option (précisée sous la forme d'une chaîne) d'une image embarquée de position *index* (rappel: le nom d'une image est un index)

.. py:method:: Text.image_configure(index, option=valeur, ...)

            Sert à configurer une ou plusieurs options de l'image embarquée identifiée par *index*.

            Si aucune option n'est précisée, la méthode retournera un dicitionnaire qui contient toutes les options et les valeurs correspondantes définies pour cette image.

.. py:method:: Text.image_names()

            Retourne un tuple qui contient les noms de toutes les images embarquées dans le widget ``Text`` appelant.

.. py:method:: Text.index(i)

            Étant donné index *i*, retourne la position équivalente sous la forme 'ligne.colonne'.

.. py:method:: Text.insert(index, text, tags=None)

            Insère le texte donné à la position d'*index* donnée.

            Si vous ne précisez pas l'argument *tags*, le texte inséré aura le ou les tags qui s'appliquent éventuellement aux caractères qui entourent le point d'insertion.

            Si vous souhaitez utiliser un ou plusieurs tags au texte à insérer, utilisez un tuple de chaîne de tag comme troisième arguments. Chaque tag qui s'applique aux caractères qui entourent le point d'insertion est alors ignoré. Notez que le troisième argument doit être un tuple: si vous fournissez une liste de tags, tkinter n'en appliquera aucun et ça sans vous prévenir; si vous utilisez une chaîne de caractères, chaque caractère de la chaîne est traité comme un tag.

.. py:method:: Text.mark_gravity(mark, gravity=None)

            Modifie ou récupère la propriété de gravité d'une marque existante; voir “Text widget marks”, pour plus d'informations sur la propriété de gravité.

            Pour régler la propriété de gravité d'une marque *mark*, utilisez les valeurs 'left' ou 'right' comme deuxième argument. Pour récupérer la propriété de gravité de la marque *mark*, ne renseignez pas le seconde argument et la méthode retourne 'left' ou 'right'.

.. py:method:: Text.mark_names()

            Retourne la liste de toutes les marques de l'éditeur, 'insert' et 'current' inclus.

.. py:method:: Text.mark_next(index)

            Retourne le nom de la marque situé après la position d'*index* donné; s'il n'y en a pas, une chaîne vide est retournée.

            Si l'index est sous forme numérique, la méthode retourne la première marque située à cette position. Si *index* est une marque, la méthode retourne la prochaîne marque qui la suit, laquelle peut être à la même position numérique.

.. py:method:: Text.mark_previous(index)

            Retourne le nom de la marque qui est situé en amont de la position d'*index* donné. S'il n'y en a pas, une chaîne vide est retournée.

            Si l'*index* est numérique, la méthode retourne la dernière marque située à cette position. Si l'*index* est une marque, la méthode retourne la marque qui la précèsde, laquelle peut être à la même position numérique.

.. py:method:: Text.mark_set(mark, index)

            Si aucune marque de nom *mark* n'existe, une marque est crée avec sa propriété de gravité à 'right' et elle est placée à la position d'*index* donné. Si la marque existe déjà, elle est déplacée à cette position.

            Cette méthode peut modifier la position des marques 'insert' et 'current'.

.. py:method:: Text.mark_unset(mark)

            Supprime la marque *mark*. Cette méthode ne peut pas être utilisée pour supprimer les marques 'insert' et 'current'.

.. py:method:: Text.scan_dragto(x, y)

            Voir la méthode scan_mark() ci-dessous.

.. py:method:: Text.scan_mark(x, y)

            Cette méthode sert à implémenter le défilement rapide de la zone visible du widget ``Text``. Typiquement, un utilisateur enfonce un bouton de la souris puis la déplace sans relâcher le bouton dans la direction désirée, et la zone visible est déplacée dans cette direction à un rythme proportionnel à la distance parcouru par la souris depuis le clic. Le mouvement peut réaliser un défilement oblique.

            Pour implémenter cette fonctionnalité, liez l'événement «appui sur le bouton de la souris» à un gestionnaire chargé d'appeler scan_mark(x, y), où *x* et y* représente la position de la souris au moment de l'appui. Ensuite, liez l'événement '<Motion'> (déplacement de la souris) à un gestionnaire qui appelera la méthode scan_dragto(x, y) où *x* et *y* désignent la nouvelle position de la souris.

.. py:method:: Text.search(pattern, index, option=valeur, ...)

            Recherche le motif *pattern* (lequel peut être une chaîne ou une expression régulière) dans la fenêtre en commençant à l'*index* indiqué. Si le motif est trouvé, la méthode retourne un index de la forme 'ligne.colonne'; sinon, elle retourne une chaîne vide.

            Les options disponibles pour cette méthode sont:
            **backwards**
                    Mettre cette option à True pour faire une recherche vers l'arrière à partir de la position *index*. Par défaut la recherche se fait en avant.
            **count**
                    Si vous régler cette option avec une variable de contrôle de type IntVar, lorsque la recherche réussie vous pouvez récupérer la longueur du texte qui correspondait au motif *pattern* en utilisant la méthode get() sur cette variable après le retour de la méthode search.
            **exact**
                    Mettre cette option à True pour que la chaîne trouvé soit la réplique exacte de la chaîne de motif *pattern*. C'est la valeur par défaut. Comparez avec l'option *regex* ci-dessous.
            **forwards**
                    Mettre cette option à True pour faire une recherche vers l'avant. C'est la valeur par défaut de l'option.
            **regexp**
                    Mettre cette option à True pour interpréter la chaîne *pattern* comme une expression régulière dans le style du langage Tcl. Par défaut la recherche se fait de manière exacte (voir l'option *exact*). Les expressions régulières dans le style Tcl forment un sous ensemble des expressions régulières de Python; elle supportent ces caractères spéciaux: . ^ [c1…] (…) * + ? e1|e2
            **nocase**
                            Mettre cette option à 1 pour une recherche insensible à la casse (majuscule/minuscule). Par défaut, la recherche est sensible à la casse.
            **stopindex**
                            Pour limiter la recherche, utiliser un index pour préciser une position au delà de laquelle la recherche ne doit pas continuer.

.. py:method:: Text.see(index)

            Si le texte situé à la position d'*index* donné n'est pas visible, la méthode fait défiler la zone visible du widget de façon à ce que le texte devienne visible.

.. py:method:: Text.tag_add(tagName, index1, index2=None)

            Cette méthode associe le tag nommé *tagName* avec la région du contenu situé entre la position d'*index1* et d'*index2*. Si *index2* est omis, seul le caractère situé juste après la position *index1* est tagué.

.. py:method:: Text.tag_bind(tagName, sequence, func, add=None)

            Cette méthode lie la séquence d'événement *sequence* à la région de texte tagué avec *tagName*. Voir “Events” pour plus d'informations sur la gestion des événements.

            Pour créer une nouvelle liaison pour un texte tagué, utilisez les trois premiers arguments: *sequence* sert à identifier l'événement, *gest* est la fonction qui sera appelée lorsque l'événement ciblé se produira.

            Pour ajouter d'autres liaisons à un texte tagué, utiliser '+' pour l'argument *add*.

            Pour connaître le gestionnaire d'événement associé à un texte tagué pour un événement donné, n'utilisez que les deux premiers arguments et la méthode retournera le gestionnaire correspondant.

            Pour connaître tous les événements associés à un texte tagué, n'utilisez que le premier argument; la méthode retourne alors une liste qui contient toutes les séquences d'événement positionnées.

.. py:method:: Text.tag_cget(tagName, option)

            Utilisez cette méthode pour récupérer la valeur d'une option (précisé à l'aide d'une chaîne) pour un texte tagué avec *tagName*.

.. py:method:: Text.tag_config(tagName, option=valeur, ...)

            Pour modifier la valeur des option d'un texte tagué avec *tagName*, utilisez une ou plusieurs déclarations option=value séparé par des virgules.

            Si vous ne précisez aucune option, la méthode retourne un dictionnaire qui contient toutes les options actuellement configurées pour ce texte tagué.

            Voici les options de configurations pour un texte tagué:
            
            **background**
                    La couleur d'arrière plan du texte tagué. Notez que vous ne pouvez pas utiliser l'abbréviation *bg*.
            **bgstipple**
                    Pour griser la couleur de fond, préciser l'un des bitmap standard (voir “Bitmaps”). Cela n'a aucun effet si la couleur d'arrière plan n'a pas été spécifiée.
            **borderwidth**
                    Épaisseur de la bordure autour du texte tagué. 0 par défaut. Notez que vous ne pouvez pas utiliser *bd* comme abbréviation.
            **fgstipple**
                    Pour griser un texte, utiliser un bitmap.
            **font**
                    La police de caractère utilisée pour afficher le texte tagué. Voir “Type fonts”.
            **foreground**
                    La couleur utilisée pour le texte tagué. Notez que vous ne pouvez pas utiliser l'abbréviation *bd*.
            **justify**
                    Cette option, qui est positionnée pour chaque nouvelle ligne de texte du contenu, sert à préciser son alignement; les valeurs possibles sont 'left', 'right', 'center'.
            **lmargin1**
                    Taille du retrait (indentation) à appliquer au début de la première ligne de la portion de texte tagué. 0 par défaut. Voir “Dimensions” pour les valeurs permises.
            **lmargin2**
                    Taille du retrait (indentation) à appliquer au début de chaque ligne de la portion de texte tagué. 0 par défaut.
            **offset**
                    De combien élever (valeur positive) ou abaisser (valeur négative) le texte tagué relativement à la ligne de base. Utilisez cela pour créer des «indices» ou des «exposants» par exemple.
            **overstrike**
                    Mettre à 1 pour «barrer» le texte tagué (une ligne horizontale le parcourt en son centre).
            **relief**
                    Sert à préciser le style de relief de la bordure du texte tagué. Sa valeur par défaut est 'flat'. Voir “Relief styles” pour d'autres valeurs possibles.
            **rmargin**
                    Largeur de la marge droite à appliqué pour le texte tagué. Sa valeur par défaut est 0.
            **spacing1**
                    Cette option précise la quantité d'espace vertical supplémentaire à ajouter au dessus de chaque ligne de la portion de texte tagué. Si certaine lignes sont enveloppés (saut de ligne logique pour éviter le débordement à droite), cet espace supplémentaire n'est appliqué qu'à la première ligne. Sa valeur par défaut est 0.
            **spacing2**
                    Quantité d'espace vertical supplémentaire à ajouter entre deux lignes qui appartiennent à une seule ligne physique qui a été coupées pour éviter un débordement à droite. Sa valeur par défaut est 0.
            **spacing3**
                    Quantité d'espace vertical supplémentaire à ajouter en dessous d'une ligne physique (par opposition à une ligne enveloppée). Sa valeur par défaut est 0.
            **tabs**
                    Sert à préciser le traitement des tabulation pour la portion de texte tagué comme l'option de même nom du widget ``Text``. Voir “Setting tabs in a Text widget”.
            **underline**
                    Mettre à 1 pour souligner la portion de texte tagué.
            **wrap**
                    Longueur maximale d'une ligne de texte au-dessus de quoi elle est coupée (logiquement) afin de ne pas excéder cette longueur. Voir la description de l'option *wrap* du widget ``Text`` plus haut.

.. py:method:: Text.tag_delete(tagName, ...)

            Pour supprimer un ou plusieurs tags, donner leur nom à cette méthode. Leurs options et liaisons sont perdus, et les différentes portion de texte tagué avec ce tag le perdent.

.. py:method:: Text.tag_lower(tagName, sousLui=None)

            Utilisez cette méthode pour modifier l'ordre des tags dans la pile des tags (voir “Text widget tags”, pour une description de cette «pile»). Si vous précisez deux arguments, le tag de nom *tagName* est déplacer juste en dessous du tag de nom *sousLui*. Si vous n'utilisez que le premier argument, le tag est déplacé tout en bas de la pile.

.. py:method:: Text.tag_names(index=None)

            Si vous précisez *index*, cette méthode retourne la liste de tous les tags qui sont associés au caractère situé immédiatement après la position *index*. Sans argument, vous obtenez la liste de tous les tags définis pour le widget ``Text`` appelant.

.. py:method:: Text.tag_nextrange(tagName, index1, index2=None)

            Recherche le texte tagué avec *tagName* et dont le premier caractère n'est pas situé avant le caractère d'index *index1* ni après le caractère situé juste avant celui d'index *index2*. Si *index2*, la recherche se poursuit jusqu'à la fin du texte.

            Si la recherche aboutie, la méthode retourne une liste *[i0, i1]*, où *i0* est l'index du premier caractère tagué et *i1* la position situé juste après le dernier caractère tagué. Si plusieurs étendus de texte tagué existent, seul le premier trouvé est pris en considération. 

            Si rien n'est trouvé, la méthode retourne une chaîne vide.

.. py:method:: Text.tag_prevrange(tagName, index1, index2=None)

            Cette méthode est similaire à la précédente, mais le premier caractère tagué avec *tagName* ne doit pas être situé après le caractère d'index *index1* ni avant le caractère d'index *index2*. Si plusieurs étendus de texte correspondent, celle qui est la plus proche d'*index1* est choisie. Si *index2* n'est pas précisé, alors par défaut il correspond au début du texte.

            La valeur de retour est similaire à celle retournée par tag_nextrange(). 

.. py:method:: Text.tag_raise(tagName, surLui=None)

            Utilisez cette méthode pour modifier l'ordre des tags dans la pile des tags (voir “Text widget tags” pour plus d'explication sur cette pile). Si vous utilisez deux arguments, le tag *tagName* est déplacé juste au-dessus du tag *surLui*. Si vous n'utilisez qu'un argument, le tag indiqué est placé tout en haut de la pile.

.. py:method:: Text.tag_ranges(tagName)

            Cette méthode trouve tous les intervalles de texte tagués avec *tagName* et retourne une liste [s0, e0, s1, e1, …], où chaque ``si`` est l'index juste avant le premier caractère de l'intervalle tagué et ``ei`` est l'index juste après le dernier caractère de l'intervalle marqué. Si rien n'est trouvé, une chaîne vide est retournée.

.. py:method:: Text.tag_remove(tagName, index1, index2=None)

            Supprime le tag *tagName* de tous les caractères situés entre *index1* et juste avant *index2*. Si *index2* est omis, seul le tag du caractère situé juste après *index1* est supprimé.

.. py:method:: Text.tag_unbind(tagName, sequence, funcid=None)

            Supprime la liaison entre l'événement précisé par *sequence* et la portion de texte tagué avec *tagName*. Si vous avez plusieurs gestionnaires  pour l'événement précisé par *sequence*, vous pouvez en enlever un seul en l'indiquant comme troisième argument.

.. py:method:: Text.window_cget(index, option)

            Retourne la valeur de l'*option* précisé par une chaîne pour le widget embarqué situé à la position précisé par *index*.

.. py:method:: Text.window_configure(index, option=valeur, ...)

            Sert à modfier une ou plusieurs option d'un widget embarqué à la position précisé par *index* en donnant un ou plusieurs paires option=valeur.

            Si vous n'indiquez aucune option, la méthode retourne un dictionnaire qui contient les options et leurs valeurs courantes.

.. py:method:: Text.window_create(index, option, ...)

            Cette méthode crée une fenêtre par l'intermédiaire de laquelle un widget peut être inséré dans le contenu du texte. Il y a deux moyen d'embarquer un widget:

            * vous pouvez passer le widget à l'option *window* de cette méthode, ou

            * vous pouvez définir une fonction sans argument (procédure) qui créera le widget et la passer à son option *create*.

            Les options pour cette méthode sont:
            
            **align**
                    Précise comment positionner verticalement le widget embarqué dans sa ligne, s'il n'est pas aussi haut que le texte de cette ligne. Les valeurs incluent: 'center' (par défaut), ce qui a pour effet de centrer le texte verticalement dans sa ligne; 'top', ce qui place son bord haut sur le haut de la ligne; 'bottom', ce qui place son bord bas sur le bas de la ligne; et 'baseline', ce qui aligne son bord bas avec la ligne de base du texte.
            **create** 
                    Une fonction sans argument (procédure) qui sera charger de créer le widget embarqué à la demande. Cette fonction doit créer le widget comme enfant du widget ``Text`` appelant et retourner ce widget.
            **padx** 
                    Espace supplémentaire à ajouter à gauche et à droite du widget dans la ligne de texte. 0 par défaut.
            **pady** 
                    Espace supplémentaire à ajouter au dessus et en dessous du widget à l'intérieur de la ligne de texte. 0 par défaut.
            **stretch** 
                    Sert à préciser ce qui arrive dans le cas où la ligne est plus haute que le widget embarqué. Sa valeur par défaut est 0, ce qui signifie que le widget conserve sa taille normale. Si stretch=1, le widget est étiré verticalement de manière à remplir la hauteur de la ligne et l'option *align* est ignorée.
            **window** 
                    Le widget à embarquer. Ce widget doit être un enfant du widget ``Text`` appelant.

.. py:method:: Text.window_names()

            Retourne une liste qui contient les noms de tous les widgets actuellement embarqués.

.. py:method:: Text.xview('moveto', fraction)

            Cette méthode fait défiler l'éditeur horizontalement pour amener le bord gauche de la vue à la position précisée par *fraction* (appartient à [0,1]). Par exemple, si fraction=0.5, le bord gauche de la vue correspond à 50% de la largeur totale de l'éditeur. Cette méthode peut être transmise à l'option *command* d'une barre de défilement horizontale associée à l'éditeur.

            Si fraction=0.0, le bord gauche de la vue coincide avec le bord gauche de l'éditeur. Si fraction=1.0, le bord droit de la vue coincide avec le bord droit de l'éditeur.

.. py:method:: Text.xview('scroll', n, quoi)

            Dans cette deuxième forme, la vue défine de *n* fois *quoi* qui peut prendre la valeur 'units' (1 caractère) ou 'pages' (largeur de la vue). Le sens du déplacement dépend du signe de *n* (positif vers la droite, négatif vers la gauche)

.. py:method:: Text.xview_moveto(fraction)

            Fait défiler la vue de la même façon que xview('moveto', fraction). 

.. py:method:: Text.xview_scroll(n, what)

            Pareil que xview('scroll', n, quoi). 

.. py:method:: Text.yview('moveto', fraction)

            Pareil que xview('moveto',…), mais pour un défilement vertical. 

.. py:method:: Text.yview('scroll', n, quoi)

            Pareil que xview('scroll',…). Dans ce cas 'units' désigne une ligne.

.. py:method:: Text.yview_moveto(fraction)

            Similaire à xview_moveto() dans la direction verticale.  

.. py:method:: Text.yview_scroll(n, quoi)

            Similaire à xview_scroll() dans la direction verticale. 
    
