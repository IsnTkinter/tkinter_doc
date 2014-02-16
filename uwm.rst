.. _UNIVERSAL:

************************************
Méthodes communes à tous les widgets
************************************

Les méthodes données ci-après sont communes à tous les widgets. Dans les description, ``w`` désigne un widget de type arbitraire.

.. hlist::
        :columns: 3

        * :py:meth:`after`
        * :py:meth:`after_cancel`
        * :py:meth:`after_idle`
        * :py:meth:`bell`
        * :py:meth:`bind`
        * :py:meth:`bind_all`
        * :py:meth:`bind_class`
        * :py:meth:`bindtags`
        * :py:meth:`cget`
        * :py:meth:`clipboard_append`
        * :py:meth:`clipboard_clear`
        * :py:meth:`column_configure`
        * :py:meth:`config`
        * :py:meth:`configure`
        * :py:meth:`destroy`
        * :py:meth:`event_add`
        * :py:meth:`event_delete`
        * :py:meth:`event_generate`
        * :py:meth:`event_info`
        * :py:meth:`focus_displayof`
        * :py:meth:`focus_force`
        * :py:meth:`focus_get`
        * :py:meth:`focus_lastfor`
        * :py:meth:`focus_set`
        * :py:meth:`grab_current`
        * :py:meth:`grab_release`
        * :py:meth:`grab_set`
        * :py:meth:`grab_set_global`
        * :py:meth:`grab_status`
        * :py:meth:`grid_forget`
        * :py:meth:`grid_propagate`
        * :py:meth:`grid_remove`
        * :py:meth:`image_names`
        * :py:meth:`keys`
        * :py:meth:`lift`
        * :py:meth:`lower`
        * :py:meth:`mainloop`
        * :py:meth:`nametowidget`
        * :py:meth:`option_add`
        * :py:meth:`option_clear`
        * :py:meth:`option_get`
        * :py:meth:`option_readfile`
        * :py:meth:`register`
        * :py:meth:`quit`
        * :py:meth:`rowconfigure`
        * :py:meth:`selection_clear`
        * :py:meth:`selection_get`
        * :py:meth:`selection_own`
        * :py:meth:`selection_own_get`
        * :py:meth:`tk_focusFollowsMouse`
        * :py:meth:`tk_focusNext`
        * :py:meth:`tk_focusPrev`
        * :py:meth:`unbind`
        * :py:meth:`unbind_all`
        * :py:meth:`unbind_class`
        * :py:meth:`update`
        * :py:meth:`update_idletasks`
        * :py:meth:`wait_variable`
        * :py:meth:`wait_visibility`
        * :py:meth:`wait_window`
        * :py:meth:`winfo_children`
        * :py:meth:`winfo_class`
        * :py:meth:`winfo_containing`
        * :py:meth:`winfo_depth`
        * :py:meth:`winfo_fpixels`
        * :py:meth:`winfo_geometry`
        * :py:meth:`winfo_height`
        * :py:meth:`winfo_id`
        * :py:meth:`winfo_ismapped`
        * :py:meth:`winfo_manager`
        * :py:meth:`winfo_name`
        * :py:meth:`winfo_parent`
        * :py:meth:`winfo_pathname`
        * :py:meth:`winfo_pixels`
        * :py:meth:`winfo_pointerx`
        * :py:meth:`winfo_pointerxy`
        * :py:meth:`winfo_pointery`
        * :py:meth:`winfo_reqheight`
        * :py:meth:`winfo_reqwidth`
        * :py:meth:`winfo_rgb`
        * :py:meth:`winfo_rootx`
        * :py:meth:`winfo_rooty`
        * :py:meth:`winfo_screenheight`
        * :py:meth:`winfo_screenmmheight`
        * :py:meth:`winfo_screenmmwidth`
        * :py:meth:`winfo_screenvisual`
        * :py:meth:`winfo_screenwidth`
        * :py:meth:`winfo_toplevel`
        * :py:meth:`winfo_viewable`
        * :py:meth:`winfo_width`
        * :py:meth:`winfo_x`
        * :py:meth:`winfo_y`

