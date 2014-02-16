.. _SAISIE:

******************************
Les champs de saisie ``Entry``
******************************

Un champs de saisie ``Entry`` est utile pour permettre à l'utilisateur de modifier une ligne de texte.

* Si vous souhaitez afficher plusieurs lignes de textes modifiables, voir :ref:`TEXT`.

* Si vous souhaitez afficher une ou plusieurs lignes de textes qui ne peuvent pas être directement modifiées par l'utilisateur, voir :ref:`Label`.

Quelques définitions:

* La **sélection** est la région du texte mise en valeur (surlignement) dans un champs de saisie, s'il y en a une.

  Typiquement, la selection est réalisée par l'utilisateur avec la souris, et le texte sélectionné est copié dans le  presse-papiers du système. Cependant, Tkinter vous permet de choisir si oui ou non, la sélection doit être copiée dans le presse-papiers. Vous pouvez aussi réaliser des sélections contrôlées par le programme.

* Le **curseur d'insertion** indique où le texte sera inséré. Il est affiché lorsque l'utilisateur clique sur le champ saisie. Il apparaît normalement comme une ligne verticale qui clignote dans le composant. Vous pouvez régler finement son apparence de plusieurs façons.

* Les positions à l'intérieur du texte affiché dans le champs sont précisées à l'aide d'un **index**. Il y a plusieurs façons d'exprimer un index:

  - En utilisant un entier qui débute à 0 comme pour les chaînes de caractère de Python.

  - La constante ``'end'`` qui se réfère à la position située après le texte.

  - La constante ``'insert'`` qui se réfère à la position courante du curseur d'insertion.

  - La constante ``'anchor'`` qui se réfère au premier caractère de la sélection courante, s'il y en a une.

  - Vous pouvez avoir besoin de récupérer le caractère qui se trouve à une position déterminée par la souris. Pour simplifier cela, vous pouvez utiliser un index à l'aide d'une chaîne de caractères de la forme ``'@n'`` où n est la distance horizontale en pixels entre le côté gauche du champ de saisie et la souris. Un tel index déterminera le caractère situé à cette distance horizontale du côté gauche du champ de saisie.

Pour créer une nouveau champ de saisie dans une fenêtre principale ou dans un cadre ``parent``:

