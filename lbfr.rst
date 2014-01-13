.. _LABELFRAME:

***********************************
Les cadres étiquetés ``LabelFrame``
***********************************

Le widget «cadre étiquetté», ``LabelFrame``, comme le widget ``Frame``, est avant tout un conteneur. Il se présente comme une zone rectangulaire dans laquelle il est possible de mettre d'autres widgets. Cependant, contrairemet au cadre ``Frame``, ce cadre vous permet d'afficher une étiquette sur sa bordure.

Voici un exemple de cadre étiqueté qui contient deux boutons. Remarquer que l'étiquette “Important controls” interrompt la bordure. Cette figure illustre les valeurs par défauts du widget: un relief 'groove' (Voir :ref:`reliefs`) et une étique ancrée au nord ouest, ``'nw'``, c'est à dire en haut du cadre à gauche.

Pour créer un cadre étiqueté dans une fenêtre mère ou un cadre ``parent``:

.. py:class:: LabelFrame(parent, option, ...)

        Retourne le cadre étiqueté créé. Ses options sont:

        :arg bg: 
                (ou **background**) La couleur de fond appliqué à l'intérieur du widget; Voir :ref:`couleurs`.
        :arg bd:
                (ou **borderwidth**) Largeur de la bordure du cadre. Voir :ref:`dimensions`. Sa valeur par défaut est 2 pixels.
        :arg cursor: 
                Le pointeur de souris utilisé lorsque la souris est à l'intérieur du cadre; voir :ref:`pointeurs`.
        :arg fg: or foreground 
                Couleur utilisé pour l'étiquette.
        :arg height: 
                La hauteur du cadre. Ne sera pas prise en compte sauf si vous appelez la méthode ``grid_propagate(0)`` sur le cadre; voir :ref:`autres-meth-grille`.
        :arg highlightbackground: 
                Couleur de la mise en valeur du focus lorsque le cadre a perdu le focus. Voir “Focus: routing keyboard input”.
        :arg highlightcolor:
                Couleur de la ligne de focus lorsque le cadre obtient le focus.
        :arg highlightthickness: 
                Épaisseur de la zone de mise en valeur du focus.
        :arg labelanchor: 
                Utilisez cette option pour positionner l'étiquette sur le bord du cadre. Sa position par défaut est ``'nw'`` ce qui place l'étiquette en haut à gauche. Pour les neuf positions possibles:
        :arg labelwidget: 
                Instead of a text label, you can use any widget as the label by passing that widget as the value of this option. If you supply both labelwidget and text options, the text option is ignored.
        :arg padx: 
                Normalement, un cadre s'ajuste à son contenu. Pour ajouter N pixels d'espace supplémentaire horizontalement: ``padx=N``.
        :arg pady: 
                Similaire à **padx** dans la direction verticale.
        :arg relief: 
                Le relief par défaut est 'groove'. Pour d'autres valeurs, voir :ref:`reliefs`.
        :arg takefocus: 
                Normalement, un cadre n'obtient pas le focus (voir “Focus: routing keyboard input” pour une vue d'ensemble de ce sujet). Cependant, donner la valeur 1 à cette option si vous voulez que le cadre soit sensible aux saisies clavier. Pour réagir aux saisies clavier, vous aurez besoin de créer une liaison pour les événements du clavier; voir “Events” pour plus d'informations sur les événements et les liaisons.
        :arg text: 
                Text of the label.
        :arg width: 
                La largeur du cadre. Voir :ref:`dimensions`. Cette valeur est ignorée sauf si vous appelez la méthode ``grid_propagate(0)`` sur le cadre; Voir :ref:`autres-meth-grille`. 
