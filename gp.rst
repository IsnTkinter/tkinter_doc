.. _POSITIONNEMENT:

*******************************
Gestionnaires de positionnement
*******************************

Par la suite nous discuterons des composants graphiques - *widgets*, les briques de construction de la GUI de votre application. Comment organiser les widgets dans une fenêtre ?

Bien qu'il y ait différents gestionnaires de positionnement (*geometry managers*) dans tkinter, nous retiendrons plus spécialement le gestionnaire ``.grid()``.
Ce gestionnaire «découpe» chaque fenêtre ou cadre en une grille formée de lignes et de colonnes.

* Une *cellulle* (*cell*) est la zone d'intersection d'une ligne et d'une colonne.

* La largeur de chaque colonne est la largeur de la plus large cellule qu'elle contient.

* La hauteur de chaque ligne est la hauteur de la plus large ligne qu'elle contient.

* Pour les composants graphiques (*widgets*) qui n'occupent pas toute la surface de leur cellule, on peut indiquer quoi faire de l'espace restant : à l'extérieur du widget, ou en étirant celui-ci pour le combler dans la direction horizontale ou verticale.

* Il est possible de regrouper (*spanning*) plusieurs cellule en une plus large (ou plus haute).

Lorsqu'on crée un widget, il n'apparaît pas jusqu'à ce qu'il soit positionné au moyen d'un gestionnaire de positionnement.  Ainsi, construction et placement du widget se font en deux  temps::

        truc = Constructeur(parent, ...)
        truc.grid(...)


où `Constructeur` est l'une des classes de widget comme ``Button``, ``Frame``, ... et `parent` est le widget parent dans lequel le widget enfant est construit.
Tous les widgets dispose de la méthode ``.grid()`` qui s'utilise pour préciser son emplacement dans une grille.

La méthode ``.grid()``
======================

Pour afficher un widget ``w`` sur l'écran de votre application:

.. py:method:: w.grid(option=valeur, ...)

    Cette méthode enregistre le widget ``w`` dans le gestionnaire de grille.
    Si vous ne faites pas ça, votre widget existera sans pour autant apparaître à l'écran.
    Voici les options possibles:

    :arg column:
        
        Le numéro de la colonne où vous souhaitez placer votre 
        widget en partant de zéro. Sa valeur par défaut est 0.

    :arg columnspan:
    
        Normalement un widget occupe seulement une cellule. Cependant, vous pouvez regrouper plusieurs cellules d'une ligne en indiquant via **columnspan** le nombre de cellules à regrouper. Par exemple, ``w.grid(row=0, column=2, columnspan=3)`` aura pour effet de placer ``w`` dans une cellule qui s'étale sur les colonnes 2, 3 et 4 de la ligne 0.
    
    :arg in\_: 
        
        Pour enregistrer ``w`` comme enfant d'un certain widget ``w2``, utiliser ``in_=w2``.
        Le nouveau parent ``w2`` doit-être un descendant du parent utilisé pour la construction du widget ``w``.
    
    :arg ipadx:

        marge interne horizontale (en *x*). Cette dimension est ajoutée à l'intérieur du widget sur ses côtés gauche et droit.
 
    :arg ipady:
        
        marge interne verticale (en *y*). Cette dimension est ajoutée à l'intérieur du widget sur ses côtés haut et bas.
  
    :arg padx:
    
        Marge externe horizontale.
 
    :arg pady:
    
        Marge externe verticale.
 
    :arg row:
    
        Le numéro de ligne où vous souhaitez placer votre widget en partant de zéro. Sa valeur par défaut est le numéro de de la première ligne inoccupée.

    :arg rowspan:
    
        Normalement un widget occupe seulement une cellule. Cependant, vous pouvez regrouper plusieurs cellules d'une colonne en indiquant via **rowspan** le nombre de cellules à fusionner. Cette option peut-être utilisée en combinaison avec **columnspan** afin de préciser un bloc de cellules. Par exemple, ``w.grid(row=3, column=2, rowspan=4, columnspan=5)`` aura pour effet de placer ``w`` dans une zone obtenue en fusionnant 20 cellules, avec les numéros de lignes 3 - 6 et les numéros de colonnes 2 - 7.

    :arg sticky: Cette option détermine la façon de distribuer l'espace inoccupé par un widget à l'intérieur d'une cellule.
    
        * Si vous ne donnez aucune valeur à l'attribut **sticky**, le comportement par défaut est de centrer le widget dans sa cellule.
        * Vous pouvez positionner le widget dans un des coins de la cellule en indiquant ``sticky='ne'`` (nord-est: en haut à droite), ``'se'`` (en bas à droite), ``'sw'`` (en bas à gauche), ou ``'nw'`` (en haut à gauche).
        * Vous pouvez centrer le widget contre l'un des bords de la cellule en utilisant ``sticky='n'`` (centré en haut), ``'e'`` (centré à droite), `'s'` (centré en bas), ou `'w'` (centré à gauche).
        * Utilisez ``sticky='ns'`` pour l'étirer verticalement tout en le laissant centré horizontalement.
        * Utilisez ``sticky='ew'`` pour l'étirer horizontalement tout en le laissant centré verticalement.
        * Utilisez ``sticky='nesw'`` pour l'étirer dans les deux directions afin de remplir la cellule.
        * Les autres combinaisons fonctionneront aussi. Par exemple, ``sticky='nsw'`` l'étirera verticalement en le plaçant contre le bord gauche de la cellule.
        
