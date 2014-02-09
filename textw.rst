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
                (ou **foreground**) The color used for text (and bitmaps) within the widget. You can change the color for tagged regions; this option is just the default.
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

* Ainsi, par exemple, si un caractère ``c`` fait partie de deux régions taggués ``t1`` et ``t2``, que ``t1`` est situé avant ``t2`` dans la liste ordonné des tags, et que ``t1`` défini une couleur de texte verte tandis que ``t2`` défini une couleur bleu, alors ``c`` sera affiché en bleu car ``t2`` a la priortié sur ``t1``.

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

The Text widget has a built-in mechanism that allows you to implement undo and redo operations that can cancel or reinstate changes to the text within the widget.

Here is how the undo/redo stack works:

    Every change to the content is recorded by pushing entries onto the stack that describe the change, whether an insertion or a deletion. These entries record the old state of the contents as well as the new state: if a deletion, the deleted text is recorded; if an insertion, the inserted text is recorded, along with a description of the location and whether it was an insertion or a deletion.

    Your program may also push a special record called a separator onto the stack.

    An undo operation changes the contents of the widget to what they were at some previous point. It does this by reversing all the changes pushed onto the undo/redo stack until it reaches a separator or until it runs out of stack.

    However, note that Tkinter also remembers how much of the stack was reversed in the undo operation, until some other editing operation changes the contents of the widget.

    A redo operation works only if no editing operation has occurred since the last undo operation. It re-applies all the undone operations. 

For the methods used to implement the undo/redo stack, see the .edit_redo, .edit_reset, .edit_separator, and .edit_undo methods in Section 24.8, “Methods on Text widgets”. The undo mechanism is not enabled by default; you must set the undo option in the widget.

Methods on Text widgets
=======================

These methods are available on all text widgets:

.. py:method:: Text.bbox(index)

            Returns the bounding box for the character at the given index, a 4-tuple (x, y, width, height). If the character is not visible, returns None. Note that this method may not return an accurate value unless you call the .update_idletasks() method (see Section 26, “Universal widget methods”). 

.. py:method:: Text.compare(index1, op, index2)

            Compares the positions of two indices in the text widget, and returns true if the relational op holds between index1 and index2. The op specifies what comparison to use, one of: '<', '<=', '==', '!=', '>=', or '>'.

            For example, for a text widget t, t.compare('2.0', '<=', END) returns true if the beginning of the second line is before or at the end of the text in t. 

.. py:method:: Text.delete(index1, index2=None)

            Deletes text starting just after index1. If the second argument is omitted, only one character is deleted. If a second index is given, deletion proceeds up to, but not including, the character after index2. Recall that indices sit between characters. 

.. py:method:: Text.dlineinfo(index)

            Returns a bounding box for the line that contains the given index. For the form of the bounding box, and a caution about updating idle tasks, see the definition of the .bbox method above. 

.. py:method:: Text.edit_modified(arg=None)

            Queries, sets, or clears the modified flag. This flag is used to track whether the contents of the widget have been changed. For example, if you are implementing a text editor in a Text widget, you might use the modified flag to determine whether the contents have changed since you last saved the contents to a file.

            When called with no argument, this method returns True if the modified flag has been set, False if it is clear. You can also explicitly set the modified flag by passing a True value to this method, or clear it by passing a False value.

            Any operation that inserts or deletes text, whether by program actions or user actions, or an undo or redo operation, will set the modified flag. 

.. py:method:: Text.edit_redo()

            Performs a redo operation. For details, see Section 24.7, “The Text widget undo/redo stack”. 

.. py:method:: Text.edit_reset()

            Clears the undo stack. 

.. py:method:: Text.edit_separator()

            Pushes a separator onto the undo stack. This separator limits the scope of a future undo operation to include only the changes pushed since the separator was pushed. For details, see Section 24.7, “The Text widget undo/redo stack”. 

.. py:method:: Text.edit_undo()

            Reverses all changes to the widget's contents made since the last separator was pushed on the undo stack, or all the way to the bottom of the stack if the stack contains no separators. For details, see Section 24.7, “The Text widget undo/redo stack”. It is an error if the undo stack is empty. 

.. py:method:: Text.image_create(index[, option=value, ...])

            This method inserts an image into the widget. The image is treated as just another character, whose size is the image's natural size.

            The options for this method are shown in the table below. You may pass either a series of option=value arguments, or a dictionary of option names and values.
            align	This option specifies how the image is to be aligned vertically if its height is less than the height of its containing line. Values may be top to align it at the top of its space; center to center it; bottom to place it at the bottom; or baseline to line up the bottom of the image with the text baseline.
            image	The image to be used. See Section 5.9, “Images”.
            name	You can assign a name to this instance of the image. If you omit this option, Tkinter will generate a unique name. If you create multiple instances of an image in the same Text widget, Tkinter will generate a unique name by appending a “#” followed by a number.
            padx	If supplied, this option is a number of pixels of extra space to be added on both sides of the image.
            pady	If supplied, this option is a number of pixels of extra space to be added above and below the image. 