.. py:method:: after(delai_ms, fonc=None, \*args)

        Demande à Tkinter d'appeller la fonction de rappel *fonc* avec les arguments *args* après l'écoulement du délai *delai_ms* donné en millisecondes. Votre fonction de rappel ne peut pas être appelée avant ce délai (même si son appel effectif peut le dépasser) et elle ne sera appelée qu'une fois.
            
        Elle retourne un entier qui sert d'identifiant et qui peut être passé à la méthode ``after_cancel`` pour annuler la demande d'appel de *fonc*.

        Si vous ne donnez aucune fonction de rappel, cette fonction arrête l'exécution du programme pendant la durée du délai indiqué (comme la fonction standard sleep du module time).
            
.. py:method:: after_cancel(id)

        Annule la demande d'appel d'une fonction après un certain délai définie par la méthode ``after``. L'argument *id* est l'identifiant numérique retourné par la méthode ``after``.

.. py:method:: after_idle(fonc, \*args)

        Demande à Tkinter d'appeler la fonction *fonc* avec les arguments *args* la prochaine fois qu'il se trouvera en "sommeil", c'est à dire, la prochaine fois qu'il n'aura plus aucun événement à traiter. La fonction *fonc* n'est appelée qu'une seule fois. Si vous souhaitez la rappeler, il faudra utiliser à nouveau cette méthode.

.. py:method:: bell()

        Produit un son, généralement un bip. 

