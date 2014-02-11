.. _RADIOBUTTON:

*********************************
Les boutons radio ``Radiobutton``
*********************************

Les boutons radio sont des ensembles de widgets connexes qui permettent à l'utilisateur de sélectionner un seul d'un ensemble de choix. Chaque bouton radio se compose de deux parties, l'indicateur et l'étiquette:

* L'indicateur est la partie en forme de losange qui vire au rouge à l'élément sélectionné.

* L'étiquette est le texte, mais vous pouvez utiliser une image bitmap en guise d'étiquette.

* Si vous préférez, vous pouvez vous passer de l'indicateur. Les boutons radio ressemblent alors à des boutons "push-push", avec l'entrée sélectionnée apparaissant enfoncée et les autres entrées apparaissant soulevées.

* Pour réunir plusieurs boutons radio dans un groupe fonctionnel, créer une variable de contrôle unique (voir la section 52, «Les variables de contrôle: les valeurs derrière les widgets", ci-dessous), et réglez l'option variable de chaque bouton radio à cette variable.

* La variable de contrôle peut être soit un IntVar, soit un StringVar. Si deux ou plusieurs boutons radio partagent la même variable de contrôle, régler l'un d'entre eux remplacera le réglage des autres.

* Chaque bouton radio dans un groupe doit avoir une unique option de valeur du même type que la variable de contrôle. Par exemple, un groupe de trois boutons radio pourrait partager un IntVar et avoir pour valeurs 0, 1 et 99. Ou vous pouvez utiliser une variable de contrôle StringVar et donner aux boutons radio comme options de valeur 'trop chaud', 'trop froid' et 'correct'.

Pour créer un nouveau widget bouton radio en tant qu'enfant d'une fenêtre ou d'un cadre nommé parent:

.. py:class:: Radiobutton(parent, option, ...)

        Ce constructeur renvoie le nouveau widget Radiobutton. Les options sont:

        :arg activebackground:
                La couleur d'arrière plan utilisé quand la souris est au-dessus du widget. Voir “Colors”.
        :arg activeforeground:
                La couleur du texte lorsque la souris est au-dessus du widget.
        :arg anchor:
                Si le widget occupe plus de place que de besoin, cette option sert à préciser la position occupé par le bouton dans cet espace. La valeur par défaut est 'center'. Pour d'autres positions, reportez-vous à  “Anchors”. Par exemple, si anchor="ne", le bouton sera positionné au nord-est, c'est à dire dans le coin supérieur droit.
        :arg bg: 
                (ou **background**) La couleur d'arrière plan du widget.
        :arg bitmap:
                Pour afficher une image monochrome à côté du bouton radio, configurer cette option avec un bitmap; voir “Bitmaps”.
        :arg bd: 
                (ou **borderwidth**) L'épaisseur de la bordure de l'indicateur (c'est à dire du bouton lui-même). 2 pixels par défaut. Pour connaître les valeurs possibles, voir “Dimensions”.
        :arg command:
                Une fonction qui sera appelée à chaque fois que l'utilisateur modifiera l'état du bouton.
        :arg compound: 
                If you specify both text and a graphic (either a bitmap or an image), this option specifies where the graphic appears relative to the text. Possible values are tk.NONE (the default value), tk.TOP, tk.BOTTOM, tk.LEFT, tk.RIGHT, and tk.CENTER. For example, compound=tk.BOTTOM would position the graphic below the text. If you specify compound=tk.NONE, the graphic is displayed but the text (if any) is not.
        :arg cursor:
                Le pointeur de souris à afficher lorsque la souris est au-dessus du bouton radio. Voir "Cursors”
        :arg disabledforeground:
                La couleur du texte lorsque le bouton est dans l'état 'disabled'. La valeur par défaut est une version  en "pointillée" de la couleur par défaut de l'option "foreground".
        :arg font:
                La fonte de caractères utilisée pour le texte. Voir “Type fonts”.
        :arg fg: 
                (ou **foreground**) La couleur de l'étiquette.
        :arg height:
                Le nombre de ligne (non des pixels) de texte que peut contenir le widget. 1 par défaut.
        :arg highlightbackground:
                La couleur de la ligne de mise en valeur du focus lorsque le widget ne l'a pas. Voir “Focus: routing keyboard input”.
        :arg highlightcolor:
                La couleur de la ligne de mise en valeur du focus lorsque le widget l'obtient.
        :arg highlightthickness:
                L'épaisseur de la ligne de mise en valeur du focus. 1 par défaut. Mettre cette option à 0 pour supprimer la mise en valeur du focus.
        :arg image:
                Pour afficher une image plutôt que du texte à côté du bouton radio, configurez cette option avec l'objet image désirée. Voir “Images”. L'image apparaît lorsque le bouton radio est désactivé; comparez avec l'option **selectimage** ci-dessous.
        :arg indicatoron:
                Normalement un bouton radio est accompagné d'un indicateur. Si vous configurez cette option avec 0, l'indicateur n'apparaît plus, et le widget se comporte comme un bouton "poussoir": Il semble enfoncé lorsqu'on l'active ou "émergent" sinon. Vous pouvez renforcer cet effet en augmentant la valeur de l'option **borderwidth** ce qui rendra l'état du bouton plus visible.
        :arg justify:
                Si le texte est formé de plusieurs ligne, cette option permet de contrôler l'alignement. Les valeurs possbiles sont: 'center' (par défaut), 'left', ou 'right'.
        :arg offrelief:
                Si vous supprimez l'indicateur en utilisant ``indicatoron=False``, cette option sert à préciser le style de relief à appliquer au bouton lorsqu'il est désactivé. La valeur par défaut est 'raised'.
        :arg overrelief: 
                Le relief a utiliser lorsque la souris est au-dessus du bouton radio.
        :arg padx:
                Espace supplémentaire à ajouter à gauche et droite du texte et du bouton.
        :arg pady:
                Espace supplémentaire à ajouter en haut et en bas du texte et du bouton. 1 pixel par défaut.
        :arg relief:
                Par défaut, un bouton radio a un style de relief 'flat' ce qui fait qu'il ne ressort pas de ce qui l'entoure. Pour d'autres style de relief, voir  “Relief styles”. Vous pouvez utiliser l'option relief='solid' afin d'afficher un cadre autour.
        :arg selectcolor:
                La couleur du bouton radio lorsqu'il est activé. 'red' par défaut.
        :arg selectimage:
                Si vous utilisez l'option **image** pour afficher un graphique plutôt qu'une étiquette lorsque le bouton n'est pas activé, vous pouvez configurer cette option avec une image différente qui sera affichée lorsque le bouton est activée. Voir “Images”.
        :arg state:
                L'état par défaut est 'normal', mais vous pouvez utiliser la valeur 'disabled' pour griser le bouton et le rendre inactif. Lorsque la souris est au-dessus du bouton, son état devient 'active'.
        :arg takefocus:
                Par défaut, ce widget reçoit le focus (voir “Focus: routing keyboard input”). will pass through a radiobutton. If you set takefocus=0, focus will not visit this radiobutton.
        :arg text:
                L'étiquette ou texte qui est affiché à côté du bouton radio. Utiliser le caractère spacial '\n' pour faire un saut de ligne.
        :arg textvariable:
                Si vous avez besoin de modifier dynamiquement (au fil de l'exécution) l'étiquette d'un bouton radio, créez une variable de contrôle de classe StringVar (voir “Control variables: the values behind the widgets”) qui servira à gérer la valeur courante de l'étiquette, et configurez cette option avec celle-ci. Lorsque la valeur de la variable de contrôle est modifiée (en utilisant sa méthode set), l'étiquette du bouton radio sera mise à jour dans le même temps.
        :arg underline:
                With the default value of -1, none of the characters of the text label are underlined. Set this option to the index of a character in the text (counting from zero) to underline that character.
        :arg value:
                Lorsque le bouton radio est activé par l'utilisateur, sa variable de contrôle prend la valeur indiquée par cette option. Selon que la variable de contrôle est un IntVar ou un StringVar, donner à chaque radio bouton du groupe auquel il appartient une valeur différente (chaîne ou entière) de façon à reconnaître celui qui a été activé.
        :arg variable:
                The control variable that this radiobutton shares with the other radiobuttons in the group; see Section 52, “Control variables: the values behind the widgets”. This can be either an IntVar or a StringVar.
        :arg width:
                The default width of a radiobutton is determined by the size of the displayed image or text. You can set this option to a number of characters (not pixels) and the radiobutton will always have room for that many characters.
        :arg wraplength:
                Normally, lines are not wrapped. You can set this option to a number of characters and all lines will be broken into pieces no longer than that number.

        Methods on radiobutton objects include:

        .. py:method:: deselect()

                    Clears (turns off) the radiobutton. 

        .. py:method:: flash()

                    Flashes the radiobutton a few times between its active and normal colors, but leaves it the way it started. 

        .. py:method:: invoke()

                    You can call this method to get the same actions that would occur if the user clicked on the radiobutton to change its state. 

        .. py:method:: select()

                    Sets (turns on) the radiobutton. 
