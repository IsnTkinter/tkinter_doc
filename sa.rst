.. _STDATTR:

***********************
Les attributs standards
***********************

Avant d'examiner les widgets disponibles, prenons le temps d'observer comment certains
de leurs attributs communs - comme les tailles, les couleurs et les polices de caractères (fontes) - sont
précisés.

* Chaque widget possède un ensemble d'`options` qui affectent son apparence et son comportement - des attributs comme les fontes, les couleurs, les tailles, les étiquettes textuelles, etc.

* Vous pouvez préciser les options lors de l'appel du constructeur du widget en utilisant des mots clés comme ``text='PANIQUE'`` ou ``height=20``.

* Après avoir créé un widget, il est encore possible de modifier chacune de ses options en utilisant sa méthode :py:meth:`config`. Vous pouvez aussi récupérer la valeur courante de n'importe laquelle de ses options en utilisant sa méthode :py:meth:`cget`. Voir :ref:`UNIVERSAL` pour en apprendre plus sur ces méthodes.

.. _dimensions:

Les dimensions
==============

Les différentes dimensions comme la largeur, la hauteur, etc. peuvent être précisées dans différentes unités.

* Si vous indiquez une dimension par un entier, elle est supposée être en pixels.
* Vous pouvez préciser une unité en utilisant une chaîne de caractères qui contient un nombre suivi d'une unité :
      
    * ``c`` : Centimètres
    * ``i`` : Pousses (`Inches`)
    * ``m`` : Millimètres 
    * ``p`` : Points d'impression

  
.. _systeme:

Le système de coordonnées
=========================

Comme dans la plupart des systèmes d'affichage, l'origine de chaque système de coordonnées est
située à son coin supérieur gauche, les valeurs de `x` augmentant vers la droite et
les valeurs de `y` augmentant vers le bas.

.. image:: img/coords.png 
        :align: center
L'unité de base est le pixel avec le coin supérieur gauche de coordonnées `(0,0)`.
Les coordonnées indiquées par un entier sont toujours exprimées en pixels, mais chaque coordonnée
peut être indiquée via une chaîne de caractères dans une unité particulière; voir :ref:`dimensions`.

.. _couleurs:

Les couleurs
============

Il y a deux manières générales pour indiquer une couleur dans tkinter.

* Vous pouvez utiliser une chaîne de caractères qui précise la proportion de rouge (`red`), vert (`green`) et bleu (`blue`) en hexadécimal:

    * ``#rgb`` : quatre bits par couleur
    * ``#rrggbb`` : huit bits par couleur
    * ``#rrrgggbbb``: douze bits par couleur
    
    Par exemple, ``#fff`` est blanc, ``#000000`` est noir, ``#000fff000`` est un vert pur et   ``#00ffff`` est un cyan pur (vert plus bleu).

* Vous pouvez aussi utiliser n'importe quelle couleur définie localement par son nom standard. Les couleurs ``'white'``, ``'black'``, ``'red'``, ``'green'``, ``'blue'``, ``'cyan'``, ``'yellow'``, and ``'magenta'`` seront toujours disponibles. D'autres noms peuvent fonctionner selon la configuration de votre ordinateur.


.. _polices:

Les polices de caractères
=========================

Selon votre système d'exploitation, il peut y avoir jusqu'à trois façons d'indiquer un type de fonte.

* Comme un tuple dont le premier élément est la famille de la fonte, suivi par une taille (en point si positif, en pixel si négatif), optionnellement suivi par une chaîne contenant un (ou plusieurs) modificateur de style ``bold``, ``italic``, ``underline`` et ``overstrike``.

    Exemples :  ``('Helvetica', '16')`` pour une police Helvetica régulière de 16 points; ``('Times', '24', 'bold italic')`` pour une police Times de 16 points en gras italique; Pour une police Times en gras de 20 pixels, utilisez ``('Times', -20, 'bold')``.