.. py:method:: bind(sequence=None, evtGest=None, add=None)

        Cette méthode est utilisée pour attacher un gestionnaire d'événement (une fonction) à la survenue d'un événement, précisé par *sequence*, sur le widget appelant (sur lequel cette méthode a été appliquée). Voir :ref:`EVENTS` pour une vue d'ensemble sur le moyen de rendre votre application réactive aux actions de l'utilisateur.

        L'argument *sequence* sert à décrire le type d'événement (action de l'utilisateur) auquel il faut réagir par le moyen du gestionnaire *evtGest*, c'est à dire en appelant cette fonction lorsque survient l'événement surveillé sur le widget. Si une liaison avait déjà été définie sur ce widget, l'ancien gestionnaire d'événement est remplacé par le nouveau sauf si vous utilisez ``add='+'``; dans ce cas les gestionnaires définie précédement sont préservés.

.. py:method:: bind_all(sequence=None, func=None, add=None)

        Similaire à la méthode ``bind()``, mais s'applique à tous les widgets de l'application.

.. py:method:: bind_class(type, sequence=None, func=None, add=None)

        Similaire à la méthode ``bind()``, mais s'applique à tous les widgets du type indiqué par l'argument *type* (par exemple ``'Button'``).

.. py:method:: bindtags(tagList=None)

        Si vous appelez cette méthode sans argument, elle vous retournera les marques (tags) "de liaison" pour le widget appelant sous la forme d'une liste de chaînes de caractères. Une marque de liaison est le nom d'une fenêtre (qui débute par un '.') ou un type de widgtet (par exemple 'Listbox').

        Vous pouvez modifier l'ordre dans lequel les niveaux de liaison sont appelés en passant à la méthode la liste des marques de liaison que vous souhaitez que le widget utilise.

        Voir :ref:`EVENTS` pour une discussion sur les niveaux de liaison et leur relation avec les marques.

.. py:method:: cget(option)

        Retourne la valeur courante de l'*option* indiquée par une chaîne de caractères. Vous pouvez aussi obtenir la valeur d'une option d'un widget ``w`` en utilisant la syntaxe ``w[option]``.

.. py:method:: clipboard_append(text)

        Ajoute la chaine de caractères *text* au presse-papiers.

.. py:method:: clipboard_clear()

        Efface le contenu du presse-papiers. (voir la méthode ``clipboard_append()`` ci-dessus).

.. py:method:: column_configure()

        Voir :ref:`autres-meth-grille`.

.. py:method:: config(option=value, ...)

        Identique à la méthode ``configure()``.

.. py:method:: configure(option=value, ...)

        Sert à configurer les valeurs d'une ou plusieurs options. Pour les options dont les noms sont des mots réservés de Python (class, from, in), ajoutez un caractère «souligné» à la fin de l'option:  'class\_', 'from\_', 'in\_'.

        Vous pouvez aussi configurer la valeur d'une option pour le widget ``w`` avec une instruction de la forme ``w[option] = value``.

        Si vous appelez la méthode ``config()`` sans arguments, elle retourne un dictionnaire de toutes les options du widget appelant. Les clés sont les noms des options (incluant les alias comme bd pour borderwidth). La valeur pour chaque clé est: 

        * Pour la plupart des entrées, un tuple à 5 éléments: ``(nom de l'option, clé de l'option dans la bdd, classe de l'option dans la bdd, valeur par défaut, valeur courante)``; ou,

        * Pour les alias (comme 'fg'), un tuple à deux éléments: ``(alias, nom standard équivalent)``. 

.. py:method:: destroy()

        L'appel ``w.destroy()`` sur un widget ``w`` détruit ``w`` ainsi que tous ses enfants.

.. py:method:: event_add(virtevt, \*sequences)

        Cette méthode crée un événement virtuel dont le nom est la chaîne de caractères donnée comme premier argument *virtevt*. Chaque argument supplémentaire décrit une «séquence», c'est à dire, la description d'un événement physique (appui sur une touche, mouvement de la souris ...). Lorsque cet événement se produit, le nouvel événement virtuel est déclenché.

        Voir :ref:`EVENTS` pour une description générale des événements virtuels.

.. py:method:: event_delete(virtevt, \*sequences)

        Supprime le ou les événements physiques associés à l'événement virtuel dont le nom est précisé en premier argument par la chaîne *virtevt*. Si tous les événements physiques sont supprimés de l'événement virtuel, cet événement virtuel ne sera plus déclenché.

.. py:method:: event_generate(sequence, \*\*kw)

        Cette méthode déclenche l'événement (sans que le stimulus externe n'ait eu lieu). La gestion de l'événement n'est pas différete de celle qui est engagée avec un stimuli externe. L'argument *sequence* décrit l'événement à déclencher. Vous pouvez configurer les valeurs des attributs de l'objet événement qui sera passé au gestionnaire en fournissant des arguments de la forme ``attr=valeur``, où ``attr`` est le nom d'un attribut de l'objet ``Event``.

        Voir :ref:`EVENTS` pour une discussion complète des événements.

.. py:method:: event_info(virtual=None)

        Si vous appelez cette méthode sans argument, vous obtenez la liste de tous les événements virtuels qui sont actuellement définis.

        Pour récupérer les événements physiques associés à un événement virtuel, précisez son nom et vous obtiendrez la liste de tous les événements physiques associés ou ``None`` s'il n'y en a pas.

.. py:method:: focus_displayof()

        Retourne le nom de la fenêtre qui possède actuellement le focus sur le même écran que le widget appelant. Retourne ``None`` Si aucune telle fenêtre n'a le focus.

        Voir :ref:`FOCUS` pour une description générale du focus.

.. py:method:: focus_force()

        Force le focus sur le widget appelant. Ce n'est pas très poli. Il vaut mieux attendre que le gestionnaire de fenêtre donne lui-même le focus. Voir aussi la méthode :py:meth:`grab_set_global` ci-dessous. 

.. py:method:: focus_get()

        Retourne le widget qui possède actuellement le focus s'il y en a, autrement retourne ``None``.

.. py:method:: focus_lastfor()

        Cette méthode retourne le nom du widget qui est le dernier a avoir eu le focus dans la fenêtre mère qui contient le widget appelant. Si aucun widget de la fenêtre mère n'a eu le focus, elle retourne le nom de la fenêtre mère. Si l'application n'a pas le focus, elle retournera le nom du widget qui aura le focus lorsque l'application l'obtiendra de nouveau.

.. py:method:: focus_set()

        Si l'application qui contient le widget appelant a le focus, le focus est dirigé vers ce widget. Sinon, Tk le donnera au widget lorsque l'application aura le focus à nouveau.

.. py:method:: grab_current()

        If there is a grab in force for w's display, return its identifier, otherwise return None. Refer to Section 54, “Events” for a discussion of grabs. 

.. py:method:: grab_release()

        If w has a grab in force, release it. 

.. py:method:: grab_set()

        Widget w grabs all events for w's application. If there was another grab in force, it goes away. See Section 54, “Events” for a discussion of grabs. 

.. py:method:: grab_set_global()

        Widget w grabs all events for the entire screen. This is considered impolite and should be used only in great need. Any other grab in force goes away. Try to use this awesome power only for the forces of good, and never for the forces of evil, okay? 

.. py:method:: grab_status()

        If there is a local grab in force (set by .grab_set()), this method returns the string 'local'. If there is a global grab in force (from .grab_set_global()), it returns 'global'. If no grab is in force, it returns None. 

.. py:method:: grid_forget()

        Voir :ref:`autres-meth-grille`. 

.. py:method:: grid_propagate()

        Voir :ref:`autres-meth-grille`.  

.. py:method:: grid_remove()

        Voir :ref:`autres-meth-grille`.

.. py:method:: image_names()

        Retourne les noms de toutes les images de l'application (sous la forme d'une séquence de chaînes de caractères) qui contient le widget appelant.

