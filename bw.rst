.. _BOUTONS:

**********************
Les Boutons ``Button``
**********************

Pour créer un simple bouton dans une fenêtre autonome ou un cadre nommé ``parent``:

.. py:class:: Button(parent, option=valeur, ...)

    Le constructeur retourne le nouveau widget bouton. Ces options sont :


    :arg activebackground:
            Couleur de fond lorsque la souris survole le bouton.
    :arg activeforeground:
            Couleur du texte lorsque la souris survole le bouton.
    :arg anchor:
            Précise la position du texte sur le bouton.
            Voir :ref:`ancrage`.
            Par exemple, anchor="ne" positionne le texte dans le bord supérieur droit (nord est) du bouton.
    :arg borderwidth: 
            aussi bd ; la largeur de la bordure around the outside of the button; Voir :ref:`dimensions`.
            The default is two pixels.
    :arg background:
            aussi bg ; Normal background color.
    :arg bitmap: 
            Name of one of the standard bitmaps to display on the button (instead of text).
    :arg command:
            Function or method to be called when the button is clicked.
    :arg cursor:
            Selects the cursor to be shown when the mouse is over the button. 
    :arg default:
            tk.NORMAL is the default; use tk.DISABLED if the button is to be initially disabled (grayed out, unresponsive to mouse clicks).
    :arg disabledforeground:
             Foreground color used when the button is disabled.
    :arg foreground:
             Aussi fg, Normal foreground (text) color.
    :arg font:
            Text font to be used for the button's label.
    :arg height:
            Height of the button in text lines (for textual buttons) or pixels (for images).
    :arg highlightbackground:
             Color of the focus highlight when the widget does not have focus.
    :arg highlightcolor:
             The color of the focus highlight when the widget has focus.
    :arg highlightthickness:
             Thickness of the focus highlight.
    :arg image:
            Image to be displayed on the button (instead of text).
    :arg justify:
            How to show multiple text lines: tk.LEFT to left-justify each line; tk.CENTER to center them; or tk.RIGHT to right-justify.
    :arg overrelief:
            The relief style to be used while the mouse is on the button; default relief is tk.RAISED. Voir :ref:`reliefs`.
    :arg padx:
            Additional padding left and right of the text. Voir :ref:`dimensions`.
            for the possible values for padding.
    :arg pady:
            Additional padding above and below the text.
    :arg relief:
            Specifies the relief type for the button (Voir :ref:`reliefs`).
            The default relief is tk.RAISED.
    :arg repeatdelay:
            See repeatinterval, below.
    :arg repeatinterval:
            Normally, a button fires only once when the user releases the mouse button. If you want the button to fire at regular intervals as long as the mouse button is held down, set this option to a number of milliseconds to be used between repeats, and set the repeatdelay to the number of milliseconds to wait before starting to repeat. For example, if you specify “repeatdelay=500, repeatinterval=100” the button will fire after half a second, and every tenth of a second thereafter, until the user releases the mouse button. If the user does not hold the mouse button down at least repeatdelay milliseconds, the button will fire normally.
    :arg state:
            Set this option to tk.DISABLED to gray out the button and make it unresponsive. Has the value tk.ACTIVE when the mouse is over it. Default is tk.NORMAL.
    :arg takefocus:
            Normally, keyboard focus does visit buttons (see Section 53, “Focus: routing keyboard input”), and a space character acts as the same as a mouse click, “pushing” the button. You can set the takefocus option to zero to prevent focus from visiting the button.
    :arg text:
            Text displayed on the button. Use internal newlines to display multiple text lines.
    :arg textvariable:
            An instance of StringVar() that is associated with the text on this button. If the variable is changed, the new value will be displayed on the button. See Section 52, “Control variables: the values behind the widgets”.
    :arg underline:
            Default is -1, meaning that no character of the text on the button will be underlined. If nonnegative, the corresponding text character will be underlined. For example, underline=1 would underline the second character of the button's text.
    :arg width:
            Width of the button in letters (if displaying text) or pixels (if displaying an image).
    :arg wraplength:
            If this value is set to a positive number, the text lines will be wrapped to fit within this length. For possible values, Voir :ref:`dimensions`.

    .. py:method:: flash()

            Causes the button to flash several times between active and normal colors. Leaves the button in the state it was in originally. Ignored if the button is disabled. 

    .. py:method:: invoke()

            Calls the button's command callback, and returns what that function returns. Has no effect if the button is disabled or there is no callback. 
