.. _MENU:

******************
Le widget ``Menu``
******************

Les menus surgissant sont une façon populaire de présenter à l'utilisateur des choix possibles sans pour autant encombrer l'interface lorsque l'utilisateur n'est pas en train de faire un choix.

* Un bouton de menu, ``Menubutton``, est la partie visible d'un tel menu.

* Un menu, ``Menu``, est la liste des choix qui apparaîssent seulement après que l'utilisateur ait cliqué sur le bouton de menu.

Pour faire une sélection, l'utilisateur peut faire un cliquer-glisser du bouton vers le choix. Il peut aussi, cliquer le bouton de menu: le menu apparaît et reste à l'écran tant que l'utilisateur n'a pas fait un choix en cliquant sur l'un d'eux.

La version de Tkinter pour Unix (au moins) supporte les menus «amovibles». Si cette fonctionnalité est activée, une ligne en pointillé apparaît au-dessus des choix du menu. L'utilisateur peut cliquer sur cette ligne pour détacher le menu afin qu'il puisse être déplacé librement: une nouvelle fenêtre indépendante qui contient tous les choix du menu apparaît.

Reportez vous à “The Menubutton widget”, below, pour voir comment créer un bouton de menu et connecter celui-ci à un menu. Mais attardons-nous avant sur le widget ``Menu`` qui sert à afficher la liste des choix possibles.

Les choix affichés sur un menu peuvent être:

* Une simple **commande**: une chaîne de caractères (ou une image) que l'utilisateur peut sélectionner pour réaliser une certaine opération.

* Une « **cascade** »: une chaîne de caractères ou une image que l'utilisateur peut sélectionner pour faire apparaître un sous menu.

* Un **choix  à cocher** «checkbutton» (voir “The Checkbutton widget”).

* Un groupe de **boutons «radio»** (voir “The Radiobutton widget”). 

Pour créer un widget Menu, vous devez avoir créé au préalable un bouton de menu ``Menubutton`` que nous écrirons ``mb`` (à moins que vous ne souhaitiez créer une barre de menu, voir ...):