.. _autres-meth-grille:

Autres méthodes du gestionnaire de grille
=========================================

Ces méthodes relatives au placement dans une grille sont définies sur tous les widgets ``w``:

.. py:method:: w.grid_bbox(column=None, row=None, col2=None, row2=None)

    Retourne un tuple à 4 éléments qui décrit la boîte englobante (`bounding box`) de tout ou partie de la grille associée au widget ``w``.
    Les deux premiers nombres sont les coordonnées ``x`` et ``y`` du coin supérieur gauche de la zone, et les deux autres sa largeur et sa hauteur.
    
    Si vous précisez les arguments ``column`` et ``row``, la boîte englobante retournée décrit la zone de la cellule correspondante.
    Si vous renseignez aussi les arguments ``col2`` et ``row2``, la boîte englobante retournée décrit la zone du grillage qui va de la colonne ``column`` à ``col2`` inclus et de la ligne ``row`` à ``row2`` inclus.
    
    Par exemple, ``w.grid_bbox(0, 0, 1, 1)`` retourne la boîte englobante de quatre cellules et non pas une.
    
.. py:method:: w.grid_forget()

    Cette méthode fait disparaître ``w`` de l'écran. Il existe toujours, il est simplement invisible. Vous pouvez utiliser ``.grid()`` pour le faire apparaître de nouveau, mais ses options de grille auront été oubliées.
  
.. py:method:: w.grid_info()

    Retourne un dictionnaire dont les clés sont les noms des options de grille de ``w`` avec les valeurs correspondantes de ces options.
    
.. py:method:: w.grid_location(x, y)

    Étant donné des coordonnées `(x, y)` relatives au widget conteneur, cette méthode retourne un tuple `(col, row)` qui décrit quelle cellule du système de grille de ``w`` contient ces coordonnées à l'écran.
    
.. py:method:: w.grid_propagate()

    Normalement, tous les widgets *propagent* leurs dimensions, ce qui veut dire qu'ils s'ajustent pour s'adapter à leur contenu.
    Cependant, il arrive qu'on veuille forcer un widget à être d'une certaine taille indépendamment de la taille de son contenu.
    Pour faire cela, appeler ``w.grid_propagate(0)`` où ``w`` est le widget dont vous voulez forcer la taille.
    
.. py:method:: w.grid_remove()

    Cette méthode ressemble à ``.grid_forget()``, mais les options de grille ne sont pas perdues. Ainsi, si vous appellez ``.grid()`` à nouveau, les mêmes options de grilles seront utilisées.
    
.. py:method:: w.grid_size()

    Retourne un tuple à deux éléments qui contient le nombre de colonnes et de lignes dans le système de grille de ``w``.
    