* Vous pouvez créer un «objet fonte» en important le sous-module ``tkinter.font`` et en utilisant le constructeur ``Font``:

    .. code-block:: python

        import tkinter.font as tkFont # ou «import TkFont» pour python 2
    
        #....
        font = tkFont.Font(option, ...)


    où les options sont :

    * ``family`` : la famille de fonte via une chaîne de caractères.
    * ``size`` : la taille de fonte en points via un entier. Pour obtenir une taille de `n` pixels, utiliser ``-n``.
    * ``weight`` : 'bold' pour gras, 'normal' pour un rendu normal.
    * ``slant`` : 'italic' pour italique, 'roman' pour un rendu normal.
    * ``underline`` : 1 pour le soulignement, 0 pour un rendu normal.
    * ``overstrike`` : 1 pour barrer, 0 pour un rendu normal.
    
    Par exemple, pour obtenir une fonte Helvetica de 36 points en gras italique::
    
     helv36 = tkFont.Font(family='Helvetica', size=36, weight='bold')

* Si vous utilisez le système X Window, vous pouvez utiliser n'importe quel nom de fonte X. Par exemple, la fonte nommée ``'-*-lucidatypewriter-medium-r-*-*-*-140-*-*-*-*-*-*'`` est une bonne fonte à chasse fixe pour l'affichage à l'écran. Utilisez le programme `xfontsel` pour vous aider à choisir une fonte plaisante.

Pour obtenir la liste de toutes les familles de polices disponibles dans votre environnement, appelez cette fonction::

    tkFont.families()
    
La valeur de retour est une liste de chaînes. Note : il est nécessaire de créer votre fenêtre principale avant d'appeler cette fonction.

Les méthodes qui suivent sont disponibles pour n'importe quel objet de type Font.

.. py:method:: Font.actual(option=None)
    
    Si vous ne fournissez aucun argument, vous obtenez un dictionnaire des options courantes de la fonte qui peuvent être différentes de celles que vous avez demandées. Pour obtenir la valeur actuelle d'une option, fournissez son nom comme argument.
    
.. py:method:: Font.cget(option)

    Retourne la valeur de l'option indiquée sous la forme d'une chaîne de caractères.
    
.. py:method:: Font.configure(option, ...)

    Utilisez cette méthode pour modifier une ou plusieurs options d'une fonte. Par exemple, si vous disposez d'un objet Font nommé ``titres`` et que vous appelez titres.configure(family='times', size=18), cette fonte sera modifiée conformément ainsi que tout widget qui l'utilise.
    
.. py:method:: Font.copy()

    Retourne une copie de l'objet Font appelant.

.. py:method:: Font.measure(text)

    Passez à cette méthode une chaîne de caractères et elle vous retournera le nombre de pixels en largeur que cette chaine occuperait avec la fonte appelante. Attention: certains caractères penchés peuvent déborder cette zone.
    
.. py:method:: Font.metrics(option)

    Si vous appelez cette méthode sans argument, elle retourne un dictionnaire qui contient toutes les métriques de la fonte. Vous pouvez récupérer la valeur d'une métrique particulière en la fournissant en argument.
    
    :arg ascent: Nombre de pixels en hauteur entre la ligne de base et le point haut du plus haut caractère.
    :arg descent: Nombre de pixels en hauteur entre la ligne de base et le point bas du plus bas caractère.
    :arg fixed: Cette valeur est nulle pour une fonte à largeur variable et vaut 1 pour une police à chasse fixe.
    :arg linespace: Nombre de pixels de la hauteur totale. This is the leading of type set solid in the given font.

.. _ancrage:

Le système d'ancrage
=====================

Le module Tkinter définit un certain nombre de constantes d'ancrage que vous pouvez utiliser pour contrôler l'endroit où un widget est positionné relativement à son contexte.
Par exemple, les ancrages peuvent préciser l'endroit où un widget est situé à l'intérieur d'un cadre (`Frame`) lorsque celui-ci est plus grand que le widget.

Ces constantes sont données comme sur une boussole où le nord est en haut et l'ouest à gauche. Nous prions les lecteurs de l'hémisphère sud de nous pardonner ce chauvinisme du nord.

Les constantes d'ancrages sont montrées ci-dessous:

.. image:: img/anchors.png
        :align: center

Par exemple, si vous créez un petit widget dans un large cadre et utilisez l'option ``anchor='se'``, le widget sera placé au niveau du bord inférieur droit du cadre. Si vous utilisez
``anchor='n'``, il sera centré sur le bord haut du cadre.

Les ancres sont aussi utilisées pour préciser où positionner un texte relativement à un point de référence. Par exemple, si on utilise ``'center'`` comme une ancre pour un texte, il est centré horizontalement et verticalement autour du point de référence. L'ancre ``'nw'`` le positionnerait de telle sorte que le point de référence coïncide avec le coin nord ouest de la boîte qui contient le texte. L'ancre ``'w'`` le centrerait verticalement avec le bord gauche de la boîte du texte sur le point et ainsi de suite.