.. py:class:: Menu(mb, option, ...)

        Ce constructeur retourne le nouveau widget Menu. Ses options incluent:

        :arg activebackground:
                Couleur de fond utilisée pour le choix qui est survolé par la souris. Voir “Colors”.
        :arg activeborderwidth:
                Précise l'épaisseur de la bordure qui entoure le choix actuellement survolé par la souris. 1 pixel pas défaut. Voir “Dimensions”.
        :arg activeforeground:
                Couleur d'avant plan qui est utilisée pour le choix qui est survolé par la souris.
        :arg bg: 
                 (ou **background**) La couleur de fond utilisée pour les choix qui ne sont pas survolés par la souris.
        :arg bd:
               (ou **borderwidth**) L'épaisseur de la bordure qui entoure chaque item de choix. Voir “Dimensions”. 1 pixels par défaut.
        :arg cursor:
                Le pointeur de souris utilisé lorsque la souris survole les choix du menu, mais seulement lorsque le menu a été «détaché». Voir “Cursors”.
        :arg disabledforeground: 
                La couleur du texte pour les items de choix ayant l'état 'disabled'.
        :arg font:
                La police de caractères utilisée pour afficher les textes des choix. Voir “Type fonts”.
        :arg fg: 
                 (ou **foreground**) La couleur d'avant plan utilisée pour colorer les choix qui ne sont survolés par la souris.
        :arg postcommand:
                Vous pouvez configurer cette option avec une fonction, et cette fonction sera appelée (sans argument) à chaque fois que qu'un utilisateur fera apparaître ce menu.
        :arg relief:
                La valeur par défaut de l'effet de relief pour les menus est ``relief='raised'``. Pour d'autres valeurs, voir “Relief styles”.
        :arg selectcolor:
                Sert à préciser la couleur affichée pour les choix à cocher ou les boutons radio lorsqu'il sont activés.
        :arg tearoff:
                Normalement, un menu peut être «détaché» (il occupe alors une fenêtre qui peut être déplacée à l'écran indépendamment du bouton qui a servi à l'ouvrir): la première position (position 0) dans la liste des choix est occupée par la ligne en pointillé qui actionne le «détachement» (l'élément de tear-off), et les autres choix sont ajoutés en partant de la position 1. Si ``tearoff=0``, le menu n'a plus d'élément graphique de «détachement», et les choix sont ajoutés à partir de la position 0.
        :arg tearoffcommand:
                Si vous souhaitez que votre application soit avertie lorsque l'utilisateur clique sur l'élément graphique de «détachement» du menu, régler cette option avec une fonction qui sera appelée si le menu est effectivement détaché. Cette fonction sera appelée avec deux arguments: l'identifiant de la fenêtre mère initial du menu et l'identifiant de la fenêtre qui contient le menu «arraché».
        :arg title:
                Normalement, le titre de la fenêtre qui contient le menu détaché est le texte du bouton de menu ou le titre de la cascade qui mène à ce menu. Si vous souhaitez changer le titre de cette fenêtre, régler cette option avec la chaîne de caractères correspondante.

        Les méthodes qui suivent sont communes à tous les widget ``Menu``. Celles qui servent à créer des items de choix ont leur propre jeu d'options; voir “Menu item creation (coption) options”.

         .. hlist::
                :columns: 4

                * :py:meth:`~add`          
                * :py:meth:`~add_cascade`
                * :py:meth:`~add_checkbutton`
                * :py:meth:`~add_command`
                * :py:meth:`~add_radiobutton`
                * :py:meth:`~add_separator`
                * :py:meth:`~delete`
                * :py:meth:`~entrycget`
                * :py:meth:`~entryconfigure`
                * :py:meth:`~index`
                * :py:meth:`~insert_cascade`
                * :py:meth:`~insert_checkbutton`
                * :py:meth:`~insert_command`
                * :py:meth:`~insert_radiobutton`
                * :py:meth:`~insert_separator`
                * :py:meth:`~invoke`
                * :py:meth:`~post`
                * :py:meth:`~type`
                * :py:meth:`~yposition`

        .. py:method:: add(genre, coption, ...)

                Ajoute un choix du ``genre`` indiqué, à la suite des choix existants. L'argument ``genre`` peut être ``'cascade'``, ``'checkbutton'``, ``'command'``, ``'radiobutton'``, ou ``'separator'``. En fonction du genre indiqué, cette méthode est équivalente à ``add_cascade()``, ``add_checkbutton()``, etc. Pour plus de détails, reportez-vous à ces méthodes (voir ci-dessous).

        .. py:method:: add_cascade(coption, ...)

                Ajoute un élément de type **cascade** à la liste des éléments de choix déjà présents dans ce menu. Servez-vous de l'option **menu** pour préciser l'objet Menu qui correspond au sous-menu.

        .. py:method:: add_checkbutton(coption, ...)

                 Ajoute un choix à cocher à la liste des élements de choix déjà présents dans ce menu. Les options vous permettront de régler cet item à peu près de la même façon qu'on configure une case à cocher ``Checkbutton``. Voir “Menu item creation (coption) options”. 

        .. py:method:: add_command(coption, ...)

                 Ajoute une choix de type commande aux choix existants. Utilisez les options **label**, **bitmap**, ou **image** pour placer du texte ou une image sur le menu; utiliser l'option **command** pour connecter cet élément à une fonction qui sera appelée lorsque cet élément est sélectionné.

        .. py:method:: add_radiobutton(coption, ...)

                 Ajoute un bouton radio aux choix existants. Les options vous permettent de configurer un tel bouton à peu près de la même façon qu'un widget ``Radiobutton``; voir “The Radiobutton widget”. 

        .. py:method:: add_separator()

                 Ajoute un séparateur après le dernier choix courant du menu. Il s'agit juste d'une ligne horizontale qui peut servir à grouper des choix. Les séparateurs ont une position comme les autres choix, ainsi, si vous avez déjà trois choix et que vous ajoutez un séparateur, il occupera la position 3 (si on compte à partir de 0).

        .. py:method:: delete(index1, index2=None)

                 Cette méthode supprime les choix du menu situés entre la position ``index1`` jusqu'à la position ``index2`` inclue. Pour supprimer un seul choix, il suffit d'omettre le deuxième argument. Vous ne pouvez pas utiliser cette méthode pour détruire l'élément graphique de détachement du menu (tear-off), mais vous pouvez faire cela en mettant l'option **tearoff** du menu à 0.

        .. py:method:: entrycget(index, coption)

                 Sert à récupérer la valeur courante d'une option du choix ayant la position index dans le menu. l'option est à fournir sous la forme d'une chaîne de caractères. 

        .. py:method:: entryconfigure(index, coption, ...)

                 Pour modifier la valeur courante d'une ou de plusieurs options du choix ayant la position ``index`` dans le menu, appeler cette méthode avec l'index adéquat et un ou plusieurs arguments de la forme ``coption=valeur``. 

        .. py:method:: index(i)

                 Retourne la position du choix indiqué via l'index ``i``. Par exemple, vous pouvez utilisez  ``index(tk.END)`` pour savoir quel est le numéro d'index du dernier choix. Retourne ``None`` si aucun choix n'est trouvé.

        .. py:method:: insert_cascade(index, coption, ...)

                 Insère une cascade à la position ``index``, en partant de 0. Chaque choix situé après cette position est décalé vers le bas d'une unité. Les options sont les mêmes que pour la méthode ``add_cascade()``, ci-dessus. 

        .. py:method:: insert_checkbutton(index, coption, ...)

                 Insère un choix à cocher à la position ``index``. Les options sont les mêmes que pour la méthode ``add_checkbutton()`` ci-dessus.

        .. py:method:: insert_command(index, coption, ...)

                 Insère un choix de type commande à la position ``index``. Les options sont les mêmes que pour la méthode ``add_command()`` ci-dessus.

        .. py:method:: insert_radiobutton(index, coption, ...)

                 Insère un choix de type bouton radio à la position ``index``. Les options sont les mêmes que pour la méthode ``add_radiobutton()`` ci-dessus.

        .. py:method:: insert_separator(index)

                 Insère un séparteur à la position ``index``.

        .. py:method:: invoke(index)

                 Appelle la fonction de rappel associé à l'élément de choix situé à la position ``index``. Si c'est un choix à cocher, son état est basculé entre actif ou inactif. Si c'est un choix de type bouton radio, le bouton est activé.

        .. py:method:: post(x, y)

                 Affiche le menu à la position (x, y) relativement à la fenêtre principale.

        .. py:method:: type(index)

                 Retourne le type du choix de position ``index``: ``'cascade'``, ``'checkbutton'``, ``'command'``, ``'radiobutton'``, ``'separator'``, ou ``'tearoff'``. 

        .. py:method:: yposition(n)

                 Retourne le décalage vertical en pixel (relatif au haut du menu) de l'élément de choix numéro ``n``. La raison d'être de cette méthode est de vous permettre de calculer précisément la position où placer un menu surgissant (popup) par rapport à la position courante de la souris.

Options des items de choix d'un menu (coption)
==============================================

À chaque fois qu'une méthode de menu décrite plus haut possède un argument ``coption``, vous pouvez indiquer une valeur pour chaque nom d'option donné ci-dessous sous la forme ``coption=valeur``. Par exemple, pour créer un choix de type commande dont le texte est rouge, utiliser ``foreground='red'`` comme argument de la méthode ``add_command``.

Les options des élements de choix (coption) sont:

**accelerator** 
        Pour indiquer qu'une combinaison de touches devrait déclencher (accélérer) le choix correspondant. Utilisez l'option ``accelerator=s`` où ``s`` est une chaîne de caractères qui sera affichée sur le côté droit du choix. Par exemple, pour indiquer qu'un choix de type command est déclenché par la combinaison Control-X, utilisez ``accelerator='^X'``. Notez bien que cette option n'implémente pas l'accélérateur; Il faudra réaliser un gestionnaire d'événement pour déclencher l'action.
**activebackground** 
        La couleur d'arrière plan utilisée lorsque la souris survole le choix.
**activeforeground**
        La couleur d'avant plan (texte) utilisée lorsque la souris survole le choix.
**background**
        La couleur d'arrière plan utilisée lorsque la souris ne survole pas le choix. Notez qu'on ne peut pas utiliser l'abbréviation bg.
**bitmap**
        Affiche un bitmap pour figurer le choix; voir “Bitmaps”.
**columnbreak**
        Normalement tous les choix sont disposés les uns en dessous des autres (dans une longue colonne). Si ``columnbreak=1``, ce choix sera disposé à la droite de celui qui le précède (démarrant ainsi une nouvelle colonne).
**command**
        Une fonction de rappel qui sera appelée lorsque le choix est activé.
**compound** 
        Si vous souhaitez afficher à la fois du texte et un graphique (soit un bitmap soi une image) sur un choix de menu, utilisez cette option pour préciser la position du graphique relativement au texte. Les valeurs possibles sont ``'left'``, ``'right'``, ``'top'``, ``'bottom'``, ``'center'`` ou ``'none'``. Par exemple, si ``compound='top'``, le graphique est placé au-dessus du texte.
**font**
        La police de caractères utilisée pour l'étiquette. Voir “Type fonts”
**foreground**
        La couleur d'avant plan du choix lorsque la souris ne le survole pas. Notez qu'il n'est pas possible d'utiliser l'abbréviation fg.
**hidemargin** 
        Par défaut, une petite marge sépare deux choix adjacents dans le menu. Utilisez ``hidemargin=True`` pour supprimer cette marge. Par exemple, si vos choix sont les couleurs d'une palette, cette option permet de réaliser une transition continue entre les couleurs.
**image**
        Affiche une image pour ce choix; voir “Images”.
**label**
        La chaîne de caractères qui contient le texte à afficher pour ce choix.
**menu**
        Cette option est disponible uniquement pour les choix de type cascade. Configurez là avec un widget ``Menu`` qui sera chargé de contenir le sous menu.
**offvalue**
        Normalement, la variable de contrôle pour un choix à cocher est 0 si ce choix est désactivé. Vous pouvez modifier la valeur associée à l'état désactivé en en utilisant cette option. Voir “Control variables: the values behind the widgets”.
**onvalue**
        Normalement, la variable de contrôle pour un choix à cocher est 1 si ce choix est activé. Vous pouvez modifer la valeur associée à l'état activé en utilisant cette option.
**selectcolor**
        Normalement, la couleur utilisée pour un ensemble de choix à cocher ou de boutons radio est rouge. Modifiez cette couleur en configurant cette option avec la couleur voulue; voir “Colors”.
**selectimage** 
        Si vous utilisez l'option image pour afficher un graphique à la place du texte d'un choix à cocher ou d'un bouton radio, en utilisant ``selectimage=I``, l'image ``I`` sera affichée lorsque l'élément est sélectionné.
**state**
        Par défaut, tous les choix réagissent aux clics souris, mais vous pouvez utiliser ``state='disabled'`` pour griser et rendre le choix courant insensible à la souris. Cette option prend la valeur ``'active'`` lorsque la souris survole le choix.
**underline**
        Par défaut, aucun caractère de l'étiquette n'est souligné. Configurez cette option avec l'index du caractère que vous souhaitez souligner.
**value**
        Sert à préciser la valeur de la variable de contrôle associée à ce choix (voir “Control variables: the values behind the widgets”) pour un bouton radio. Vous pouvez utiliser un entier si la variable de contrôle est une ``IntVar``, ou une chaîne de caractères si c'est une ``StringVar``.
**variable**
        Pour les choix à cocher ou les choix de type bouton radio, cette option devrait être configurée en utilisant une variable de contrôle (partagée par un ensemble de boutons radio). Voir “Control variables: the values behind the widgets”. 

Barre de menus
==============

Pour créer une barre de menu principale, c'est à dire sous le bord supérieur de la fenêtre de l'application (Avec MacOS, il apparaîtra tout en haut de l'écran lorsque l'application a le focus), procéder comme cela:

* Récupérer (éventuellement) la fenêtre principale à partir d'un widget arbitraire ``w`` en utilisant la méthode ``w.winfo_toplevel()``.

* Créer un widget ``Menu`` en utilisant la fenêtre principale comme premier argument du constructeur et passer le à l'option **menu** de la fenêtre principale.

* Ajouter des choix de type cascade pour autant d'entrées que souhaitées dans la barre des menus.
  
* Associer un sous menu à chaque cascade.

Voici un simple exemple (``root`` désigne la fenêtre principale). Ce code créera un barre de menu formée de d'un choix de premier niveau "Aide" (cascade) lequel donnera accès à un choix "À propos" (command) qui appelera la gestionnaire ``aproposGest``::

    menuBar = Menu(root)
    root['menu'] = menuBar

    sousMenu = Menu(menuBar)
    menuBar.add_cascade(label='Aide', menu=sousMenu)
    sousMenu.add_command(label='À propos', command=aproposGest)

Note: Vous devez utiliser la méthode ``add_cascade()`` pour ajouter les choix que vous souhaitez proposer dans la barre de menu principale. Les appels aux méthodes ``add_checkbutton()``, ``add_command()``, ou ``add_radiobutton()`` seront ignorés dans ce contexte.

On constate certaines variations de comportement selon la plateforme utilisée.

* Pour Windows ou les systèmes Unix (linux par ex.), le menu principal de fenêtre apparaît sous le bord supérieur de la fenêtre principale de l'application.

* Pour MacOS X, le menu principal apparaît tout en haut de l'écran quand l'application a le focus, juste à l'endroit où les utilisateurs d'un Mac s'attendent à le voir.

