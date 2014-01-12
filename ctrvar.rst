.. _CTRLVARIABLES:

*******************************************************
Les variables de contrôle: Les valeurs sous les widgets
*******************************************************

Une variable de contrôle de tkinter est un objet spécial qui se comporte comme une variable ordinaire de Python en ce sens que c'est un conteneur pour une valeur comme un nombre ou une chaîne de caractères.

Tout l'intérêt des variables de contrôle, c'est qu'elles peuvent-être partagées entre plusieurs widgets, et qu'elles se souviennent de tous les widgets qui les partagent à un moment donné. En particulier, cela signifie que si votre programme mémorise une valeur ``v`` dans une variable de contrôle ``c`` en utilisant la méthode ``c.set(v)``, tous les widgets qui sont reliés à cette variable de contrôle sont automatiquement mis à jour sur l'écran.

Tkinter utilise des variables de contrôles pour réaliser de nombreuses fonctionnalités, par exemple:

* Les boîtes à cocher, *Checkbuttons*, utilisent une variable de contrôle pour mémoriser leur état courant (on ou off).

* Un groupe de boutons radio, *radiobuttons*, partage une variable de contrôle qui peut être utilisée pour connaître le bouton qui est actuellement coché. Quand l'utilisateur clique sur l'un des boutons d'un groupe, le mécanisme qui assure qu'un seul des boutons est coché à un moment donné s'appuie sur cette variable de contrôle partagée.

* Les variables de contrôles contiennent des textes pour de nombreuses applications. Normalement, le texte affiché dans un widget de saisie, *Entry*, est relié à une variable de contrôle. Il est aussi possible d'utiliser une telle variable de contrôle pour gérer les textes des étiquettes des cases à cocher, des boutons radio et le contenu des widgets étiquettes, *Label*.

  Par exemple, vous pourriez relier un widget ``Entry`` (boîte de saisie) à un widget ``Label`` (étiquette) de telle sorte que quand l'utilisateur modifie le texte du premier, le second soit automatiquement mis à jour pour montrer le même texte.

Pour obtenir une variable de contrôle, utilisez l'un de ces constructeurs, en fonction du type de valeur que vous souhaitez mémoriser::

    v = DoubleVar()   # Mémorise un flottant; sa valeur par défaut est 0.0
    v = IntVar()      # Mémorise un entier; sa valeur par défaut est 0
    v = StringVar()   # Mémorise une chaîne de caractères; sa valeur par défaut est ''

Toutes les variables de contrôle disposent de ces méthodes:

.. py:method:: get()

        Retourne la valeur courante de la variable de contrôle.

.. py:method:: set(valeur)

        Modifie la valeur courante de la variable de contrôle. Si les options d'un ou plusieurs widgets sont reliées à cette variable, ces widgets seront automatiquement mis à jour quand la boucle principale sera à nouveau en attente; voir ``.update_idletasks()`` in Section 26, “Universal widget methods” pour plus d'information sur le contrôle de ce cycle de mise à jour.

Voici quelques indications sur la façon dont les variables de contrôles sont utilisées avec certains widgets.

``Button``

    Vous pouvez renseigner son option **textvariable** avec une ``StringVar``. À chaque fois que cette variable est modifiée, le texte du bouton sera mis à jour pour afficher la nouvelle valeur. Il n'est pas nécessaire d'utiliser cela sauf si le texte du bouton doit changer au cours du temps: utilisez l'option **text** si l'étiquette du bouton ne change pas.