.. py:method:: keys()

        Retourne les noms des options du widget sous la forme d'une liste de chaînes de caractères.

.. py:method:: lift(aboveThis=None)

        Si l'argument est ``None``, la fenêtre qui contient le widget appelant est déplacée tout en haut de la pile des fenêtres. Pour déplacer la fenêtre juste au-dessus d'une fenêtre principale ``f``, la fournir en argument.

.. py:method:: lower(belowThis=None)

        Si l'argument est ``None``, la fenêtre qui contient le widget appelant est déplacée tout en bas de la pile des fenêtres. Pour déplacer la fenêtre juste en dessous d'une fenêtre principale ``f``, la fournir en argument.

.. py:method:: mainloop()

        Cette méthode doit être appelée (généralement après avoir créé tous les widgets statiques) afin de démarrer le traitement des événements. Vous pouvez arrêter ce traitement en boucle en utilisant la méthode :py:meth:`quit` ci-dessous. Vous pouvez aussi appeler cette méthode à l'intérieur d'un gestionnaire d'événement pour redémarrer le traitement des événements (main loop).

.. py:method:: nametowidget(nom)

        Retourne le widget dont le chemin de nommage est nom. Voir :ref:`nomfen`. Si le nom est inconnu, cette méthode lancera une exception du type ``KeyError``. 

.. py:method:: option_add(motif, value, priorite=None)

        Cette méthode ajoute des valeurs par défaut à la base de données des options de Tkinter. L'argument *motif* est une chaîne de caractères qui précise l'option à configurer par défaut pour un ou plusieurs widgets. L'argument *priorite* peut prendre l'une des valeurs suivantes:
        20 	Pour les propriétés par défaut des widgets.
        40 	Pour les propriétés par défaut qui concerne des applications particulières.
        60 	Pour les options précisées dans des fichiers d'utilisateur.
        80 	Pour les options qui sont configurées au démarrage de l'application. C'est ce niveau qui a la priorité par défaut.

        Plus la valeur est grande, plus le réglage correspondant est prioritaire. Voir :ref:`APPEARANCE` pour une vue d'ensemble de la base de données des options. La syntaxe de l'argument *motif* est la même que celle du début d'une ligne de spécification d'option dans la base de donnée.

        Par exemple, pour obtenir les effets de cette ligne de spécification:

        ``*Button*font: times 24 bold``

        votre application peut contenir ces lignes:

        .. code-block:: python

                grandeFonte = tkFont.Font(family='times', size=24,
                                     weight='bold')
                root.option_add('*Button*font', grandeFonte)

        Chaque bouton créé après l'exécution de ces lignes utilisera par défaut une police Times grasse de 24 points (sauf si l'option font est renseignée dans le constructeur de bouton).

.. py:method:: option_clear()

        Cette méthode supprime toutes les champs de la base de données des options de Tkinter. Cela a pour effet de revenir à toutes les valeurs par défauts.

.. py:method:: option_get(name, classname)

        Utilisez cette méthode pour récupérer la valeur courante d'une option de la base de données des options de Tkinter. Le premier argument est la clé de l'instance et le second la clé de la classe. S'il y a correspondance, elle retourne la valeur de l'option qui correspond le mieux. Sinon, elle retourne une chaîne vide.

        Reportez-vous à :ref:`APPEARANCE` pour en savoir plus sur la façon dont les clés sont mises en correspondance avec les options.