.. py:method:: Text.get(index1, index2=None)

            Use this method to retrieve the current text from the widget. Retrieval starts at index index1. If the second argument is omitted, you get the character after index1. If you provide a second index, you get the text between those two indices. Embedded images and windows (widgets) are ignored. If the range includes multiple lines, they are separated by newline ('\n') characters. 

.. py:method:: Text.image_cget(index, option)

            To retrieve the current value of an option set on an embedded image, call this method with an index pointing to the image and the name of the option. 

.. py:method:: Text.image_configure(index, option, ...)

            To set one or more options on an embedded image, call this method with an index pointing to the image as the first argument, and one or more option=value pairs.

            If you specify no options, you will get back a dictionary defining all the options on the image, and the corresponding values. 

.. py:method:: Text.image_names()

            This method returns a tuple of the names of all the text widget's embedded images. 

.. py:method:: Text.index(i)

            For an index i, this method returns the equivalent position in the form 'line.char'. 

.. py:method:: Text.insert(index, text, tags=None)

            Inserts the given text at the given index.

            If you omit the tags argument, the newly inserted text will be tagged with any tags that apply to the characters both before and after the insertion point.

            If you want to apply one or more tags to the text you are inserting, provide as a third argument a tuple of tag strings. Any tags that apply to existing characters around the insertion point are ignored. Note: The third argument must be a tuple. If you supply a list argument, Tkinter will silently fail to apply the tags. If you supply a string, each character will be treated as a tag. 

.. py:method:: Text.mark_gravity(mark, gravity=None)

            Changes or queries the gravity of an existing mark; see Section 24.2, “Text widget marks”, above, for an explanation of gravity.

            To set the gravity, pass in the name of the mark, followed by either tk.LEFT or tk.RIGHT. To find the gravity of an existing mark, omit the second argument and the method returns tk.LEFT or tk.RIGHT. 

.. py:method:: Text.mark_names()

            Returns a sequence of the names of all the marks in the window, including tk.INSERT and tk.CURRENT. 

.. py:method:: Text.mark_next(index)

            Returns the name of the mark following the given index; if there are no following marks, the method returns an empty string.

            If the index is in numeric form, the method returns the first mark at that position. If the index is a mark, the method returns the next mark following that mark, which may be at the same numerical position. 

.. py:method:: Text.mark_previous(index)

            Returns the name of the mark preceding the given index. If there are no preceding marks, the method returns an empty string.

            If the index is in numeric form, the method returns returns the last mark at that position. If the index is a mark, the method returns the preceding mark, which may be at the same numerical position. 

.. py:method:: Text.mark_set(mark, index)

            If no mark with name mark exists, one is created with tk.RIGHT gravity and placed where index points. If the mark already exists, it is moved to the new location.

            This method may change the position of the tk.INSERT or tk.CURRENT indices. 

.. py:method:: Text.mark_unset(mark)

            Removes the named mark. This method cannot be used to remove the tk.INSERT or tk.CURRENT marks. 

.. py:method:: Text.scan_dragto(x, y)

            See .scan_mark, below. 

.. py:method:: Text.scan_mark(x, y)

            This method is used to implement fast scrolling of a Text widget. Typically, a user presses and holds a mouse button at some position in the widget, and then moves the mouse in the desired direction, and the widget moves in that direction at a rate proportional to the distance the mouse has moved since the button was depressed. The motion may be any combination of vertical or horizontal scrolling.

            To implement this feature, bind a mouse button down event to a handler that calls .scan_mark(x, y), where x and y are the current mouse position. Then bind the <Motion> event to a handler that calls .scan_dragto(x, y), where x and y are the new mouse position. 

.. py:method:: Text.search(pattern, index, option, ...)

            Searches for pattern (which can be either a string or a regular expression) in the buffer starting at the given index. If it succeeds, it returns an index of the 'line.char' form; if it fails, it returns an empty string.

            The allowable options for this method are:
            backwards 	Set this option to True to search backwards from the index. Default is forwards.
            count 	If you set this option to an IntVar control variable, when there is a match you can retrieve the length of the text that matched by using the .get() method on that variable after the method returns.
            exact	Set this option to True to search for text that exactly matches the pattern. This is the default option. Compare the regexp option below.
            forwards	Set this option to True to search forwards from the index. This is the default option.
            regexp 	Set this option to True to interpret the pattern as a Tcl-style regular expression. The default is to look for an exact match to pattern. Tcl regular expressions are a subset of Python regular expressions, supporting these features: . ^ [c1…] (…) * + ? e1|e2
            nocase 	Set this option to 1 to ignore case. The default is a case-sensitive search.
            stopindex 	To limit the search, set this option to the index beyond which the search should not go. 

