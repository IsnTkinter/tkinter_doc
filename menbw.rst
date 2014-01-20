.. _MENUBUTTON:

*********************
``Menubutton`` widget
*********************

Un bouton de menu ``Menubutton`` est la partie visible d'un menu déroulant. A menubutton is the part of a drop-down menu that stays on the screen all the time. Every menubutton is associated with a Menu widget (see above) that can display the choices for that menubutton when the user clicks on it.

Pour créer un bouton de menu à l'intérieur d'une fenêtre principale ou d'un cadre référencé par parent:

.. py:class:: Menubutton(parent, option, ...)

        Le constructeur retourne le nouveau bouton de menu. Ses options sont:

        :arg activebackground: 
                La couleur de fond utilisée lorsque la souris survole le widget. Voir “Colors”.
        :arg activeforeground: 
                La couleur d'avant plan (texte) utilisée lorsque la souris survole le widget.
        :arg anchor:
                Cette option sert à préciser la position du texte du bouton si celui-ci dispose de plus de place que de besoin pour le texte. Sa valeur par défaut est 'center' ce qui centre le texte sur bouton. Pour d'autres valeur possibles, voir Section 5.5, “Anchors”. Par exemple, si anchor='w', le texte sera centré verticalement contre le bord gauche du bouton.
        :arg bg: 
                (ou **background**) La couleur de fond utilisée lorsque la souris ne survole pas le bouton.
        :arg bitmap:
                Pour afficher un bitmap sur le bouton de menu, configurez cette option avec le nom de ce bitmap; voir “Bitmaps”.
        :arg bd: 
                (ou **borderwidth**) Epaisseur de la bordure dessiné autour du bouton de menu. 2 pixels par défaut. Pour les valeurs possibles, voir “Dimensions”.
        :arg compound: 
                Si vous utilisez à la fois du texte et un graphique (soit un bitmap soit une image), cette option sert à indiquer où le graphique apparaît par rapport au texte. Les valeurs possibles sont 'none' (par défaut), 'top', 'bottom', 'left', 'right' et 'center'. Par exemple, compound='right' possitionnera le graphique à la droite du texte. Si vous conservez compound='none', le graphique sera affiché mais pas le texte.
        :arg cursor:
                Le pointeur de souris utilisé lorsqu'elle survole ce widget. Voir “Cursors”.
        :arg direction:
                Normalement, le menu apparaît en dessous du bouton de menu. Utilisez ``direction='left'`` pour afficher le menu sur le côté gauche du bouton, ``direction='right'`` pour l'afficher à sa droite; ``direction='above'`` pour l'afficher au-dessus.
        :arg disabledforeground:
                La couleur d'avant plan (texte) utilisée lorsque le bouton de menu est désactivé.
        :arg fg: 
                (ou **foreground**) La couleur d'avant plan utilisée lorsque la souris ne survole pas le bouton.
        :arg font: 
                Sert à préciser la police de caractère utilisée pour afficher le texte. Voir “Type fonts”.
        :arg height:
                La hauteur du bouton de menu exprimé en ligne de texte (non en pixels !). Par défaut, le bouton s'ajuste à son contenu.
        :arg highlightbackground: 
                La couleur de la ligne de focus lorsque le widget n'a pas le focus. Voir “Focus: routing keyboard input”.
        :arg highlightcolor:
                Couleur de la ligne de focus lorsque le widget a le focus.
        :arg highlightthickness:
                Epaisseur de la ligne de focus.
        :arg image:
                Pour afficher une image sur un bouton de menu, passer la référence à l'image à cette option. Voir “Images”.
        :arg justify:
                This option controls where the text is located when the text doesn't fill the menubutton: use justify=tk.LEFT to left-justify the text (this is the default); use justify=tk.CENTER to center it, or justify=tk.RIGHT to right-justify.
        :arg menu:
                Pour associer un ensemble de choix au bouton de menu, configurer cette option avec un widget ``Menu`` qui contient ces choix. Ce widget ``Menu`` doit avoir été créé en utilisant le bouton de menu comme premier argument de son constructeur. Voir plus loin pour un exemple qui montre comment associer un bouton de menu avec un menu.
        :arg padx:
                Sert à indiquer un espace horizontal à mettre de chaque côté (gauche et droit) du bouton. 1 pixel par défaut.
        :arg pady:
                Similaire à **padx** mais dans la direction verticale. 1 pixels par défaut.
        :arg relief:
                Sert à préciser le relief à utiliser pour dessiner les contours du bouton; 'raised' par défaut. Pour d'autres effets, voir “Relief styles”.
        :arg state:
                Normalement, un bouton de menu est réactif à la souris. Utilisez state='disabled' pour le griser et le rendre inactif.
        :arg takefocus: 
                Normalement, les boutons de menu n'obtiennet pas le focus lorsque l'utilisateur appuie sur la touche Tab (voir “Focus: routing keyboard input”). Utilisez ``takefocus=True`` pour qu'il puisse obtenir le focus comme cela.
        :arg text:
                Pour afficher un texte sur le bouton de menu, configurez cette option avec le texte voulu donné sous la forme d'une chaîne de caractères. Utiliser le caractère spécial '\n' pour faire des sauts de ligne.
        :arg textvariable:
                Vous pouvez associée une variable de contrôle StringVar à ce bouton de menu par l'intermédiaire de cette option. Toute modification de sa valeur est répercutée sur le bouton et vice versa. Voir “Control variables: the values behind the widgets”.
        :arg underline:
                Set à souligner l'un des caractères du texte en précisant sa position (index) dans le texte. Par défaut, aucun caractère n'est souligné.
        :arg width:
                Width of the menubutton in characters (not pixels!). If this option is not set, the label will be sized to fit its contents.
        :arg wraplength:
                Normally, lines are not wrapped. You can set this option to a number of characters and all lines will be broken into pieces no longer than that number.

Voici un court exemple qui illustre la création d'un bouton de menu et du menu associé composé de deux cases à cocher::

    mb = Menubutton(root, text='condiments',
                             relief=RAISED)
    mb.grid()

    mb.menu = Menu(mb, tearoff=0)
    mb['menu'] = mb.menu

    mayoVar  = IntVar()
    ketchVar = IntVar()
    mb.menu.add_checkbutton(label='mayo',
        variable=mayoVar)
    mb.menu.add_checkbutton(label='ketchup',
        variable=ketchVar)

Dans cet exemple, on crée un bouton de menu étiqueté "condiments". Lorsque qu'on clique dessus, deux cases à cocher étiqueté "mayo" et "ketchup" s'affiche en dessous. will drop down. 