.. py:method:: option_readfile(fileName, priority=None)

        Afin de permettre à l'utilisateur de configurer l'interface, vous pouvez désigner le nom d'un fichier dans lequel l'utilisateur pourra mémoriser ses options préférées en utilisant le même format que celui du fichier .Xdefaults. Ainsi, lors de l'initialisation de l'application, vous pouvez indiquer ce fichier à cette méthode et les options qu'il contient seront ajoutées à la base de données des options. Si le fichier n'existe pas ou si son format est invalide, cette méthode lèvera une erreur du type ``TclError``.

        Reportez-vous à :ref:`APPEARANCE` pour une introduction à la base de données des options ainsi qu'au format des fichiers d'options.

.. py:method:: register(function)

        Cette méthode crée un «emballage Tcl» autour d'une fonction Python, et retourne le nom de cet «emballage» sous la forme d'une chaîne de caractères. Pour un exemple d'utilisation de cette méthode, voir :ref:`validation`.

.. py:method:: quit()

        Cette méthode fait sortir de la boucle des événéments (mainloop). Voir la méthode :py:meth:`mainloop` ci-dessous pour plus d'informations sur la boucle des événements.

.. py:method:: rowconfigure()

        Voir :ref:`autres-meth-grille`.

.. py:method:: selection_clear()

        Si le widget appelant possède une sélection (comme une portion de texte mis en valeur dans un widget de saisie), cette sélection est effacée.

.. py:method:: selection_get()

        Si le widget appelant possède une sélection, cette méthode retourne le texte sélectionné. Sinon, une erreur du type ``TclError`` est levée.

.. py:method:: selection_own()

        Fait du widget appelant le «propriétaire» de la sélection dans sa zone d'affichage, la volant au propriétaire précédent s'il y en avait un.Make w the owner of the selection in w's display, stealing it from the previous owner, if any. 

.. py:method:: selection_own_get()

        Retourne le widget qui possède actuellement la sélection sur la zone d'affichage du widget appelant. Lève une erreur de type ``TclError`` s'il n'y a aucune sélection.

.. py:method:: tk_focusFollowsMouse()

        Normalement le focus circule en boucle sur une liste de widgets déterminés par leur hiérachie et l'ordre de leur création; voir :ref:`FOCUS`. Pour dire à Tkinter de forcer le focus en fonction de la position de la souris, utilisez cette méthode. Notez qu'il est difficile de supprimer ce comportement une fois qu'il a été activé.

.. py:method:: tk_focusNext()

        Retourne le widget qui suit le widget appelant dans la liste de traversée du focus. Voir :ref:`FOCUS` pour plus d'information sur la traversée du focus.

.. py:method:: tk_focusPrev()

        Retourne le widget qui précède le widget appelant dans la liste de traversée du focus.

.. py:method:: unbind(sequence, funcid=None)

        Cette méthode supprime la liaison d'événement du widget appelant, pour un événement décrit par *sequence*. Si le second argument est un gestionnaire associé à cet événement, ce gestionnaire est détruit mais pas les autres s'il y en a. Si le second argument est omis, toutes les liaisons pour l'événement considéré sont supprimées.

        Voir :ref:`EVENTS` pour une discussion générale à propos des liaisons d'événements.

.. py:method:: unbind_all(sequence)

        Supprime toutes les liaisons d'événement de l'application pour l'événement décrit par la chaîne *sequence*.

.. py:method:: unbind_class(className, sequence)

        Similaire à unbind_all(), mais s'applique à tous les widgets de type *className* (c'est à dire 'Entry' ou 'Listbox'). 

.. py:method:: update()

        Cette méthode force le rafraîchissement de l'affichage. Vous ne devriez l'utiliser que si vous savez ce que vous faites puisqu'elle peut conduire à un comportement imprévisible ou à une boucle infinie. Dans tous les cas, elle ne devrait jamais être appelée à partir d'un gestionnaire d'événement ou d'une fonction appelée par un tel gestionnaire.

