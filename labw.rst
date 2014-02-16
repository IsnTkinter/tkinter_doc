.. _LABEL:

**************************
``Label`` - Les étiquettes 
**************************

Les widget ``Label`` (étiquette) servent à afficher une ou plusieurs lignes de texte avec le même style, un bitmap ou une image.
Pour créer une étiquette dans une fenêtre principale ou dans un cadre ``parent``: 

.. py:class:: Label(parent, option, ...)

   Le constructeur retourne l'étiquette crée. Ses options sont:

   :arg activebackground:
           Couleur de fond lorsque la souris survole l'étiquette.
   :arg activeforeground:
           Couleur du texte lorsque la souris survole l'étiquette.
   :arg anchor:
           Cette option précise la postion du texte si le widget dispose de plus de place que de besoin pour le texte. La valeur par défaut est ``'center'``, ce qui a pour effet de centrer le texte par rapport à l'espace disponible. Pour d'autres valeur, Voir :ref:`ancrage`. Par exemple, si vous utilisez ``anchor='nw'``, le texte sera positionné dans le coin supérieur gauche de l'espace disponible.
   :arg background: 
           (ou **bg**) La couleur de fond de l'étiquette. Voir :ref:`couleurs`.
   :arg bitmap:
           Donner à cet option un bitmap ou un objet image et l'étiquette sera affichée avec ce graphique. Voir :ref:`bitmaps` et :ref:`images`.
   :arg borderwidth:
           (ou **bd**) Épaisseur de la bordure autour de l'étiquette; voir :ref:`dimensions`. La valeur par défaut est 2 pixels.
   :arg compound:
           Si vous souhaitez que l'étique affiche à la fois un texte et un graphique (soit un bitmap, soit une image), cette option sert à préciser l'orientation relative de l'image par rapport au texte. Les valeur peuvent-être ``'left'``, ``'right'``, ``'center'``, ``'bottom'`` ou ``'top'``. Par exemple, si ``compound=BOTTOM``, le graphique sera affiché en-dessous du texte.
   :arg cursor:
           Le pointeur de la souris lorsqu'elle survole l'étiquette. Voir :ref:`pointeurs`.
   :arg disabledforeground:
           La couleur d'avant plan à afficher lorsque l'étiquette est ``'disabled'``.
   :arg font:
           Si vous affichez du texte dans cette étiquette (avec l'option **text** ou **textvariable**), cette option sert à préciser la police de caractères utilisée pour afficher le texte. Voir :ref:`polices`.
   :arg foreground:
           (ou **fg**) Couleur d'avant plan de l'étiquette. Elle sera utilisée pour le texte ou pour les bits à 1 du bitmap. Voir :ref:`couleurs`.
   :arg height:	
           Hauteur de l'étiquette en nombre de lignes (non en pixels). Si cette option n'est pas précisée, l'étiquette s'ajuste à son contenu.
   :arg highlightbackground:
           Couleur de mise en valeur du focus quand le widget l'a perdu.
   :arg highlightcolor:
           Couleur de mise en valeur du focus quand le widget l'a obtenu.
   :arg highlightthickness:
           Épaisseur de la ligne de mise en valeur du focus.
   :arg image:
           Pour afficher une image dans une étiquette, indiquer un objet image pour cette option. Voir :ref:`images`.
   :arg justify:
           Précise l'alignement du texte: 'left' pour un alignement à gauche, 'center' pour centrer et 'right' pour un alignement à droite.
   :arg padx:
           Espace horizontal supplémentaire à insérer à gauche et à droite dans l'étiquette. Sa valeur par défaut est 1.
   :arg pady:	
           Similaire à **padx** mais pour la direction verticale.
   :arg relief:
           Précise l'apparence de la bordure décorative autour de l'étiquette. Par défaut, vaut ``'flat'``; pour d'autres valeurs, voir :ref:`reliefs`.
   :arg state:
           Par défaut, une étiquette est dans l'état 'normal'. Les autres états possibles sont 'disabled' et 'active' (les couleurs d'arrière plan et d'avant plan pour ces états sont alors utilisées).
   :arg takefocus:
           Normalement, une étiquette n'obtient pas le focus; voir :ref:`FOCUS`. Si vous souhaitez que l'étiquette le reçoive, mettre 1 pour cette option.
   :arg text:
           Pour afficher une ou plusieurs ligne de texte dans une étiquette, indiquer une chaîne de caractères qui contient le texte. Le caractère spécial ``'\n'`` forcera la retour à la ligne.
   :arg textvariable:
           Pour pouvoir faire varier le texte affiché en même temps que la valeur d'une variable de contrôle de type ``StringVar``, régler cette option avec cette variable. Voir :ref:`CTRLVARIABLES`.
   :arg underline:
           Vous pouvez souligner l'un des caractères du texte en indiquant sa position (à partir de 0). Par défaut, ``underline=-1``, ce qui signifie aucun soulignement.
   :arg width:
           Largeur de l'étiquette exprimée en nombre de caractères (non en pixels). Si cette option n'est pas précisée, l'étiquette s'ajuste à son contenu.
   :arg wraplength:
           Vous pouvez limiter le nombre de caractère sur chaque ligne en le précisant pour cette option. La valeur par défaut est 0, ce qui signifie que les lignes ne seront coupées que si il y a un saut de ligne.

Il n'y a pas de méthodes spécifiques aux étiquettes. Voir :ref:`UNIVERSAL`.
