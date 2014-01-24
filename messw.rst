.. _MESSAGE:

******************
Les Messages Message
******************

 Ce widget est semblable au widget Label (voir la section 12, «Les étiquettes"), mais il est destiné à l'affichage des messages sur plusieurs lignes. Tout le texte sera affiché dans la même police, si vous avez besoin d'afficher du texte avec plusieurs polices, voir la section 24, «Le widget texte".

Pour créer un nouveau message comme l'enfant d'une fenêtre ou d'un cadre nommé parent:

.. py:class:: Message(parent, option, ...)

       Le constructeur renvoie le nouveau widget Message. Ses options sont:

        :arg aspect: 
                Utilisez cette option pour spécifier le rapport largeur sur hauteur en pourcentage. Par exemple, aspect=100 vous donnerait un message en forme de texte dans un carré; avec aspect=200, la zone de texte serait deux fois plus large que haute. La valeur par défaut est 150, c'est-à-dire que le texte apparaît dans une boîte 50% plus large que haute.
        :arg bg: or background 
                La couleur de fond derrière le texte, voir la section 5.3 "Les couleurs".
        :arg bd: or borderwidth 
                Largeur de la bordure autour du widget, voir la section 5.1 "Les dimensions". La valeur par défaut est de deux pixels. Cette option est visible uniquement lorsque l'option de relief n'est pas 'flat'.
        :arg cursor: 
                Specifies the cursor that appears when the mouse is over the widget; see Section 5.8, “Cursors”.
        :arg font: 
                Specifies the font used to display the text in the widget; see Section 5.4, “Type fonts”.
        :arg fg: or foreground 
                Specifies the text color; see Section 5.3, “Colors”.
        :arg highlightbackground: 
                Color of the focus highlight when the widget does not have focus. See Section 53, “Focus: routing keyboard input”.
        :arg highlightcolor:
                Color shown in the focus highlight when the widget has the focus.
        :arg highlightthickness:
                Thickness of the focus highlight.
        :arg justify: 
                Use this option to specify how multiple lines of text are aligned. Use justify=tk.LEFT to get a straight left margin; justify=tk.CENTER to center each line; and justify=tk.RIGHT to get a straight right margin.
        :arg padx: 
                Use this option to add extra space inside the widget to the left and right of the text. The value is in pixels.
        :arg pady: 
                Use this option to add extra space inside the widget above and below the text. The value is in pixels.
        :arg relief: 
                This option specifies the appearance of the border around the outside of the widget; see Section 5.6, “Relief styles”. The default style is tk.FLAT.
        :arg takefocus: 
                Normally, a Message widget will not acquire focus (see Section 53, “Focus: routing keyboard input”). Use takefocus=True to add the widget to the focus traversal list.
        :arg text: 
                The value of this option is the text to be displayed inside the widget.
        :arg textvariable: 
                If you would like to be able to change the message under program control, associate this option with a StringVar instance (see Section 52, “Control variables: the values behind the widgets”). The value of this variable is the text to be displayed. If you specify both text and textvariable options, the text option is ignored.
        :arg width: 
                Use this option to specify the width of the text area in the widget, in pixels. The default width depends on the displayed text and the value of the aspect option. 
