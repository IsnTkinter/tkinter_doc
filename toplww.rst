.. _TOPLEVEL:

**********************************
``Toplevel``: fenêtres primaires
**********************************

Une fenêtre primaire - *Toplevel window* - est une fenêtre qui possède une existence indépendante pour le gestionnaire de fenêtre du système d'exploitation. Une telle fenêtre possède tous les boutons ordinaires (fermeture, réduction/agrandissement) et elle peut être déplacée et redimensionnée à la souris. Votre application peut utiliser autant de fenêtres «primaires» que souhaité.

Étant donné un widget w, vous pouvez récupérer la fenêtre primaire qui le contient en utilisant ``w.winfo_toplevel()``.

Pour créer une nouvelle fenêtre primaire:

.. py:class:: Toplevel(option, ...)

        Ses options incluent:

        :arg bg: 
                 (ou *background*) La couleur d'arrière plan de la fenêtre. Voir :ref:`couleurs`.
        :arg bd: 
                 (ou *borderwidth*) La largeur de sa bordure en pixels; 0 par défaut. Pour des valeurs possibles, voir :ref:`dimensions`. Voir aussi l'option **relief** ci-dessous.
        :arg class\_: 
                Vous pouvez donner à une fenêtre primaire un nom de classe. De tels noms peuvent être alors utilisés dans la base de données des options afin de récupérer les préférences de configuration des utilisateurs (comme les couleur). Par exemple, vous pourriez concevoir une série de fenêtre surgissantes (*pop-ups*) appelées "hurlantes", et toutes les configurer avec l'option ``class_='Screamer'``. Ensuite, vous pourriez mettre la ligne suivante dans votre base de données des options::

                      *Screamer*background: red

                et enfin, utiliser la méthode ``option_readfile()`` pour lire cette base de données. Cela aurait pour effet de configurer la couleur de fond par défaut de tout les widgets ayant ce nom de classe avec la couleur rouge. Cette option est nommée ``class_`` parce que *class* est un mot clé de Python.
        :arg cursor: 
                Le pointeur de la souris utilisée lorsqu' elle survole cette fenêtre. Voir :ref:`pointeurs`.
        :arg height: 
                La hauteur de la fenêtre; voir :ref:`dimensions`.
        :arg highlightbackground:
                La couleur de ligne de mise en valeur du focus lorsque la fenêtre ne l'a pas. Voir :ref:`FOCUS`.
        :arg highlightcolor: 
                La couleur de ligne de mise en valeur du focus lorsque la fenêtre l'obtient.
        :arg highlightthickness: 
                L'épaisseur de la ligne de mise en valeur du focus. 1 par défaut. Pour supprimer la mise en évidence du focus, mettre cette option à 0.
        :arg menu:
                Pour incorporer une barre des menus principaux, configurez cette option avec un widget Menu. Sous MacOS, ce menu apparaîtra tout en haut de l'écran lorsque la fenêtre est active. Sous Window ou Unix, il apparaîtra en haut de la fenêtre.
        :arg padx:
                Utilisez cette option pour ajouter une marge horizontale à gauche et à droite de la fenêtre. La valeur est un nombre de pixels.
        :arg pady:
                Utilisez cette option pour ajouter une marge verticale en haut et en base de la fenêtre. La valeur est un nombre de pixels.
        :arg relief: 
                Normalement, une fenêtre primaire n'a pas de bordure 3d. Pour obtenir une telle bordure, réglez l'option **bd** avec une valeur supérieure à 0 et celle-ci avec l'une des valeurs possible pour le relief (voir :ref:`reliefs`).
        :arg takefocus:
                Normalement, une fenêtre primaire n'obtient pas le focus. Utilisez ``takefocus=True`` si vous souhaitez qu'elle puisse l'obtenir; voir :ref:`FOCUS`.
        :arg width: 
                La largeur de la fenêtre. Voir :ref:`dimensions`.

        Les méthodes des fenêtres primaires sont:

        .. py:method:: aspect(nmin, dmin, nmax, dmax)

                    Sert à contraindre le rapport largeur sur hauteur de la fenêtre dans l'intervalle [ *nmin* / *dmin*, *nmax* / *dmax* ]. 

        .. py:method:: deiconify()

                    Si la fenêtre a été réduite en une icone, cette méthode la ramène à l'écran.

        .. py:method:: geometry(newGeometry=None)

                    Sert à régler la géométrie de la fenêtre. Pour la forme de son argument, voir :ref:`geometrie`. Si l'argument est omis, elle retourne la chaîne qui décrit sa géométrie courante.

        .. py:method:: iconify()

                    Réduit la fenêtre en une icone.

        .. py:method:: lift(aboveThis=None)

                    Pour élever cette fenêtre tout en haut de la pile ordonnée des fenêtre que gère le gestionnaire de fenêtres du système, utilisez cette méthode sans argument. Vous pouvez aussi élever cette fenêtre juste au-dessus d'une autre fenêtre en précisant cette dernière comme argument.

        .. py:method:: lower(belowThis=None)

                    Sans aucun argument, la fenêtre est déplacée tout en bas de la pile ordonnée des fenêtres que gère le gestionnaire de fenêtre du sytème. Vous pouvez aussi la déplacer juste en dessous d'une autre en précisant cette dernière comme argument.

        .. py:method:: maxsize(largeur=None, hauteur=None)

                    Sert à régler la taille maximale de la fenêtre. Si les arguments sont omis, elle retourne les valeurs courantes (largeur, hauteur). 

        .. py:method:: minsize(width=None, height=None)

                    Sert à régler la taille minimale de la fenêtre. Si les arguments sont omis, elle retourne les valeurs courantes sous la forme d'un tuple à deux éléments.

        .. py:method:: overrideredirect(flag=None)

                    Lorsque cette méthode est appelée avec la valeur True, elle positionne le drapeau *override redirect*, lequel supprime toutes les décorations de la fenêtres de telle sorte qu'elle ne puisse plus être déplacée, redimensionnée ou iconifiée ou fermée. Si elle est appelée avec la valeur False, elle retrouve son aspect normal ainsi que tous ses comportements. Si elle est appelée sans argument, elle retourne le drapeau *override redirect* actuellement utilisée.

                    Faites attention à appeler la méthode :py:meth:`~update_idletasks` (voir :ref:`UNIVERSAL`) avant de positionner ce drapeau. Si vous l'appeler avant d'être entré dans la boucle primaire, votre fenêtre sera désactivée avant même qu'elle ne puisse apparaître.

                    Cette méthode peut ne pas fonctionner sur certain système Unix et MacOS.

        .. py:method:: resizable(largeur=None, hauteur=None)

                    Si *largeur* est True, la fenêtre peut être agrandi horizontalement. Si hauteur est True, elle peut être agrandie verticalement. Si les arguments sont omis, cette méthode retourne la taille actuelle de la fenêtre sous la forme d'un tuple a 2 éléments.

        .. py:method:: state(newstate=None)

                    Retourne l'état actuel de la fenêtre, lequel peut être:

                    * ``'normal'``: S'affiche normalement.

                    * ``'iconic'``: A été réduite en icone.

                    * ``'withdrawn'``: Est cachée.

                    Pour modifier cet état, utiliser l'une des chaînes ci-dessus comme argument. Par exemple, pour iconifier une fenêtre primaire T, utilisez ``T.state('iconify')``. 

        .. py:method:: title(text=None)

                    Sert à configurer le titre de la fenêtre. Si l'argument est omis, elle retourne le titre courant.

        .. py:method:: transient(parent=None)

                    Une fenêtre est dite *transient* si elle apparaît toujours devant son parent. Lorsque le parent est réduit en icône, la fenêtre *transient* est iconifiée en même temps.
                    
                    Cette méthode fait de la fenêtre appelante une fenêtre *transient* relativement à une autre fenêtre parent fournie en argument; the default parent window is this window's parent.

                    Cette méthode est utile pour les fenêtres surgissantes à courte durée de vie qui servent à obtenir une information de la part de l'utilisateur.

        .. py:method:: withdraw()

                    Cache la fenêtre. Pour la faire réapparaître, utiliser les méthodes ``deiconify()`` ou ``iconify()``.
    