.. py:method:: Text.see(index)

            If the text containing the given index is not visible, scroll the text until that text is visible. 

.. py:method:: Text.tag_add(tagName, index1, index2=None)

            This method associates the tag named tagName with a region of the contents starting just after index index1 and extending up to index index2. If you omit index2, only the character after index1 is tagged. 

.. py:method:: Text.tag_bind(tagName, sequence, func, add=None)

            This method binds an event to all the text tagged with tagName. See Section 54, “Events”, below, for more information on event bindings.

            To create a new binding for tagged text, use the first three arguments: sequence identifies the event, and func is the function you want it to call when that event happens.

            To add another binding to an existing tag, pass the same first three arguments and '+' as the fourth argument.

            To find out what bindings exist for a given sequence on a tag, pass only the first two arguments; the method returns the associated function.

            To find all the bindings for a given tag, pass only the first argument; the method returns a list of all the tag's sequence arguments. 

.. py:method:: Text.tag_cget(tagName, option)

            Use this method to retrieve the value of the given option for the given tagName. 

.. py:method:: Text.tag_config(tagName, option, ...)

            To change the value of options for the tag named tagName, pass in one or more option=value pairs.

            If you pass only one argument, you will get back a dictionary defining all the options and their values currently in force for the named tag.

            Here are the options for tag configuration:
            background 	The background color for text with this tag. Note that you can't use bg as an abbreviation.
            bgstipple 	To make the background appear grayish, set this option to one of the standard bitmap names (see Section 5.7, “Bitmaps”). This has no effect unless you also specify a background.
            borderwidth 	Width of the border around text with this tag. Default is 0. Note that you can't use bd as an abbreviation.
            fgstipple 	To make the text appear grayish, set this option a bitmap name.
            font 	The font used to display text with this tag. See Section 5.4, “Type fonts”.
            foreground 	The color used for text with this tag. Note that you can't use the fg abbreviation here.
            justify 	The justify option set on the first character of each line determines how that line is justified: tk.LEFT (the default), tk.CENTER, or tk.RIGHT.
            lmargin1 	How much to indent the first line of a chunk of text that has this tag. The default is 0. See Section 5.1, “Dimensions”for allowable values.
            lmargin2 	How much to indent successive lines of a chunk of text that has this tag. The default is 0.
            offset 	How much to raise (positive values) or lower (negative values) text with this tag relative to the baseline. Use this to get superscripts or subscripts, for example. For allowable values, see Section 5.1, “Dimensions”.
            overstrike 	Set overstrike=1 to draw a horizontal line through the center of text with this tag.
            relief 	Which 3-D effect to use for text with this tag. The default is relief=tk.FLAT; for other possible values see Section 5.6, “Relief styles”.
            rmargin 	Size of the right margin for chunks of text with this tag. Default is 0.
            spacing1 	This option specifies how much extra vertical space is put above each line of text with this tag. If a line wraps, this space is added only before the first line it occupies on the display. Default is 0.
            spacing2 	This option specifies how much extra vertical space to add between displayed lines of text with this tag when a logical line wraps. Default is 0.
            spacing3 	This option specifies how much extra vertical space is added below each line of text with this tag. If a line wraps, this space is added only after the last line it occupies on the display. Default is 0.
            tabs 	How tabs are expanded on lines with this tag. See Section 24.6, “Setting tabs in a Text widget”.
            underline 	Set underline=1 to underline text with this tag.
            wrap 	How long lines are wrapped in text with this tag. See the description of the wrap option for text widgets, above. 

.. py:method:: Text.tag_delete(tagName, ...)

            To delete one or more tags, pass their names to this method. Their options and bindings go away, and the tags are removed from all regions of text. 

.. py:method:: Text.tag_lower(tagName, belowThis=None)

            Use this method to change the order of tags in the tag stack (see Section 24.5, “Text widget tags”, above, for an explanation of the tag stack). If you pass two arguments, the tag with name tagName is moved to a position just below the tag with name belowThis. If you pass only one argument, that tag is moved to the bottom of the tag stack. 

.. py:method:: Text.tag_names(index=None)

            If you pass an index argument, this method returns a sequence of all the tag names that are associated with the character after that index. If you pass no argument, you get a sequence of all the tag names defined in the text widget. 

