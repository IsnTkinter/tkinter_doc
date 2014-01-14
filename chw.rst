.. _COCHER:

**********************************
Les cases à cocher ``Checkbutton``
**********************************

Le but d'un widget de cases à cocher (parfois appelé «checkbox») est de permettre à l'utilisateur de lire et sélectionner un choix entre deux options. Le graphique ci-dessus montre à quoi ressemble une case dans l'état OFF (0) et ON (1) lors de l'utilisation : il s'agit d'une capture d'écran de deux cases à cocher avec une police de 24 points en Times.

L'indicateur est la partie de la case à cocher qui indique son état, et l'étiquette est le texte qui apparaît à côté.

    Vous aurez besoin de créer une variable, une instance de la classe IntVar, afin que votre programme puisse interroger et définir l'état de la case à cocher. Voir la section 52, «Les variables de contrôle: les valeurs derrière les widgets", ci-dessous.

    Vous pouvez également utiliser des liaisons d'événements pour réagir aux actions de l'utilisateur sur la case à cocher, voir la section 54, «Événements», ci-dessous.

    Vous pouvez désactiver une case à cocher. Cela modifie son apparence pour "grisé" et la rend insensible à la souris.

    Vous pouvez vous débarrasser de l'indicateur de case à cocher et donner une allure de widget bouton "push-push" qui paraît enfoncé quand il est activé, et soulevé quand il est désactivé.

Pour créer une case à cocher dans une fenêtre parent ou un cadre parent existant:

.. py:class:: Checkbutton(parent, option, ...)

        Le constructeur renvoie un nouveau widget Checkbutton. Les options incluent:

        :arg activebackground: 
                La couleur de fond lorsque la case à cocher est sous le curseur. Voir la section 5.3, "Les couleurs".
        :arg activeforeground: 
                La couleur du premier plan lorsque la case à cocher est sous le curseur.
        :arg anchor:
                Si le widget se situe dans un espace plus grand que nécessaire, cette option spécifie où la case à cocher va se placer dans cet espace. La valeur par défaut est anchor=tk.CENTER. Voir la section 5.5, "Le système d'ancrage" pour les valeurs permises. Par exemple, si vous utilisez anchor=NW, le widget sera placé dans le coin supérieur gauche de l'espace.
        :arg bg: or background
                La couleur de fond normale s'affiche derrière l'étiquette et indicateur. Voir la section 5.3, "Les couleurs". Pour l'option bitmap, ceci spécifie la couleur affichée pour le bit 0 dans le bitmap.
        :arg bitmap:
                Pour afficher une image monochrome sur un bouton, affectez un bitmap à cette option; voir :ref:`bitmaps`.
        :arg bd: or borderwidth
                La taille de la bordure autour de l'indicateur. Elle est par défaut de deux pixels. Pour les valeurs possibles, voir :ref:`bitmaps`.
        :arg command:
                Pour appeler une procédure à chaque fois que l'utilisateur change l'état de cette case à cocher.
        :arg compound: 
                Utilisez cette option pour afficher le texte et un graphique, qui peut être un bitmap ou une image, sur le bouton. Les valeurs autorisées décrivent la position du graphique par rapport au texte, et peuvent être l'une des suivantes : tk.BOTTOM, tk.TOP, tk.LEFT, tk.RIGHT, ou tk.CENTER. Par exemple, compound=tk.LEFT positionnerait le graphique à gauche du texte.
        :arg cursor:
                Si vous définissez cette option par un nom de curseur (voir :ref:`pointeurs`),
                le curseur de la souris se transforme en ce modèle quand il est sur la case à cocher.
        :arg disabledforeground:
                La couleur de premier plan utilisée pour afficher le texte d'une case à cocher désactivée. La valeur par défaut est une version pointillée de la couleur de premier plan par défaut.
        :arg font:
                La police utilisée pour le texte. Voir la section 5.4, "Les polices de caractères".
        :arg fg: or foreground
                La couleur utilisée pour afficher le texte. Pour l'option bitmap, ceci spécifie la couleur affichée pour le bit 1 dans le bitmap.
        :arg height:
                Le nombre de lignes de texte sur la case à cocher. La valeur par défaut est 1.
        :arg highlightbackground:
                color of the focus highlight when the checkbutton does not have focus. See Section 53, “Focus: routing keyboard input”.
        :arg highlightcolor:
                The color of the focus highlight when the checkbutton has the focus.
        :arg highlightthickness:
                The thickness of the focus highlight. Default is 1. Set to 0 to suppress display of the focus highlight.
        :arg image:
                Pour afficher une image graphique sur le bouton, affectez une une image à cette option. Voir la section 5.9, "Les images".
        :arg indicatoron:
                Normalement, l'indicateur de la case à cocher indique si la case à cocher est activée ou pas. Vous pouvez obtenir ce comportement en définissant indicatoron=1. Toutefois, si vous définissez indicatoron=0, l'indicateur disparaît et le widget entier devient un bouton push-push qui paraît enfoncé quand il est activé, et soulevé quand il est désactivé. Vous pouvez augmenter la valeur borderwidth pour rendre plus facile la lecture de l'état d'un tel contrôle.
        :arg justify:
                Si le texte contient plusieurs lignes, cette option contrôle la manière dont le texte est justifié: tk.CENTER, tk.LEFT, ou tk.RIGHT.
        :arg offrelief: 
                Par défaut, les cases à cocher utilisent le style de relief tk.RAISED lorsque le bouton est désactivé (autorisé); utiliser cette option pour spécifier un style différent de relief à afficher lorsque le bouton est éteint. Voir la section 5.6, "Les styles de relief" pour les valeurs.
        :arg offvalue:
                Normalement, la variable de contrôle associée à une case à cocher sera mise à 0 quand cette case est désactivée (OFF). Vous pouvez fournir une autre valeur pour cette état OFF en affectant cette valeur à offvalue.
        :arg onvalue:
                Normalement, la variable de contrôle associée à une case à cocher sera mise à 1 quand cette case est activée (ON). Vous pouvez fournir une autre valeur pour cette état ON en affectant cette valeur à offvalue.
        :arg overrelief: 
                Utilisez cette option pour spécifier un style de relief à afficher lorsque la souris est sur la case à cocher; voir :ref:`reliefs`.
        :arg padx:
                Combien d'espace à laisser à gauche et à droite de la case à cocher et du texte. La valeur par défaut est de 1 pixel. Pour les valeurs possibles, voir :ref:`dimensions`.
        :arg pady:
                Combien d'espace à laisser au-dessus et en dessous de la case à cocher et du texte. La valeur par défaut est de 1 pixel.
        :arg relief:
                Avec la valeur par défaut, relief=tk.FLAT, la case à cocher ne se distingue pas de son arrière-plan. Vous pouvez configurer cette option pour l'un des autres styles (voir :ref:`reliefs`),
                ou utiliser relief=tk.SOLID, ce qui vous donne un cadre noir fixe autour de lui.
        :arg selectcolor:
                The color of the checkbutton when it is set. Default is selectcolor='red'.
        :arg selectimage:
                If you set this option to an image, that image will appear in the checkbutton when it is set. See Section 5.9, “Images”.
        :arg state:
                The default is state=tk.NORMAL, but you can use state=tk.DISABLED to gray out the control and make it unresponsive. If the cursor is currently over the checkbutton, the state is tk.ACTIVE.
        :arg takefocus:
                The default is that the input focus (see Section 53, “Focus: routing keyboard input”) will pass through a checkbutton. If you set takefocus=0, focus will not pass through it.
        :arg text:
                The label displayed next to the checkbutton. Use newlines ('\n') to display multiple lines of text.
        :arg textvariable:
                If you need to change the label on a checkbutton during execution, create a StringVar (see Section 52, “Control variables: the values behind the widgets”) to manage the current value, and set this option to that control variable. Whenever the control variable's value changes, the checkbutton's annotation will automatically change as well.
        :arg underline:
                With the default value of -1, none of the characters of the text label are underlined. Set this option to the index of a character in the text (counting from zero) to underline that character.
        :arg variable:
                The control variable that tracks the current state of the checkbutton; see Section 52, “Control variables: the values behind the widgets”. Normally this variable is an IntVar, and 0 means cleared and 1 means set, but see the offvalue and onvalue options above.
        :arg width:
                The default width of a checkbutton is determined by the size of the displayed image or text. You can set this option to a number of characters and the checkbutton will always have room for that many characters.
        :arg wraplength:
                Normally, lines are not wrapped. You can set this option to a number of characters and all lines will be broken into pieces no longer than that number.

        Methods on checkbuttons include:

        .. py:method:: deselect()

                Clears (turns off) the checkbutton. 

        .. py:method:: flash()

                Flashes the checkbutton a few times between its active and normal colors, but leaves it the way it started. 

        .. py:method:: invoke()

                You can call this method to get the same actions that would occur if the user clicked on the checkbutton to change its state. 

        .. py:method:: select()

                Sets (turns on) the checkbutton. 

        .. py:method:: toggle()

                Clears the checkbutton if set, sets it if cleared. 