.. _reliefs:

Les styles de relief
=====================

Le style de relief d'un widget se réfère à la simulation de certains effets 3D autour de l'extérieur du widget. Voici les différentes possibilités :

.. image:: img/relief.png
        :align: center

Les valeurs peuvent être précisées par des chaînes de caractères comme ``'raised'``, ``'sunken'``, ``'flat'`` ...

La largeur des bords dépend de l'option **borderwidth** du widget. Ici, cette largeur a été fixée à 5 pixels alors que par défaut elle vaut 2 pixels.

.. _bitmaps:

Les bitmaps
===========

Pour les options ``bitmap`` des widgets, les bitmaps représentés ci-dessous sont toujours disponibles :

.. image:: img/stdbitmaps.png
        :align: center

L'image montre des widget boutons qui portent les bitmaps standards.

De la gauche vers la droite, il y a ``'error'``, ``'gray75'``, ``'gray50'``, ``'gray25'``, ``'gray12'``, ``'hourglass'``, ``'info'``, ``'questhead'``, ``'question'``, et ``'warning'``. 

Vous pouvez utiliser vos propres bitmaps. N'importe quel fichier d'extension `.xbm` de format «X bit map» fonctionnera. À la place du nom standard des bitmaps, utilisez une chaîne ``'@'`` suivi du chemin du fichier `.xbm`.

.. _pointeurs:

Le pointeur de la souris
========================

Il y a un grand nombre de pointeurs de souris disponibles. Leurs noms et le graphique associé sont indiqués ci-dessous. Le dessin exact peut varier d'un système à l'autre.

``arrow`` |arrow| ; ``man`` |man| ; ``based_arrow_down`` |based_arrow_down| ; ``middlebutton`` |middlebutton| ;
``based_arrow_up`` |based_arrow_up| ; ``mouse`` |mouse| ; ``boat`` |boat| ; ``pencil`` |pencil| ;
``bogosity`` |bogosity| ; ``pirate`` |pirate| ; ``bottom_left_corner`` |bottom_left_corner| ; ``plus`` |plus| ;
``bottom_right_corner`` |bottom_right_corner| ; ``question_arrow`` |question_arrow| ; ``bottom_side`` |bottom_side| ; ``right_ptr`` |right_ptr| ;
``bottom_tee`` |bottom_tee| ; ``right_side`` |right_side| ; ``box_spiral`` |box_spiral| ; ``right_tee`` |right_tee| ;
``center_ptr`` |center_ptr| ; ``rightbutton`` |rightbutton| ; ``circle`` |circle| ; ``rtl_logo`` |rtl_logo| ;
``clock`` |clock| ; ``sailboat`` |sailboat| ; ``coffee_mug`` |coffee_mug| ; ``sb_down_arrow`` |sb_down_arrow| ;
``cross`` |cross| ; ``sb_h_double_arrow`` |sb_h_double_arrow| ; ``cross_reverse`` |cross_reverse| ; ``sb_left_arrow`` |sb_left_arrow| ;
``crosshair`` |crosshair|; ``sb_right_arrow`` |sb_right_arrow|; ``diamond_cross`` |diamond_cross|; ``sb_up_arrow`` |sb_up_arrow|;
``dot`` |dot| ; ``sb_v_double_arrow`` |sb_v_double_arrow| ; ``dotbox`` |dotbox| ; ``shuttle`` |shuttle| ;
``double_arrow`` |double_arrow| ; ``sizing`` |sizing| ; ``draft_large`` |draft_large| ; ``spider`` |spider| ;
``draft_small`` |draft_small| ; ``spraycan`` |spraycan| ; ``draped_box`` |draped_box| ; ``star`` |star| ;
``exchange`` |exchange| ; ``target`` |target| ; ``fleur`` |fleur| ; ``tcross`` |tcross| ;
``gobbler`` |gobbler| ; ``top_left_arrow`` |top_left_arrow| ; ``gumby`` |gumby| ; ``top_left_corner`` |top_left_corner| ;
``hand1`` |hand1| ; ``top_right_corner`` |top_right_corner| ; ``hand2`` |hand2| ; ``top_side`` |top_side| ;
``heart`` |heart| ; ``top_tee`` |top_tee| ; ``icon`` |icon| ; ``trek`` |trek| ;
``iron_cross`` |iron_cross| ; ``ul_angle`` |ul_angle| ; ``left_ptr`` |left_ptr| ; ``umbrella`` |umbrella| ;
``left_side`` |left_side| ; ``ur_angle`` |ur_angle| ; ``left_tee`` |left_tee| ; ``watch`` |watch| ;
``leftbutton`` |leftbutton| ; ``xterm`` |xterm| ; ``ll_angle`` |ll_angle| ; ``X_cursor`` |X_cursor| ;
``lr_angle`` |lr_angle|