.. py:method:: Text.tag_nextrange(tagName, index1, index2=None)

            This method searches a given region for places where a tag named tagName starts. The region searched starts at index index1 and ends at index index2. If the index2 argument is omitted, the search goes all the way to the end of the text.

            If there is a place in the given region where that tag starts, the method returns a sequence [i0, i1], where i0 is the index of the first tagged character and i1 is the index of the position just after the last tagged character.

            If no tag starts are found in the region, the method returns an empty string. 

.. py:method:: Text.tag_prevrange(tagName, index1, index2=None)

            This method searches a given region for places where a tag named tagName starts. The region searched starts before index index1 and ends at index index2. If the index2 argument is omitted, the search goes all the way to the end of the text.

            The return values are as in .tag_nextrange(). 

.. py:method:: Text.tag_raise(tagName, aboveThis=None)

            Use this method to change the order of tags in the tag stack (see Section 24.5, “Text widget tags”, above, for an explanation of the tag stack). If you pass two arguments, the tag with name tagName is moved to a position just above the tag with name aboveThis. If you pass only one argument, that tag is moved to the top of the tag stack. 

.. py:method:: Text.tag_ranges(tagName)

            This method finds all the ranges of text in the widget that are tagged with name tagName, and returns a sequence [s0, e0, s1, e1, …], where each si is the index just before the first character of the range and ei is the index just after the last character of the range. 

.. py:method:: Text.tag_remove(tagName, index1, index2=None)

            Removes the tag named tagName from all characters between index1 and index2. If index2 is omitted, the tag is removed from the single character after index1. 

.. py:method:: Text.tag_unbind(tagName, sequence, funcid=None)

            Remove the event binding for the given sequence from the tag named tagName. If there are multiple handlers for this sequence and tag, you can remove only one handler by passing it as the third argument. 

.. py:method:: Text.window_cget(index, option)

            Returns the value of the given option for the embedded widget at the given index. 

.. py:method:: Text.window_configure(index, option)

            To change the value of options for embedded widget at the given index, pass in one or more option=value pairs.

            If you pass only one argument, you will get back a dictionary defining all the options and their values currently in force for the given widget. 

.. py:method:: Text.window_create(index, option, ...)

            This method creates a window where a widget can be embedded within a text widget. There are two ways to provide the embedded widget:

            you can use pass the widget to the window option in this method, or

            you can define a procedure that will create the widget and pass that procedure as a callback to the create option. 

            Options for .window_create() are:
            align 	Specifies how to position the embedded widget vertically in its line, if it isn't as tall as the text on the line. Values include: align=tk.CENTER (the default), which centers the widget vertically within the line; align=tk.TOP, which places the top of the image at the top of the line; align=tk.BOTTOM, which places the bottom of the image at the bottom of the line; and align=tk.BASELINE, which aligns the bottom of the image with the text baseline.
            create 	A procedure that will create the embedded widget on demand. This procedure takes no arguments and must create the widget as a child of the text widget and return the widget as its result.
            padx 	Extra space added to the left and right of the widget within the text line. Default is 0.
            pady 	Extra space added above and below the widget within the text line. Default is 0.
            stretch 	This option controls what happens when the line is higher than the embedded widget. Normally this option is 0, meaning that the embedded widget is left at its natural size. If you set stretch=1, the widget is stretched vertically to fill the height of the line, and the align option is ignored.
            window 	The widget to be embedded. This widget must be a child of the text widget. 

.. py:method:: Text.window_names()

            Returns a sequence containing the names of all embedded widgets. 

.. py:method:: Text.xview(tk.MOVETO, fraction)

            This method scrolls the text widget horizontally, and is intended for binding to the command option of a related horizontal scrollbar.

            This method can be called in two different ways. The first call positions the text at a value given by fraction, where 0.0 moves the text to its leftmost position and 1.0 to its rightmost position. 

.. py:method:: Text.xview(tk.SCROLL, n, what)

            The second call moves the text left or right: the what argument specifies how much to move and can be either tk.UNITS or tk.PAGES, and n tells how many characters or pages to move the text to the right relative to its image (or left, if negative). 

.. py:method:: Text.xview_moveto(fraction)

            This method scrolls the text in the same way as .xview(tk.MOVETO, fraction). 

.. py:method:: Text.xview_scroll(n, what)

            Same as .xview(tk.SCROLL, n, what). 

.. py:method:: Text.yview(tk.MOVETO, fraction)

            The vertical scrolling equivalent of .xview(tk.MOVETO,…). 

.. py:method:: Text.yview(tk.SCROLL, n, what)

            The vertical scrolling equivalent of .xview(tk.SCROLL,…). When scrolling vertically by tk.UNITS, the units are lines. 

.. py:method:: Text.yview_moveto(fraction)

            The vertical scrolling equivalent of .xview_moveto(). 

.. py:method:: Text.yview_scroll(n, what)

            The vertical scrolling equivalent of .xview_scroll(). 
    
