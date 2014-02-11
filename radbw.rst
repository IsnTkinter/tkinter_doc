.. _RADIOBUTTON:

**********************
Les boutons radio ``Radiobutton``
**********************

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
                The foreground color used to render the text of a disabled radiobutton. The default is a stippled version of the default foreground color.
        :arg font:
                The font used for the text. See Section 5.4, “Type fonts”.
        :arg fg: 
                (ou **foreground**) La couleur de l'étiquette.
        :arg height:
                Le nombre de ligne (non des pixels) de texte que peut contenir le widget. 1 par défaut.
        :arg highlightbackground:
                The color of the focus highlight when the radiobutton does not have focus. See Section 53, “Focus: routing keyboard input”.
        :arg highlightcolor:
                The color of the focus highlight when the radiobutton has the focus.
        :arg highlightthickness:
                The thickness of the focus highlight. Default is 1. Set highlightthickness=0 to suppress display of the focus highlight.
        :arg image:
                To display a graphic image instead of text for this radiobutton, set this option to an image object. See Section 5.9, “Images”. The image appears when the radiobutton is not selected; compare selectimage, below.
        :arg indicatoron:
                Normally a radiobutton displays its indicator. If you set this option to zero, the indicator disappears, and the entire widget becomes a “push-push” button that looks raised when it is cleared and sunken when it is set. You may want to increase the borderwidth value to make it easier to see the state of such a control.
        :arg justify:
                If the text contains multiple lines, this option controls how the text is justified: tk.CENTER (the default), tk.LEFT, or tk.RIGHT.
        :arg offrelief: 
                If you suppress the indicator by asserting indicatoron=False, the offrelief option specifies the relief style to be displayed when the radiobutton is not selected. The default values is tk.RAISED.
        :arg overrelief: 
                Specifies the relief style to be displayed when the mouse is over the radiobutton.
        :arg padx:
                Espace supplémentaire à ajouter à gauche et droite du texte et du bouton.
        :arg pady:
                Espace supplémentaire à ajouter en haut et en bas du texte et du bouton. 1 pixel par défaut.
        :arg relief:
                By default, a radiobutton will have tk.FLAT relief, so it doesn't stand out from its background. See Section 5.6, “Relief styles” for more 3-d effect options. You can also use relief=tk.SOLID, which displays a solid black frame around the radiobutton.
        :arg selectcolor:
                La couleur du bouton radio lorsqu'il est activé. 'red' par défaut.
        :arg selectimage:
                If you are using the image option to display a graphic instead of text when the radiobutton is cleared, you can set the selectimage option to a different image that will be displayed when the radiobutton is set. See Section 5.9, “Images”.
        :arg state:
                The default is state=tk.NORMAL, but you can set state=tk.DISABLED to gray out the control and make it unresponsive. If the cursor is currently over the radiobutton, the state is tk.ACTIVE.
        :arg takefocus:
                Par défaut, ce widget reçoit le focus (voir “Focus: routing keyboard input”). will pass through a radiobutton. If you set takefocus=0, focus will not visit this radiobutton.
        :arg text:
                L'étiquette ou texte qui est affiché à côté du bouton radio. Utiliser le caractère spacial '\n' pour faire un saut de ligne.
        :arg textvariable:
                If you need to change the label on a radiobutton during execution, create a StringVar (see Section 52, “Control variables: the values behind the widgets”) to manage the current value, and set this option to that control variable. Whenever the control variable's value changes, the radiobutton's annotation will automatically change to that text as well.
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