.. |arrow| image:: img/cursors/2.png
.. |man| image:: img/cursors/41.png
.. |based_arrow_down| image:: img/cursors/3.png
.. |middlebutton| image:: img/cursors/42.png
.. |based_arrow_up| image:: img/cursors/4.png
.. |mouse| image:: img/cursors/43.png
.. |boat| image:: img/cursors/5.png
.. |pencil| image:: img/cursors/44.png
.. |bogosity| image:: img/cursors/6.png
.. |pirate| image:: img/cursors/45.png
.. |bottom_left_corner| image:: img/cursors/7.png
.. |plus| image:: img/cursors/46.png
.. |bottom_right_corner| image:: img/cursors/8.png
.. |question_arrow| image:: img/cursors/47.png
.. |bottom_side| image:: img/cursors/9.png
.. |right_ptr| image:: img/cursors/48.png
.. |bottom_tee| image:: img/cursors/10.png
.. |right_side| image:: img/cursors/49.png
.. |box_spiral| image:: img/cursors/11.png
.. |right_tee| image:: img/cursors/50.png
.. |center_ptr| image:: img/cursors/12.png
.. |rightbutton| image:: img/cursors/51.png
.. |circle| image:: img/cursors/13.png
.. |rtl_logo| image:: img/cursors/52.png
.. |clock| image:: img/cursors/14.png
.. |sailboat| image:: img/cursors/53.png
.. |coffee_mug| image:: img/cursors/15.png
.. |sb_down_arrow| image:: img/cursors/54.png
.. |cross| image:: img/cursors/16.png
.. |sb_h_double_arrow| image:: img/cursors/55.png
.. |cross_reverse| image:: img/cursors/17.png
.. |sb_left_arrow| image:: img/cursors/56.png
.. |crosshair| image:: img/cursors/18.png
.. |sb_right_arrow| image:: img/cursors/57.png
.. |diamond_cross| image:: img/cursors/19.png
.. |sb_up_arrow| image:: img/cursors/58.png
.. |dot| image:: img/cursors/20.png
.. |sb_v_double_arrow| image:: img/cursors/59.png
.. |dotbox| image:: img/cursors/21.png
.. |shuttle| image:: img/cursors/60.png
.. |double_arrow| image:: img/cursors/22.png
.. |sizing| image:: img/cursors/61.png
.. |draft_large| image:: img/cursors/23.png
.. |spider| image:: img/cursors/62.png
.. |draft_small| image:: img/cursors/24.png
.. |spraycan| image:: img/cursors/63.png
.. |draped_box| image:: img/cursors/25.png
.. |star| image:: img/cursors/64.png
.. |exchange| image:: img/cursors/26.png
.. |target| image:: img/cursors/65.png
.. |fleur| image:: img/cursors/27.png
.. |tcross| image:: img/cursors/66.png
.. |gobbler| image:: img/cursors/28.png
.. |top_left_arrow| image:: img/cursors/67.png
.. |gumby| image:: img/cursors/29.png
.. |top_left_corner| image:: img/cursors/68.png
.. |hand1| image:: img/cursors/30.png
.. |top_right_corner| image:: img/cursors/69.png
.. |hand2| image:: img/cursors/31.png
.. |top_side| image:: img/cursors/70.png
.. |heart| image:: img/cursors/32.png
.. |top_tee| image:: img/cursors/71.png
.. |icon| image:: img/cursors/33.png
.. |trek| image:: img/cursors/72.png
.. |iron_cross| image:: img/cursors/34.png
.. |ul_angle| image:: img/cursors/73.png
.. |left_ptr| image:: img/cursors/35.png
.. |umbrella| image:: img/cursors/74.png
.. |left_side| image:: img/cursors/36.png
.. |ur_angle| image:: img/cursors/75.png
.. |left_tee| image:: img/cursors/37.png
.. |watch| image:: img/cursors/76.png
.. |leftbutton| image:: img/cursors/38.png
.. |xterm| image:: img/cursors/77.png
.. |ll_angle| image:: img/cursors/39.png
.. |X_cursor| image:: img/cursors/1.png
.. |lr_angle| image:: img/cursors/40.png