``Checkbutton``

    Normalement, vous relierez son option **variable** à une ``IntVar``, et cette variable aura la valeur 1 lorsque la case est cochée, la valeur 0 lorsqu'elle ne l'est pas. Cependant, vous pouvez choisir d'autres valeurs pour ces deux états en utilisant les options **onvalue** et **offvalue**.

    Vous pouvez même utiliser une ``StringVar`` comme **variable** de la case à cocher en fournissant des chaînes de caractères aux options **onvalue** et **offvalue**. Voici un exemple:
    
    ::

        spamVar = StringVar()
        spamCB  = Checkbutton(root, text='Spam?',
            variable=spamVar, onvalue='oui', offvalue='non')

    Si cette case est cochée, ``spamVar.get()`` retournera ``'oui'``; Si elle ne l'est pas, la même instruction renverra ``'non'``. De plus, votre programme peut cocher la case en appelant ``spamVar.set('oui')``.

    Vous pouvez encore indiquer une ``StringVar`` pour son option **textvariable**. Il vous suffit alors d'utiliser sa méthode ``.set()`` pour actualiser l'étiquette de cette case à cocher.

``Entry``

    Positionnez son option **textvariable** avec une ``StringVar``. Utilisez alors sa méthode ``.get()`` pour récupérer le texte actuellement affiché dans la boîte de saisie. Vous pouvez aussi modifier ce texte en utilisant sa méthode ``.set()``.
    
``Label``

    Positionnez son option **textvariable** avec une ``StringVar``. En appelant sa méthode ``.set()``, vous pourrez modifier le texte affiché sur cette étiquette. Il n'est pas nécessaire d'utiliser cela; si vous ne prévoyez pas de changer son texte, utilisez plutôt son option **text** pour renseigner son contenu.

``Menubutton``

    Si vous souhaitez être capable de modifier le texte affiché sur un bouton de menu, positionnez son option **textvariable** avec une ``StringVar`` et utilisez sa méthode ``.set()`` pour modifier le texte affiché.

``Radiobutton``

    Son option **variable** doit être réglée avec une variable de contrôle, soit une ``IntVar`` soit une ``StringVar``. Tous les boutons radios qui forment un groupe doivent alors partager cette variable de contrôle.

    Régler l'option **value** de chaque bouton radio du groupe à une valeur différente. Lorsque l'utilisateur coche un bouton, la variable mémorisera la valeur de l'option **value** de ce bouton et tous les autres boutons seront décochés.

    Vous pourriez vous demander dans quel état se trouve un groupe de boutons radio lorsque leur variable de contrôle n'a pas encore reçu de valeur et que l'utilisateur n'a pas encore coché l'un des boutons ? Chaque variable de contrôle possède une valeur par défaut: ``0`` pour une ``IntVar``, ``0.0`` pour une ``DoubleVar``, et ``''`` pour une ``StringVar``. Si l'un des boutons radio a cette valeur, il est coché initialement. Si aucun d'eux n'a cette valeur, aucun n'est coché.

    Si vous souhaitez modifier l'étiquette d'un bouton radio pendant l'exécution du programme, régler son option ``textvariable`` avec une ``StringVar``. Vous serez alors en mesure de la modifier en utilisant la méthode ``.set()`` de cette variable de contrôle.
    
``Scale``

    Pour un widget «curseur», *Scale*, positionnez son option **variable** avec une variable de contrôle du type voulu et réglez ses options ``from_`` et ``to`` aux valeurs limites qui apparaissent à chaque extrémité du widget.

    Par exemple, vous pourriez utiliser une ``IntVar`` en combinaison avec ``from_=0`` et ``to=100``. Alors, à chaque fois que l'utilisateur modifie la position du curseur, la variable de contrôle est mise à jour avec la valeur sélectionnée de l'intervalle *[0; 100]*.

    Votre programme peut aussi déplacer le curseur du widget en utilisant la méthode ``.set()`` de la variable de contrôle. Dans l'exemple précédent, l'instruction ``.set(75)`` déplacer le curseur au 3/4 de sa barre.

    Pour utiliser un widget ``Scale`` avec des valeur flottantes, utilisez une ``DoubleVar``.

    Vous pouvez utiliser une ``StringVar`` comme variable de contrôle d'un widget ``Scale``. Il sera tout de même nécessaire de préciser des valeurs numériques pour les options *from\_* et *to*, Mais les valeurs numériques du widget seront converties en une chaîne de caractères pour être mémorisées dans la ``StringVar``. Utilisez l'option **digit** du widget pour contrôler la précision avec laquelle cette conversion est réalisée.