.. py:method:: w.grid_slaves(row=None, column=None)

    Retourne la liste des widgets gérés par ``w``. Si aucun argument n'est fourni, la liste est exhaustive.
    Utilisez l'argument ``row=`` pour selectionner ceux qui se trouvent dans une ligne particulière.
    De même, utilisez ``column=`` pour sélectionner ceux qui se trouvent dans une colonne particulière.

Configuration de la taille des lignes et des colonnes
=====================================================

Sauf à prendre certaines précautions, la largeur d'une colonne pour un certain widget sera égal à la largeur de sa plus large cellule et la hauteur d'une ligne sera égal à la hauteur de sa plus haute cellule. L'attribut `sticky` controle seulement son emplacement dans la cellule s'il ne la remplit pas complètement.

Si vous souhaitez controler plus finement cet ajustement automatique des colonnes et des lignes, utilisez ces méthodes sur le widget parent qui contient la grille de positionnement.

.. py:method:: w.columnconfigure(N, option=valeur, ...)

    Dans la grille du widget ``w``, configure la colonne numéro N de telle sorte que les options fournies aient les valeurs indiquées (voir plus bas). 

.. py:method:: w.rowconfigure(N, option=valeur, ...)

    Dans la grille du widget ``w``, configure la ligne numéro N de telle sorte que les options fournies aient les valeurs indiquées. 

    :arg minsize:
    
        la taille minimum de la ligne (ou colonne) en pixels. Si il n'y a rien dans la ligne (ou colonne) indiquée, elle n'apparaîtra pas, même si vous utilisez cette option.  

    :arg pad:
    
        marge en pixels à ajouter autour de la plus large cellule de la ligne (ou colonne).
    
    :arg int weight:
        
        Pour rendre une ligne (ou colonne) étirable lors d'un redimensionnement, utilisez cette option en fournissant une valeur qui donne le poid relatif de cette ligne (ou colonne) lors de la distrubution de l'espace supplémentaire.
        
        Par exemple, si un widget ``w`` contient une grille, le code qui suit attribura trois quart (3/4) de l'espace supplémentaire à la première colonne et un quart (1/4) à la seconde::
        
            w.columnconfigure(0, weight=3)
            w.columnconfigure(1, weight=1)
            
        Si cette option n'est pas utilisée, les lignes et colonnes ne seront pas étirées.


Rendre la fenêtre principable redimensionnable
==============================================

Vous souhaitez que l'utilisateur puisse redimensionner la fenêtre de l'application tout en distribuant l'espace supplémentaire entre les widgets qui la composent. Cela requiert certaines opérations qui ne sont pas évidentes.

Il est nécessaire d'utiliser les techniques de gestion de la taille des lignes et colonnes décrites dans la section précédente pour rendre votre grille étirable. Cependant, ce n'est pas suffisant.

Reprenons l'exemple de la simple application qui contenait un seul bouton.
Si vous la lancez et que vous redimensionnez la taille de la fenêtre, le bouton conserve la même taille.

Voici une version où le bouton remplit toujours tout l'espace disponible:

.. code-block:: python
    :linenos:
    :emphasize-lines: 9, 10, 16

    # Chargement du module tkinter
    from tkinter import * # pour Python2 se serait Tkinter
    
    # Construction de la fenêtre principale «root»
    root = Tk()
    root.title('Simple exemple')
    
    # Configuration du gestionnaire de grille
    root.rowconfigure(0, weight=1)
    root.columnconfigure(0, weight=1)
    
    # Construction d'un simple bouton
    qb = Button(root, text='Quitter', command=root.quit)
    
    # Placement du bouton dans «root»
    qb.grid(row=0, column=0, sticky="nsew")
    
    # Lancement de la «boucle principale»
    root.mainloop()
    
Cependant, dans la plupart des applications, les widgets sont positionnés en grille dans des cadres eux-mêmes positionnés dans la fenêtre principale.
Dans cette situation, il ne faudra pas oublier de rendre étirable la grille de la fenêtre principale ainsi que les grilles des cadres.