.. _images:

Les images
==========

Il y a trois méthodes générales pour afficher des images dans votre application tkinter.

* Pour afficher une image bitmap dans le format `.xbm`, voir :ref:`bimage`.

* Pour afficher des images dans le format `.gif`, `.pgm` ou `.ppm`, voir :ref:`photoimage`.

* La libraire d'images de Python (PIL) offre un support pour une plus grande variété de format. Sa classe ``ImageTk`` a été spécialement conçue pour afficher des images dans les applications tkinter.

.. _bimage:

La classe ``BitmapImage``
-------------------------

Pour afficher un bitmap dans le format `.xbm` vous aurez besoin de ce constructeur::

    BitmapImage(file=f, background=b, foreground=c)

où *f* est le nom du fichier image `.xbm`.

Normalement, le bit d'avant plan ``foreground`` (1) est affiché en noir et le le bit d'arrière-plan ``background`` (0) sera transparent. Pour modifier ce comportement, utilisez l'option ``background=b`` pour régler la couleur à ``b``, et l'option ``foreground=c`` pour régler la couleur à ``c``. Pour les spécifications de couleurs, :ref:`couleurs`. 

Ce constructeur retourne une valeur qui peut être utilisée à n'importe quel endroit où tkinter attend une image. Par exemple, pour afficher une image comme une étiquette, utiliser un widget ``Label`` (voir :ref:`LABEL`) et fournissez l'objet ``BitmapImage`` comme valeur à son option ``image``::

    logo = BitmapImage('logo.xbm', foreground='red')
    Label(image=logo).grid()
    
.. _photoimage:

La classe ``PhotoImage``
------------------------

Pour afficher une image du type `.gif`, `.pgm` ou `.ppm`, vous aurez besoin du constructeur::

    PhotoImage(file=f)

où *f* est le nom d'un fichier image. Le constructeur retourne une valeur qui peut être utilisée partout où tkinter attend une image.

.. _geometrie:

Les chaînes de géométrie
========================

Une chaîne de géométrie est un moyen standard de décrire à la fois la taille et la localisation d'une fenêtre principale sur l'écran du bureau.

Une chaîne de géométrie a la forme générale::

    'wxh±x±y'
    
où :

* ``w`` et ``h`` désignent respectivement la largeur (*width*) et la hauteur (*height*) de la fenêtre en pixels. Ils sont séparés par le caractère ``'x'``.

* Si la prochaine partie a la forme ``+x``, elle indique que le bord gauche de la fenêtre doit être situé à ``x`` pixels du côté gauche du bureau. Si elle a la forme ``-x``, elle indique que le bord droit de la fenêtre doit être situé à ``x`` pixels du côté droit du bureau.

* Si la prochaine partie est de la forme ``+y``, elle indique que le bord haut de la fenêtre est situé à ``y`` pixels du bord haut du bureau. Si elle a la forme ``-y``, elle indique que le bord bas de la fenêtre est situé à ``y`` pixels du bord bas du bureau.

Par exemple, une fenêtre crée avec ``geometry='120x50-0+20'`` aura une largeur de 120 pixels, une hauteur de 50 pixels, son bord droit sera collé à celui du bureau à 20 pixels du haut de celui-ci.

.. _nomfen:

Le nommage des Fenêtres (`Window`)
==================================

Le terme fenêtre (`window`) se rapporte à une zone rectangulaire du bureau.

* Une fenêtre primaire (`top-level` ou `root widow`) est une fenêtre qui a une existence indépendante pour le gestionnaire de fenêtre du système d'exploitation utilisé. Elle est décorée avec les motifs et boutons habituels du système et peut être déplacée et redimensionnée. Votre application peut utiliser n'importe quel nombre de fenêtre racine.
    
* Le terme fenêtre s'applique aussi à n'importe quel widget qui fait partie d'une fenêtre primaire. 
    
tkinter nomme toutes ces fenêtres en utilisant un nommage «hiérarchique» :

