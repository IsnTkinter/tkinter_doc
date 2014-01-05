.. _BOUTONS:

**********************
Les Boutons ``Button``
**********************

Pour créer un simple bouton dans une fenêtre ou un cadre nommé ``parent``:

.. py:class:: Button(parent, option=valeur, ...)

    Le constructeur retourne le nouveau widget bouton. Ses options sont :


    :arg activebackground:
            Couleur de fond lorsque la souris survole le bouton.
    :arg activeforeground:
            Couleur du texte lorsque la souris survole le bouton.
    :arg anchor:
            Précise la position du texte sur le bouton.
            Voir :ref:`ancrage`.
            Par exemple, ``anchor="ne"`` positionne le texte dans le bord supérieur droit (nord est) du bouton.
    :arg borderwidth: 
            (ou **bd**) largeur de la bordure du bouton ; Voir :ref:`dimensions`.
            Par défaut, sa valeur est 2 pixels.
    :arg background:
            (ou **bg**) Couleur de fond.
    :arg bitmap: 
            Nom de l'un des bitmaps standards à afficher sur le bouton à la place du du texte.
    :arg command:
            Fonction ou méthode a appeler lorsqu'on clique sur le bouton.
    :arg cursor: 
            Pour indiquer le pointeur de la souris à afficher lorsqu'on survole le bouton.
    :arg default:
            ``'normal'`` est la valeur par défaut; utiliser ``'disabled'`` si le bouton doit être désactivé (grisé et ne répondant pas au clic de la souris).
    :arg disabledforeground:
             Couleur du texte lorsque le bouton est désactivé.
    :arg foreground:
             (ou **fg**), Couleur du texte.
    :arg font:
            Police de caractère a utiliser pour le texte sur le bouton.
    :arg height:
            Hauteur du bouton en nombre de ligne (si le bouton possède une étiquette textuelle) ou en pixel (pour les images).
    :arg highlightbackground:
             Couleur de ligne indiquant que le bouton n'a pas le focus.
    :arg highlightcolor:
             Couleur de ligne indiquant que le bouton a le focus.
    :arg highlightthickness:
             Épaisseur de la ligne de focus.
    :arg image:
            Image a afficher sur le bouton (à la place du texte).
    :arg justify:
            ``'left'``, ``'center'`` ou ``'right'`` pour indiquer la position du texte.
    :arg overrelief:
            Le style de relief à utiliser lorsque la souris est sur le bouton; la valeur par défaut est ``'raised'``. Voir :ref:`reliefs`.
    :arg padx:
            Marge additionnelle à gauche et à droite du texte. Voir :ref:`dimensions` pour les valeurs possibles.
    :arg pady:
            Marge additionnelle en haut et bas du texte.
    :arg relief:
            Précise le type de relief appliqué au bouton. (Voir :ref:`reliefs`).
    :arg repeatdelay:
            Voir l'argument suivant.
    :arg repeatinterval:
            Normalement, un bouton est déclenché une seule fois lorsque l'utilisateur relâche le bouton de la souris. si vous souhaitez que le bouton soit déclenché à des intervalles réguliers lorsque l'utilisateur maintient le bouton de la souris enfoncé, positionner cette option a un certain nombre de millisecondes à attendre entre chaque répétition et donner une valeur à l'option repeatdelay (ms) pour indiquer un délai après lequel le bouton est déclenché. Par exemple, si ``repeatdelay=500`` et ``repeatinterval=100``, le bouton sera déclenché après une demi-seconde puis redéclenché tous les dixièmes de secondes juqu'à ce que l'utilisateur relâche le bouton de la souris. Si l'utilisateur relache le bouton avant la durée repeatdelay, le bouton se déclenche normalement.
    :arg state:
            Positionner cette option à ``'disabled'`` pour le griser et le rendre inactif. Sa valeur est 'active' lorsque la souris est sur le bouton et ``'normal'`` autrement.
    :arg takefocus:
            Normalement, en utilisant la touche Tab, on peut donner le focus aux bouton (see Section 53, “Focus: routing keyboard input”), et l'appui sur la barre espace a le même effet qu'un clic sur le bouton. Vous pouvez mettre **takefocus** a zéro pour empêcher cela.
    :arg text:
            Le texte a afficher sur le bouton.
    :arg textvariable:
            Une instance d'un ``StringVar()`` qui sera associée au texte du bouton. Si la variable est modifiée, un nouveau texte est affiché sur le bouton. See Section 52, “Control variables: the values behind the widgets”.
    :arg underline:
            Par défaut, vaut -1, indiquant qu'aucun caractère du texte du bouton n'est souligné. Si sa valeur est positive ou nulle, le caractère correspondant du texte est souligné. Par exemple, ``underline=1`` indique que le deuxième caractère du texte sera souligné.
    :arg width:
            Largeur du bouton en nombre de lettres (si du texte est affiché) ou en pixels (pour une image).
    :arg wraplength:
            Si on indique une valeur positive, le texte est affiché avec autant de lignes qu'il faut pour tenir dans la largeur fixé par wraplength. Pour les différentes valeurs possibles, Voir :ref:`dimensions`.

    .. py:method:: flash()

            Provoque quelques clignotement du bouton. Après cela, il revient dans son état initial.

    .. py:method:: invoke()

            Appelle la fonction de rappel (callback) associée à l'option command et retourne ce que cette fonction retourne. N'a pas d'effet si le bouton est désactivé ou si aucune fonction de rappel ne lui est associé.