.. py:method:: update_idletasks()

        certaines tâches dans la mise à jour de l'affichage, comme l'agrandissement/réduction d'un widget, sont dites dormantes ou en sommeil (idle) parce qu'elles sont normalement reportées jusqu'au moment où l'application a terminé de s'occuper des événements et est revenue dans la boucle principale pour attendre les prochains.

        Si vous souhaitez forcer le rafraîchissement de l'affichage avant que l'application soit de nouveau en sommeil, appelez cette méthode sur un widget arbitraire.

.. py:method:: wait_variable(v)

        Attend que la valeur de la variable *v* soit modifiée. Cette méthode déclenche une boucle locale d'attente, elle ne bloque donc pas le reste de l'application.

.. py:method:: wait_visibility(w)

        Attend que l'état de visibilité du widget *w* (typiquement une fenêtre principale) soit modifié.

.. py:method:: wait_window(w)

        Attend que la fenêtre *w* soit détruite. S'utilise typiquement pour attendre qu'un utilisateur ait fini d'interagir avec une fenêtre de dialogue avant d'utiliser le résultat de ses choix.

.. py:method:: winfo_children()

        Retourne la liste de tous les widgets enfants du widget appelant dans leur ordre de rangement dans la pile: du plus bas au plus haut.

.. py:method:: winfo_class()

        Retoune le type du widget appelant (par exemple 'Button'). 

.. py:method:: winfo_containing(rootX, rootY, displayof=0)

        Cette méthode est utilisée pour trouver la fenêtre qui contient le point (rootX, rootY). Si l'argument displayof est 0 (valeur par défaut), les coordonnées sont relatives à la fenêtre principale de l'application; si il vaut 1, les coordonnées sont relative à la fenêtre de haut niveau (top-level) qui contient le widget appelant. Si le point (rootX, rootY) se trouve dans l'une des fenêtre de haut niveau de l'application, cette méthode retourne cette fenêtre, autrement elle retourne None.

.. py:method:: winfo_depth()

        Retourne le nombre de bits par pixels utilisés dans l'affichage du widget appelant.

.. py:method:: winfo_fpixels(dim)

        Convertit et retourne la dimension *dim* (voir :ref:`dimensions`) en pixels de l'affichage du widget appelant sous la forme d'un float.

.. py:method:: winfo_geometry()

        Retourne la chaîne de géométrie ``"Largeurxhauteur+x+y"`` qui décrit la taille et la position sur l'écran du widget appelant. Voir :ref:`geometrie`.

        Attention, cette chaîne n'est précise qu'une fois que l'application a traitées ses tâches en sommeil. En particulier, toutes les chaînes géométriques sont initialisées à '1x1+0+0' jusqu'au moment où le widget et le gestionnaire de positionnement ont négociés tailles et positions. Voir la méthode :py:meth:`update_idletasks` ci-dessus pour s'assurer que la géométrie du widget a été mise à jour.

.. py:method:: winfo_height()

        Retourne la hauteur courante du widget appelant en pixels. Voir les remarques sur les mises à jour de sa géométrie faites pour la méthode ``winfo_geometry()`` ci-dessus. Vous préfererez probablement la méthode :py:meth:`winfo_reqheight`, décrite ci-après, qui assure que la géométrie est à jour.

.. py:method:: winfo_id()

        Retourne un entier qui identifie de manière unique le widget appelant relativement à sa fenêtre mère. Vous aurez besoin de cela pour utiliser la méthode winfo_pathname() ci-dessous.

.. py:method:: winfo_ismapped()

        Retourne ``True`` si le widget appelant à été positionné (mapped) par un gestionnaire de positionnement (grid, pack ou place) à l'intérieur de son parent et si son parent a lui-même été positionné et ainsi de suite jusqu'à la fenêtre de plus haut niveau. Autrement, la méthode retourne False.

.. py:method:: winfo_manager()

        Si le widget appelant n'a pas été positionné par un gestionnaire de positionnement (grid, pack ou place), cette méthode retoune une chaîne vide. Autrement, elle retourne une chaîne qui peut être 'grid', 'pack', 'place', 'canvas', ou 'text'. 

.. py:method:: winfo_name()

        Cette méthode retourne le nom relatif (à son parent) du widget appelant. Voir :ref:`nomfen`. Voir aussi la méthode :py:meth:`winfo_pathname` ci-dessous pour obtenir le nom (chemin) complet.