* La fenêtre principale est nommée ``'.'``
    
* Une fenêtre enfant aura un nom de la forme ``'.n'``, où ``n`` est un entier sous la forme d'une chaîne. Par exemple, une fenêtre nommée ``'.135932060'`` est un enfant de la fenêtre racine (``'.'``).
    
* Les fenêtres enfants des fenêtres enfants auront des noms de la forme ``'.p.n'`` où ``p`` est le nom de la fenêtre parente et ``n`` est un certain entier. Par exemple, une fenêtre nommée ``'.135932060.137304468'`` a une fenêtre parent ``'.135932060'``, c'est donc un petit enfant de la fenêtre principale. 
    
* Le nom relatif d'une fenêtre est la partie qui suit le dernier ``'.'`` dans le nom complet. En poursuivant l'exemple précédent, la fenêtre petit enfant a pour nom relatif ``'137304468'``.
    
Pour obtenir le nom d'un widget ``w``, utilisez ``str(w)``.

Voir aussi :ref:`UNIVERSAL` pour les méthodes que vous pouvez utiliser afin d'agir sur les noms de fenêtre, plus spécialement les méthodes  :py:meth:`winfo_name`, :py:meth:`winfo_parent`, et :py:meth:`winfo_pathname`.

.. _style-extr:

Style des extrémités (`cap`) et des jointures (`join`)
======================================================

Pour obtenir des dessins plaisants, il est parfois bon de s'intéresser au style des extrémités et des jointures.

    * le style des extrémités (`cap style`) d'une ligne permet de contrôler la forme de ses terminaisons. Les styles possibles sont :
        
        * ``'butt'`` : la fin d'une ligne est coupée perpendiculairement par une ligne qui passe par le point final.
                
        * ``'projecting'`` : La fin d'une ligne est coupée perpendiculairement par une ligne qui dépasse le point final de la moitié de la largeur de la ligne.
        
        * ``'round'`` : la fin est réalisée avec un demi-cercle centré sur le point final.
        
    * Le style de jointure (`join style`) décrit la forme que prend le lieu où deux lignes se rejoignent:
    
        * ``'rond'`` : la jointure est réalisée avec un cercle centré au point de jointure.
        
        * ``'bevel'`` : Une ligne droite est dessinée avec un angle intermédiaire entre les angles des lignes adjacentes.
        
        * ``'mitter'`` : Les côtés des lignes adjacentes sont poursuivies jusqu'à ce qu'elles se rencontrent en un point.
        
La figure suivante illustre ces styles. Les points rouges montrent la localisation des points qui définissent les lignes.

.. image:: img/cap-join.png
        :align: center

.. _Motifs-brise:

Motifs brisés (`dash patterns`)
===============================

Bon nombre de widgets vous permettent d'indiquer un motif brisé pour dessiner leur ligne de contour (`outline`). Les options **dash** et **dashoffset** vous donnent un contrôle fin sur le motif exact qui sera dessiné.

**dash**

    Cette option est renseignée avec un tuple d'entiers. Le premier entier précise combien de pixels doivent être tracés. Le second précise combien de pixels doivent être «sautés» avant de recommencer le tracé et ainsi de suite. Lorsque tous les entiers du tuple ont été utilisés, ils sont réutilisés dans le même ordre jusqu'à ce que la bordure soit complète.
    
    Par exemple, l'option ``dash=(3, 5)`` produit une ligne où le parties tracées font 3 pixels et où les parties vides en font 5. ``dash=(7, 1, 1, 1)`` produirait un motif de base où les partie tracées mesureraient 7 puis 1 pixels séparés par des parties vides de 1 pixel. ``dash=(5,)`` produirait une alternance 5 pixels tracés, 5 pixels vides.
  
**dashoffset**

    Pour démarrer le motif brisé en un point différent du cycle c'est à dire qui ne soit pas le point de départ, utiliser une option ``dashoffset=n`` où `n` est un nombre de pixels à sauter avant le démarrage du motif.
    
    Par exemple, ``dash=(5, 1, 2, 1)`` en combinaison avec ``dashoffset=3`` produirait: tracé 2, vide 1, tracé 2, vide 1 puis ensuite, tracé 5, vide 1, tracé 2, vide 1 et ainsi de suite :
    
.. image:: img/dashpat.png
        :align: center

.. _nuagepts:

Ajuster des motifs en nuage de points
=====================================

À faire ...