.. py:class:: Entry(parent, option, ...)

        Ce constructeur retourne le nouveau champ de saisie. Ses options incluent:

        :arg bg:
                (ou **background**) La couleur de fond de la zone de saisie. C'est un gris léger par défaut.
        :arg bd: 
                (ou **borderwidth**) L'épaisseur de la bordure qui entoure la zone de saisie. Voir :ref:`dimensions`. Sa valeur est 2 pixels par défaut.
        :arg cursor:
                Pour indiquer le pointeur de souris à afficher lorsqu'on survole le bouton. Voir :ref:`pointeurs`.
        :arg disabledbackground: 
                La couleur d'arrière plan qui est utilisée lorsque le widget est dans l'état ``'disabled'``.
        :arg disabledforeground: 
                Couleur du texte lorsque le champ de saisie est dans l'état ``'disabled'``.
        :arg exportselection: 
                Par défaut, si vous sélectionnez du texte, il est automatiquement exporté vers le presse-papiers. Pour empêcher cela, utiliser ``exportselection=0``.
        :arg fg: 
                (ou **foreground**) La couleur utilisée pour afficher le texte. Noir par défaut.
        :arg font:
                Police de caractère utilisée pour le texte saisi dans le champ de saisi. Voir :ref:`polices`.
        :arg highlightbackground:
                Couleur de la ligne qui indique que le bouton n'a pas le focus. Voir :ref:`FOCUS`.
        :arg highlightcolor:
                Couleur de ligne qui indique que le bouton a le focus.
        :arg highlightthickness:
                Épaisseur de la ligne de mise en valeur du focus.
        :arg insertbackground:
                Par défaut, le curseur d'insertion (qui indique l'endroit où le texte sera inséré) est noir. Précisez une autre couleur pour cette option si vous souhaitez la modifier. Voir :ref:`couleurs`.
        :arg insertborderwidth:
                Par défaut, le curseur d'insertion est un simple rectangle. Vous pouvez obtenir un effet de relief ``'raised'`` (voir :ref:`reliefs`) en configurant cette option avec la dimension de la bordure 3-d. Si vous faites cela, assurez-vous que l'option **insertwidth** vaut au moins le double de cette valeur.
        :arg insertofftime:
                Par défaut, le curseur d'insertion clignote. Vous pouvez configurer cette option avec une valeur en millisecondes pour préciser la durée de sa disparition dans le clignotement. La valeur par défaut est 300. Si vous utilisez ``insertofftime=0``, le curseur ne clignotera plus du tout.
        :arg insertontime:
                Similaire à l'option **insertofftime**: durée de son apparition dans le clignotement. 600 millisecondes par défaut.
        :arg insertwidth:
                Normalement, le curseur d'insertion fait 2 pixels de large. Vous pouvez ajuster cela en indiquant une dimension arbitraire.
        :arg justify:
                Cette option contrôle l'alignement du texte lorsque celui-ci ne remplit pas complètement le champ de saisie. Les valeurs possibles sont ``'left'``, ``'center'`` et ``'right'``.
        :arg readonlybackground: 
                La couleur de fond utilisée lorsque le widget est dans l'état ``'readonly'``.
        :arg relief:
                Sert à indiquer le relief utilisé pour dessiner le contour du champ de saisie. Voir :ref:`reliefs`. La valeur par défaut est ``'sunken'``.
        :arg selectbackground:
                La couleur de fond utilisée pour mettre en valeur le texte sélectionné. Voir :ref:`couleurs`.
        :arg selectborderwidth:
                La largeur de la bordure qui entoure le texte sélectionné. 1 pixel par défaut.
        :arg selectforeground:
                La couleur du texte sélectionné.
        :arg show:
                Normalement, le texte que l'utilisateur saisi apparaît dans la zone de saisie. Pour une saisie de type mot de passe, indiquer le caractère de remplacement à afficher, souvent ``show='*'``.
        :arg state:
                Utilisez cette option pour désactiver le champ de saisie de telle sorte que l'utilisateur ne puisse plus y insérer de texte.``state='disabled'`` pour le désactiver, ``state='normal'`` pour le réactiver. Votre programme peut savoir si la souris survole le champ de saisie en interrogeant cette option qui devrait alors avoir la valeur ``'active'``.
        :arg takefocus:
                Par défaut, le widget sera visité par le focus lorsque l'utilisateur utilisera la touche Tab. Configurez cette option avec la valeur 0 pour retirer le widget de la «traversée du focus». Pour plus d'informations sur le focus, voir :ref:`FOCUS`.
        :arg textvariable:
                Pour pouvoir récupérer le texte courant du champ de saisie, vous devez configurer cette option avec une instance de ``StringVar``; voir :ref:`CTRLVARIABLES`. Vous pouvez alors récupérer ou modifier le texte en utilisant les méthodes ``get()`` ou ``set()`` de cette variable de contrôle ``StringVar``.
        :arg validate: 
                Vous pouvez utiliser cette option pour indiquer que le champ de saisie utilise une fonction de validation qui sera appelée automatiquement à certains instants. Voir :ref:`validation`.
        :arg validatecommand: 
                Une fonction de validation pour le champ de saisie. Voir :ref:`validation`.
        :arg width:
                La taille du champ de saisie mesurée en nombre de caractères. La valeur par défaut est 20. Pour les polices de caractères à chasse variable (fontes proportionnelles), la taille du champ de saisie s'obtient en multipliant la moyenne de la largeur des caractères de la fonte multipliée par la valeur de cette option.
        :arg xscrollcommand:
                Si vous vous attendez à ce que les utilisateurs saisissent plus de texte que la partie visible du champ de saisie ne peut en contenir, vous pouvez lier votre champ de saisie à une barre de défilement ``Scrollbar``. Configurez alors cette option avec la méthode ``set()`` de la barre de défilement. Pour plus d'information, voir :ref:`Defilement`.

        Les méthodes disponibles pour les champs de saisie ``Entry`` incluent:

        .. hlist::
                :columns: 4

                * :py:meth:`~delete` 
                * :py:meth:`~get`
                * :py:meth:`~icursor`
                * :py:meth:`~index`
                * :py:meth:`~insert`
                * :py:meth:`~scan_dragto`
                * :py:meth:`~scan_mark`
                * :py:meth:`~select_adjust`
                * :py:meth:`~select_clear`
                * :py:meth:`~select_from`
                * :py:meth:`~select_present`
                * :py:meth:`~select_range`
                * :py:meth:`~select_to`
                * :py:meth:`~xview`
                * :py:meth:`~xview_moveto`
                * :py:meth:`~xview_scroll`
        
        .. py:method:: delete(first, last=None)

                Supprime les caractères de la position ``first`` jusqu'à, mais sans inclure, la position ``last``. Si le deuxième argument est omis, seul le caractère à la position ``first`` est supprimé. 

        .. py:method:: get()

                Retourne le texte que contient le champ de saisie lors de son appel.

        .. py:method:: icursor(index)

                Déplace le curseur d'insertion juste avant le caractère ayant la position ``index``.

        .. py:method:: index(index)

                Fait défiler le contenu du champ de saisie de telle sorte que le caractère de position ``index`` soit à la première position visible à gauche. N'a pas d'effet si le texte tient tout entier dans le champ de saisie.

        .. py:method:: insert(index, s)

                Insère la chaîne de caractères ``s`` juste avant le caractère situé à la position ``index``.

        .. py:method:: scan_dragto(x)

                Voir la méthode ``scan_mark`` ci-dessous. 

        .. py:method:: scan_mark(x)

                Utilisez cette méthode pour initialiser le défilement rapide du contenu d'un champ de saisie munie d'une barre de défilement horizontale.

                Pour réaliser cela, lier l'événement «bouton de la souris enfoncé» à un gestionnaire d'événement qui appelera ``scan_mark(x)``, où x représente la position horizontale courante de la souris. Ensuite, lier l'événement ``'<Motion>'`` (déplacement de la souris) à un gestionnaire qui appelera ``scan_dragto(x)``, où x représente la position horizontale courante de la souris. La méthode ``scan_dragto`` fait défiler le contenu du champ de saisie de manière continue et à un rythme proportionnel à la distance (horizontale) entre la position lors de l'appel de ``scan_mark`` et la position courante.

        .. py:method:: select_adjust(index)

                Cette méthode sert à ajuster la sélection pour être sûr qu'elle contient le caractère situé à la position précisée par ``index``. Si la sélection contient déjà le caractère, rien ne se produit. Autrement, la sélection est étendue à partir de sa position courante (s'il y en a une) pour inclure la position ayant l'index indiqué.

        .. py:method:: select_clear()

                Éfface la sélection (sans supprimer son contenu). N'a pas d'effet si il n'y a aucune sélection courante.

        .. py:method:: select_from(index)

                Positionne l'index de l'ancre de sélection, ``'anchor'``, à la position du caractère sélectionné par ``index`` et sélectionne ce caractère.

        .. py:method:: select_present()

                Retourne ``True`` s'il y a une sélection, ``False`` autrement.

        .. py:method:: select_range(start, end)

                Pour régler la sélection depuis l'application. Sélectionne le texte de la position ``start`` jusqu'à, mais sans inclure, la position ``end``. la position ``start`` doit être avant la position ``end``.

                Pour sélectionner tout le texte du champ de saisie ``e``, utiliser ``e.select_range(0,'end')``.

        .. py:method:: select_to(index)

                Sélection tout le texte à partir de la position ``'anchor'`` jusqu'à, mais sans inclure, le caractère de position ``index``.

        .. py:method:: xview(index)

                Fait défiler le texte de telle sorte que le caractère de position ``index`` soit situé au début du champ de saisie. Cette méthode est très utile dans la liaison entre un champ de saisie et une barre de défilement. Voir :ref:`Defilement`.

        .. py:method:: xview_moveto(f)

                Positionne le texte dans le champ de saisie de telle sorte que le caractère situé à la position relative ``f`` (par rapport à l'intégralité du texte) soit positionné sur le bord gauche du champ. L'argument ``f`` doit appartenir à l'intervalle [0;1], où 0 signifie tout à gauche et 1 tout à droite.

        .. py:method:: xview_scroll(nb, quoi)

                Sert à faire défiler le contenu du champ de saisie horizontalement. L'argument ``quoi`` est soit ``'units'``, pour indiquer un défilement caractères par caractères, ``'page'`` pour un défilement par largeur du champ de saisie. Si l'argument ``nb`` est positif, le défilement se fait de la gauche vers la droite, s'il est négatif, le défilement se fait de la droite vers la gauche. Par exemple, pour un champ de saisie ``e``, ``e.xview_scroll(-1,'pages')`` fera bouger le texte d'une «page» vers la droite et ``e.xview_scroll(4, 'units')`` le fait défiler de 4 caractères vers la gauche.

.. _Defilement:

Défilement du contenu d'un champ de saisie
==========================================

Pour pouvoir faire défiler le contenu d'un champ de saisie, il faudra ajouter un peu de code en plus afin d'adapter la fonction de rappel d'une barre de défilement ``Scrollbar`` aux méthodes fournies par le champ de saisie. Voici quelques fragments de code qui illustrent un tel réglage. Premièrement, la création et la liaison de la barre de défilement et du champ de saisie::

    saisi = Entry(root, width=10)
    saisi.grid(row=0, sticky='ew')

    saisiDefil = Scrollbar(root, orient='horizontal',
        command=defilGest)
    saisiDefil.grid(row=1, sticky='ew')

    saisi['xscrollcommand'] = saisiDefil.set

Ensuite, la définition de la fonction de rappel du code précédent::

    def defilGest(L):
        op, deCombien = L[0], L[1]

        if op == 'scroll':
            units = L[2]
            saisi.xview_scroll(deCombien, units)
        elif op == 'moveto':
            saisi.xview_moveto(deCombien)


.. _validation:

Gérer la validation
===================

Dans certaines applications, vous souhaiterez vérifier le contenu d'un champ de saisie pour vous assurez qu'il est valide selon certains critères nécessaires au bon fonctionnement de votre application. Pour préciser ce qui est valide ou non, vous définirez une fonction de rappel qui vérifiera ce contenu et signalera s'il est oui ou non valide.

Voici la procédure à suivre pour mettre en oeuvre une telle validation.

* Écrire une fonction de rappel qui vérifie le contenu du champ de saisie et retourne ``True`` s'il est considéré comme valide, ou ``False`` sinon. Si la fonction de rappel retourne ``False``, les tentatives de l'utilisateur pour modifier le contenu du champ de saisie seront refusées et le texte restera inchangé.

* Enregistrez cette fonction de rappel: cela consiste à produire un «emballage Tcl» autour de votre fonction Python.

  Supposez que votre fonction de rappel soit ``estOk``. Pour pouvoir associer cette fonction au champ de saisie, vous devez utilisez la méthode universelle (valable pour tout widget) ``register(estOk)``. Cette méthode crée «l'emballage Tcl» voulu et retourne une chaîne de caractères que tkinter peut utiliser pour appeler votre fonction.

* Lorsque vous appelez le constructeur du champ de saisie ``Entry``, utilisez son option **validatecommand** pour préciser votre fonction de validation (par l'intermédiaire de la chaîne retournée par ``register()``), et utilisez son option **validate** pour préciser les circonstances de l'appel de la fonction de validation. Les valeurs de ces options sont discutées avec plus de détails ci-dessous.

Voici les valeurs admissibles pour l'option **validate** et leur signification.

``'focus'``

        La validation est déclenchée à chaque fois que le champ de saisie obtient ou perd le focus (voir :ref:`FOCUS`).

``'focusin'``

        Elle est déclenchée lorsque le champ de saisie obtient le focus.

``'focusout'``

        Elle est déclenchée lorsque le champ de saisie perd le focus.

``'key'``

        Elle est déclenchée à chaque fois que l'appui sur une touche modifie le contenu.

``'all'``

        Lorsque l'une quelconque des situations précédentes a lieu.

``'none'``

        Désactive la validation. C'est la valeur par défaut de l'option. Notez que c'est la chaîne de caractère ``'none'``, non la valeur spéciale de Python ``None``. 

La valeur de l'option **validatecommand** dépend des arguments que vous souhaitez voir transmis à la fonction de validation.

* Peut-être que la seule chose dont à besoin votre fonction de validation est le texte qui apparaît actuellement dans le champ de saisie. Si c'est le cas, elle peut utiliser la méthode ``get()`` de la variable de contrôle qui a servi à configuer l'option **textvariable** du champ de saisie. 

  Dans ce cas, il suffit d'indiquer ``validatecommand=f``, où ``f`` est le nom de votre fonction de validation.

* Tkinter peut aussi fournir un certain nombre d'informations à votre fonction de validation. Si vous souhaitez utiliser cela, lors de l'appel du constructeur du champ de saisie, utilisez l'option ``validatecommand=(f, s1, s2, ...)``, où ``f`` est le nom «enregistré» de votre fonction de rappel (avec la méthode :py:meth:`register`, voir plus loin pour un exemple), et chaque élément ``si`` additionnel un **code de substitution**. Pour chaque code de substitution fourni, la fonction de rappel reçoit un argument positionnel qui contient la valeur appropriée.

Voici les **codes de substitution** possibles.

.. list-table::
        :widths: 10 90

        * - ``'%d'`` 
          - Code d'action: 0 pour une tentative de suppression, 1 pour une tentative d'insertion ou -1 si l'appel a eu lieu par gain ou perte du focus, ou par modification de la variable de contrôle **textvariable**.
        * - ``'%i'`` 
          - Lorque l'utilisateur tente d'insérer ou de supprimer du texte, cet argument sera la position (index) du début (cas d'une sélection) de l'insertion ou suppression. Si l'appel a eu lieu par gain ou perte de focus, ou par modification de la variable de contrôle **textvariable**, l'argument vaut -1.
        * - ``'%P'`` 
          - La valeur que le texte aurait si la modification avait lieu.
        * - ``'%s'`` 
          - Le texte du champ de saisie avant le changement.
        * - ``'%S'`` 
          - Si l'appel est du à une insertion ou une suppression, l'argument sera le texte à insérer ou à supprimer.
        * - ``'%v'`` 
          - The current value of the widget's validate option.
        * - ``'%V'`` 
          - La raison de l'appel, parmi: ``'focusin'``, ``'focusout'``, ``'key'``, ou ``'forced'`` si la variable de contrôle **textvariable** a été modifiée.
        * - ``'%W'`` 
          - Le nom du champ de saisie.

Voici un petit exemple. Supposez que vous souhaitiez que votre fonction de validation reçoive le ``'%d'`` pour déterminer les circonstances de son appel; ``'%i'`` pour déterminer où l'ajout ou la suppression doit avoir lieu; et ``'%S'`` pour déterminer ce qui doit être inséré ou supprimé. Votre fonction pourrait ressembler à cela::

    def estOK(pourquoi, ou, quoi):
        ...

Ensuite, vous utilisez la méthode universelle :py:meth:`register` pour «emballer» cette fonction. Nous supposons que ``w`` est un widget arbitraire::

    okCommand = w.register(estOK)

Pour activer cette fonction de rappel, vous aurez besoin d'utiliser ces deux options du constructeur ``Entry``::

    saisi = Entry(root, validate='all',
         validatecommand=(okCommand, '%d', '%i', '%S'), ...)

Supposez que le champ de saisie contienne actuellement la chaîne ``'abcdefg'``, et que l'utilisateur sélectionne ``'cde'`` puis appuie sur la touche Retour Arrière. Il s'ensuivrait l'appel ``estOK(0,2,'cde')``: 0 pour indiquer la suppression, 2 pour la position avant le ``'c'`` et ``'cde'`` pour la chaîne à détruire. Si ``estOK()`` retourne ``True``, le nouveau texte est ``'abfg'``; sinon, le texte est inchangé.

Le widget ``Entry`` possède aussi une option **invalidcommand** qui sert à préciser une fonction de rappel qui est appelée à chaque fois que la fonction de validation retourne False. Cette commande peut modifier le texte du champ de saisie en utilisant la méthode ``set()`` de la variable de contrôle qui a servi à configurer l'option ``textvariable``. Le réglage de cette option fonctionne de la même façon que celle de l'option **validatecommand**. Vous devez utiliser la méthode universelle ``register()`` pour envelopper votre fonction; cette méthode retourne le nom de la fonction enveloppée sous la forme d'une chaîne de caractères. Ensuite, passez cette valeur à l'option **invalidcommand** soit directement, soit comme le premier élément d'un tuple qui contient les codes de substitution qui vous intéressent.
