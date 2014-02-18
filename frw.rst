.. _CADRES:

**********************
``Frame`` - Cadres 
**********************

Un cadre est simplement un conteneur pour d'autre widgets.

* La fenêtre principale de votre application est basiquement un cadre.

* Chaque cadre possède son propre gestionnaire de positionnement. Ainsi, la disposition des widgets dans chaque cadre est indépendante.

* Les widgets ``Frame`` (les cadres), sont de bons outils pour rendre votre application modulaire. Vous pouvez grouper un ensemble cohérent de widgets en les plaçant dans un cadre. Mieux encore, vous pouvez créer votre propre classe de cadre en la faisant hériter de ``Frame``, et en réalisant votre propre interface pour ce cadre. C'est une bonne technique pour cacher les détails des interactions des widgets d'un groupe.

Pour créer un nouveau cadre dans une fenêtre mère ou dans un cadre parent:

.. py:class:: Frame(parent, option, ...)

        Le constructeur retourne le cadre créé. Ses options sont:

        :arg bg: 
                (ou **background**) La couleur de fond du cadre. Voir :ref:`couleurs`.
        :arg bd: 
                (ou **borderwidth**) Largeur de la bordure du cadre. Par défaut, vaut 0 (aucune bordure). Pour les valeurs permises, voir :ref:`dimensions`.
        :arg cursor:
                Le pointeur de souris utilisé lorsque la souris est à l'intérieur du cadre; voir :ref:`pointeurs`.
        :arg height:
                La hauteur du cadre. Ne sera pas prise en compte sauf si vous appelez la méthode ``grid_propagate(0)`` sur le cadre; voir :ref:`autres-meth-grille`.
        :arg highlightbackground:
                Couleur de la mise en valeur du focus lorsque le cadre a perdu le focus. Voir :ref:`FOCUS`.
        :arg highlightcolor:
                Couleur de la ligne de focus lorsque le cadre obtient le focus.
        :arg highlightthickness:
                Épaisseur de la zone de mise en valeur du focus.
        :arg padx: 
                Normalement, un cadre s'ajuste à son contenu. Pour ajouter N pixels d'espace supplémentaire horizontalement: ``padx=N``.
        :arg pady: 
                Similaire à **padx** dans la direction verticale.
        :arg relief:
                Le relief par défaut d'un cadre est ``'flat'``, ce qui veut dire qu'il ne se détache pas de ce qui l'entoure. Pour avoir une bordure autour du cadre, donner l'un des styles de reliefs à cette option. Voir :ref:`reliefs`.
        :arg takefocus:
                Normalement, un cadre n'obtient pas le focus (voir :ref:`FOCUS` pour une vue d'ensemble de ce sujet). Cependant, donner la valeur 1 à cette option si vous voulez que le cadre soit sensible aux saisies clavier. Pour réagir aux saisies clavier, vous aurez besoin de créer une liaison pour les événements du clavier; voir :ref:`EVENTS` pour plus d'informations sur les événements et les liaisons.
        :arg width:
                La largeur du cadre. Voir :ref:`dimensions`. Cette valeur est ignorée sauf si vous appelez la méthode ``grid_propagate(0)`` sur le cadre; Voir :ref:`autres-meth-grille`. 
