.. _LABELFRAME:

*************************************
``LabelFrame`` - Cadres étiquetés 
*************************************

Le widget «cadre étiqueté», ``LabelFrame``, comme le widget ``Frame``, est avant tout un conteneur. Il se présente comme une zone rectangulaire dans laquelle il est possible de mettre d'autres widgets. Cependant, contrairemet au cadre ``Frame``, il vous permet d'afficher une étiquette sur sa bordure.

Voici un exemple de cadre étiqueté qui contient deux boutons. Remarquez que l'étiquette “Important controls” interrompt la bordure. Cette figure illustre les valeurs par défaut du widget: un relief 'groove' (Voir :ref:`reliefs`) et une étiquette ancrée au nord ouest, ``'nw'``, c'est à dire en haut à gauche du cadre. 

.. image:: img/labelframe.png

Pour créer un cadre étiqueté dans une fenêtre mère ou un cadre ``parent``:

.. py:class:: LabelFrame(parent, option, ...)

        Retourne le cadre étiqueté créé. Ses options sont:

        :arg bg: 
                (ou **background**) La couleur de fond appliquée à l'intérieur du widget; Voir :ref:`couleurs`.
        :arg bd:
                (ou **borderwidth**) Largeur de la bordure du cadre. Voir :ref:`dimensions`. Sa valeur par défaut est 2 pixels.
        :arg cursor: 
                Le pointeur de souris utilisé lorsque la souris est à l'intérieur du cadre; voir :ref:`pointeurs`.
        :arg fg:
                (ou **foreground**) Couleur utilisée pour l'étiquette.
        :arg height: 
                La hauteur du cadre. Ne sera pas prise en compte sauf si vous appelez la méthode ``grid_propagate(0)`` sur le cadre; voir :ref:`autres-meth-grille`.
        :arg highlightbackground: 
                Couleur de la mise en valeur du focus lorsque le cadre ne l'a plus. Voir :ref:`FOCUS`.
        :arg highlightcolor:
                Couleur de la ligne de focus lorsque le cadre obtient le focus.
        :arg highlightthickness: 
                Épaisseur de la zone de mise en valeur du focus.
        :arg labelanchor: 
                Utilisez cette option pour positionner l'étiquette sur le bord du cadre. Sa position par défaut est ``'nw'`` ce qui place l'étiquette en haut à gauche. Pour les douze positions possibles:
                
                .. image:: img/labelanchor.png

        :arg labelwidget: 
                À la place d'un label texte, vous pouvez utiliser n'importe quel widget comme label en le passant à cette option. Si vous précisez à la fois un tel widget et un étiquette texte, cette dernière est ignorée.
        :arg padx: 
                Normalement, un cadre s'ajuste à son contenu. Pour ajouter N pixels d'espace supplémentaire horizontalement: ``padx=N``.
        :arg pady: 
                Similaire à **padx** dans la direction verticale.
        :arg relief: 
                Le relief par défaut est 'groove'. Pour d'autres valeurs, voir :ref:`reliefs`.
        :arg takefocus: 
                Normalement, un cadre n'obtient pas le focus (voir :ref:`FOCUS` pour une vue d'ensemble de ce sujet). Cependant, donner la valeur 1 à cette option si vous voulez que le cadre soit sensible aux saisies clavier. Pour réagir aux saisies clavier, vous aurez besoin de créer une liaison pour les événements du clavier; voir :ref:`EVENTS` pour plus d'informations sur les événements et les liaisons.
        :arg text: 
                Le texte de l'étiquette.
        :arg width: 
                La largeur du cadre. Voir :ref:`dimensions`. Cette valeur est ignorée sauf si vous appelez la méthode ``grid_propagate(0)`` sur le cadre; Voir :ref:`autres-meth-grille`. 