.. py:method:: winfo_parent()

        Retourne le nom-chemin du parent du widget appelant ou une chaîne vide si c'est une fenêtre mère. Voir :ref:`nomfen` pour plus de détails sur les nom-chemin des widgets.

.. py:method:: winfo_pathname(id, displayof=0)

        Si l'argument *displayof* est False (ou 0), cette méthode retourne le nom du chemin hierarchique du widget d'identifiant *id* dans la fenêtre principale de l'application. Si *displayof* vaut True, l'identifiant est relatif à la fenêtre mère (top-level) qui contient le widget appelant. Voir :ref:`nomfen` pour une discussion à propos des nom de chemin hiérarchique des widgets.

.. py:method:: winfo_pixels(dim)

        Pour toute dimension (voir :ref:`dimensions`), cette méthode retourne l'équivalent en pixel pour l'affichage du widget appelant. La valeur retourné est un entier.

.. py:method:: winfo_pointerx()

        Retourne la composante x du tuple retourné par la méthode winfo_pointerxy() décrite ci-après. 

.. py:method:: winfo_pointerxy()

        Retourne un tuple (x, y) qui contient les coordonnées du pointeur de souris relativement au bord gauche de l'écran.

.. py:method:: winfo_pointery()

        Retourne la composante y du tuple retourné par la méthode winfo_pointerxy() décrite plus tôt. 

.. py:method:: winfo_reqheight()

        Retourne la hauteur requise du widget appelant. Il s'agit de la hauteur minimale pour avoir la place d'afficher le contenu du widget. La véritable hauteur peut être différente suite à l'intervention d'un gestionnaire de positionnement.

.. py:method:: winfo_reqwidth()

        Similaire à la méthode précédente pour la largeur du widget appelant.

.. py:method:: winfo_rgb(color)

        Retourne le tuple (rouge, vert, bleu) qui est équivalent à la couleur passé en argument. Chaque composante du tuple est un entier de l'intervalle [0; 65536[. Par exemple, pour la couleur 'green', elle retourne (0, 65535, 0).

        Pour en savoir plus sur les moyens de préciser les couleurs, voir :ref:`couleurs`. 

.. py:method:: winfo_rootx()

        Retourne la coordonnée horizontale x du côté gauche du widget appelant relativement à l'écran. 

.. py:method:: winfo_rooty()

        Similaire à la méthode précédente mais pour la coordonnée verticale y.

.. py:method:: winfo_screenheight()

        Retourne la hauteur de l'écran en pixels.

.. py:method:: winfo_screenmmheight()

        Retourne la hauteur de l'écran en millimètres.

.. py:method:: winfo_screenmmwidth()

        Retourne la largeur de l'écran en millimètres.

.. py:method:: winfo_screenvisual()

        Retourne une chaîne qui décrit la méthode employée pour le rendu des couleurs. Cela peut être 'truecolor' pour des affichages de 16 ou 24 bits, 'pseudocolor' pour des affichages 8 bits. 

.. py:method:: winfo_screenwidth()

        Retourne la largeur de l'écran en pixels.

.. py:method:: winfo_toplevel()

        Retourne la fenêtre de plus haut niveau (top-level) qui contient le widget appelant. Cette fenêtre peut utiliser toutes les méthodes des widgets ``Toplevel``, voir :ref:`TOPLEVEL`.

.. py:method:: winfo_viewable()

        Retourne True si le widget appelant est affichable, c'est à dire si lui et tous ces ancêtres de la même fenêtre de plus haut niveau ont été positionnés par un gestionnaire de positionnement.

.. py:method:: winfo_width()

        Retourne la largeur courante du widget appelant en pixels. Voir les remarques sur les mises à jour de l'affichage faites lors de la description de la méthode :py:meth:`winfo_geometry`. Vous pouvez préférer utiliser la méthode :py:meth:`winfo_reqwidth` décrite plus tôt; la valeur obtenue est toujours à jour.

.. py:method:: winfo_x()

        Retourne l'abscisse x (horizontale) du côté gauche du widget appelant relativement à son parent.

.. py:method:: winfo_y()

        Similaire à la méthode précédente mais pour y.
