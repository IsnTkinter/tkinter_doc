.. _EVENTS:

******************************************************
Les événements: répondre aux actions de l'utilisateur.
******************************************************

Un événement est la survenue de quelquechose dans votre application - par exemple, l'utilisateur appuie sur une touche, clique avec sa souris ou la déplace - à quoi votre application à besoin de réagir.

Les widgets ont normalement un grand nombre de comportements prédéfinis. Par exemple, un bouton réagira à un clic souris en appelant sa fonction de rappel associé à son option *command*. Un autre exemple, si vous déplacez le focus sur un widget de saisi et que vous appuyez sur une lettre, cette lettre sera ajoutée au contenu du widget.

Cependant, tkinter fourni tous les moyens pour ajouter, changer ou supprimer de tels comportements.

Premièrement, quelques définitions:

* Un événement est la survenue d'une action (clavier, souris) dont votre application a besoin d'être informée.

* Un gestionnaire d'événement est une fonction de votre application qui sera appelée lorsqu'un certain événement se produira.

* Nous parlons de liaison lorsque votre application défini un gestionnaire d'événement qui sera appelé lorsqu'un événement se produit sur un widget.
    
Niveaux de liaisons
===================

Vous pouvez lier un gestionnaire à un événement à l'un de ces trois niveaux:

1) **Liaison au niveau d'un widget**: Vous pouvez lier un événement à un widget particulier. Par exemple, vous pourriez lier la touche PageUp dans un canevas à un gestionnaire qui s'occuperait de le faire défiler d'une page vers le haut. Pour lier un événement à un widget, appelez la méthode ``.bind()`` sur ce widget (voir “Universal widget methods”).

   Par exemple, supposez que vous ayez un canevas référencé par ``can`` et que vous souhaitiez dessiner un disque orange sur ce canevas à chaque fois que l'utilisateur appui sur le bouton 2 de la souris (celui du milieu). Pour définir ce comportement:

   ::

        can.bind('<Button-2>', dessineDisqueOrange)

   Le premier argument est un descripteur de séquence qui indique à tkinter que lorsque le bouton centrale de la souris est pressé, il faut qu'il appelle le gestionnaire d'événement appelé ``dessineDisqueOrange`` (Voir “Writing your handler: The Event class”, ci-dessous, pour une vue d'ensemble sur la manière d'écrire un gestionnaire comme ``dessineDisqueOrange``). Notez qu'il faut omettre les parenthèses du gestionnaire d'événement afin que Python utilise la référence au gestionnaire plutôt que d'essayer de l'appeler sur le champ.

2) **Liaison au niveau d'une classe**: Vous pouvez lier un événement à tous les widgets d'une classe donnée. Par exemple, vous pourriez souhaiter régler tous les boutons pour qu'ils réagissent à l'appui sur le bouton centrale de la souris en changeant leur étiquette du français vers l'anglais et vice versa. Pour lier un événement à tous les widgets d'une classe, utiliser la méthode ``.bind_clas()`` sur n'importe quel widget (voir “Universal widget methods”, ci-dessous).

   Par exemple, supposez que vous ayez plusieurs canevas, et que vous souhaitiez régler les choses de telle sorte que lorsque l'utilisateur clique sur le bouton central de la souris, un disque orange soit tracé dans celui sur lequel se trouve la souris. Plutôt que d'appeler la méthode ``.bind()`` pour chaque canevas, vous pouvez définir ce comportement en une fois en utilisant quelquechose de ce genre:

   ::

       # w est un widget arbitraire
       w.bind_class('Canvas', '<Button-2>', dessineDisqueOrange) 

3) **Liaison au niveau de l'application**: Vous pouvez définir une liaison d'événement de telle sorte que le gestionnaire d'événement soit appelé indépendament du widget qui a le focus ou qui se trouve sous la souris. Par exemple, vous pourriez souhaiter lier l'événement «appui sur la touche ImprÉcran» à tous les widgets de l'applicatoin de telle sorte que l'écran soit imprimé indépendamment du widget qui a effectivement reçu l'appui sur la touche. Pour lier un événement au niveau de l'application, appeler la méthode ``.bind_all()`` sur n'importe quel widget (voir “Universal widget methods”).

   Voici comment vous pourriez lier l'appui sur la touche, *Key*, ImprÉcran, *Print*, à l'effet désiré:

   ::
  
        w.bind_all('<Key-Print>', imprimeEcran)

Séquence d'événement
====================

Tkinter dispose d'une méthode générale et puissante pour vous permettre d'indiquer précisément à quels événements vos gestionnaires sont liés.

En général, une séquence d'événement est une chaîne de caractère qui contient un ou plusieurs motifs d'événements. Chaque motif d'événement décrit quelquechose qui peut survenir pendant l'éxécution de votre application. S'il y a plus d'un motif dans une séquence d'événements, le gestionnaire associé sera appelé seulement si tous les motifs de la séquences se produisent en effet.

La forme générale d'un motif d'événement est la suivante:


        ``<[modificateur-]...type[-detail]>``

* Le motif est enfermé entre des chevrons <…>.

* Le type de l'événement décrit le genre général de celui-ci, comme l'appui sur une touche ou un clic souris. Voir “Event types”.

* Vous pouvez indiquer un ou plusieurs modificateurs avant son type pour décrire une combinaison comme l'appui sur la touche Maj ou Control pendant qu'une autre touche ou qu'un bouton de la souris est enfoncé. Voir “Event modifiers”

* Vous pouvez ajouter d'autres détails après le type pour décrire la touche ou le bouton précis qui vous intéresse. Pour les boutons de la souris, 1 indique normalement le bouton de gauche, 2 celui du milieu et 3 celui de droite.

  + Notez qu'il est possible que les boutons de la souris soit inversés si un gaucher à effectuer le réglage correspondant de son système.

  + Pour les touches du clavier, il s'agit soit d'un caractère (pour un caractère unique comme pour la touche A ou \*) ou le nom d'une touche; voir  “Key names” pour une liste de tous ces noms.

Voici quelques exemples de motif d'événement:

* ``<Button-1>``: L'utilisateur à appuyer sur le premier bouton de la souris (celui de gauche normalement).
* ``<KeyPress-H>``: L'utilisateur à appuyer sur la touche H.
* ``<Control-Shift-KeyPress-H>``: L'utilsateur a appuyer simultanément sur les touches Control, Maj et H.

Types d'événements
==================

The full set of event types is rather large, but a lot of them are not commonly used. Here are most of the ones you'll need:

.. list-table::
   :header-rows: 1
   :widths: 10 10 80
   
   * - Type
     - Nom
     - Description
   * - 36
     - ``Activate`` 
     - Un widget est passé de l'état inactif à l'état actif. Se rapporte au changement de l'option **state** des widgets comme un bouton qui est inactif (grisé) et devient actif.
   * - 4
     - ``Button`` 
     - L'utilisateur a appuyé sur l'un des boutons de la souris. La partie détail précise le bouton. Pour la molette de la souris sous LinuxT, utilisez (défilement vers le haut) et (défilement vers le bas). Sous Linux, votre gestionnaire pour la molette de la souris distinguera entre le défilement vers le haut et le défilement vers le bas en examinant l'attribut ``.num`` de l'instance d'événement qui lui est fourni; voir “Writing your handler: The Event class”.
   * - 5
     - ``ButtonRelease`` 
     - L'utilisateur relâche un bouton de la souris. C'est probablement un meilleur choix dans la plupart des cas d'utiliser ce type d'événement plutôt que ``Button`` parce que si les utilsateurs appuient accidentellement sur le bouton, ils peuvent bouger la souris en-dehors du widget pour éviter de lancer l'action.
   * - 22
     - ``Configure`` 
     - L'utilisateur à modifier la taille d'un widget, par exemple en déplaçant un coin ou un côté de la fenêtre.
   * - 37
     - ``Deactivate`` 
     - Un widget est passé de l'état actif à l'état inactif. Se rapporte au changment de l'option **state** des widgets comme pour un bouton radio qui change d'état en devenant grisé.
   * - 17
     - ``Destroy`` 
     - Un widget a été détruit.
   * - 7
     - ``Enter`` 
     - L'utilisateur a bougé la souris qui est entrée dans la partie visible d'un widget. (Ne pas confondre avec la touche Entrée, qui est événement de type ``KeyPress`` pour une touche dont le nom est 'return'.)
   * - 12
     - ``Expose`` 
     - Cette événement se produit à chaque fois qu'au moins une partie de votre application ou d'un widget devient visible après avoir été recouvert par une autre fenêtre.
   * - 9
     - ``FocusIn`` 
     - Un widget obtient le focus (voir “Focus: routing keyboard input” pour une introduction générale à la notion de focus). Cela peut se produire soit en réponse à une action de l'utilisateur (comme en utilisant la touche Tab pour déplacer le focus entre les widgets) ou de manière programmée (par exemple lorsque votre programme appelle la méthode ``.focus_set()`` sur un widget).
   * - 10
     - ``FocusOut`` 
     - Le focus a été perdu par un widget. Comme avec ``FocusIn``, l'utilisateur peut produire un tel événement ou il peut se produire de manière programmée.
   * - 2
     - ``KeyPress`` 
     - L'utilisateur a appuyé sur une touche du clavier. La partie détail précise la touche particulière. Ce mot clé peut être abrégé par ``Key``.
   * - 3
     - ``KeyRelease`` 
     - L'utilisateur à relâché une touche du clavier.
   * - 8
     - ``Leave`` 
     - L'utilisateur à déplacer le pointeur de la souris en dehors d'un widget.
   * - 19
     - ``Map`` 
     - Un widget a été «mappé» (associé), c'est à dire, a été rendu visible dans l'application. Cela arrive, par exemple, lorsque vous appelez la méthode ``.grid()`` d'un widget.
   * - 6
     - ``Motion`` 
     - L'utilisateur a déplacé la souris à l'intérieur d'un widget.
   * - 38
     - ``MouseWheel`` 
     - L'utilisateur a tourné la molette de la souris, vers le haut ou vers le bas. Pour l'instant, cela n'est pris en compte que par Windows ou MacOS, mais pas par Linux. Pour ces systèmes, voir la discussion de l'attribut ``.delta`` d'une instance d'un objet de classe ``Event`` dans “Writing your handler: The Event class”. Pour Linux, se rapporter à la note ci-dessus pour le type ``Button``.
   * - 18
     - ``Unmap`` 
     - Un widget a perdu l'association (le «mappage») et n'est plus visible. Cela arrive, par exemple, lorsque vous appelez la méthode ``.grid_remove()`` d'un widget.
   * - 15
     - ``Visibility`` 
     - Se produit lorsqu'au moins une partie de la fenêtre d'application est devenue visible à l'écran.

Modificateurs d'événement
=========================

Les noms des modificateurs que vous pouvez utiliser dans une séquence d'événements sont, entre autres:

* ``Alt`` : Vrai si l'utilisateur est en train de maintenir enfoncée la touche Alt.

* ``Any`` : Ce modificateur généralise un type d'événement. Par exemple, le motif d'événement ``'<Any-KeyPress>'`` correspond à l'appui sur une touche arbitraire.

* ``Control`` : Vrai si l'utilisateur est en train de maintenir enfoncée la touche Ctrl.

* ``Double`` : Indique que deux événements se sont produit en un cours laps de temps. Par exemple, ``<Double-Button-1>`` indique un double clic sur le bouton gauche (normalement) de la souris.

* ``Lock`` : Vrai si l'utilisateur a verrouiller le mode Majuscule.

* ``Shift`` : Vrai si l'utilisateur est en train de maintenir enfoncée la touche Maj.

* ``Triple`` : Comme ``Double``, mais pour l'apparition de 3 événement dans un cours laps de temps.

Vous pouvez utiliser des formes courtes pour préciser un événenemt. Voici quelques exemples:

    ``'<1>'`` revient au même que ``'<Button-1>'``.

    ``'x'`` revient au même que ``'<KeyPress-x>'``. 

Remarquez que vous pouvez omettre les chevrons ``'<…>'`` pour la plupart des caractères, mais que vous ne pouvez pas le faire pour l'espace (dont le nom est ``'<space>'``) ou pour le caractère inférieur à < (dont le nom est ``'<less>'``).

Noms des touches
================

La partie detail d'un motif pour un événement ``KeyPress`` ou ``KeyRelease`` précise la touche que vous souhaitez surveiller. (Voir le modificateur ``Any`` ci-dessus si vous souhaitez surveiller toutes les touches). 

Le tableau ci-dessous montre plusieurs façons de nommer les touches. Voir “Writing your handler: The Event class”, ci-dessous, pour plus d'information sur les objets Event, dont les attributs décrivent les touches de la même manière)

* La colonne ``keysym`` montre le «symbole de touche», une chaîne de caractère pour la touche. Cela correpond à l'attribut ``keysym`` des objets ``Event``.

* La colonne ``keycode`` correpond au «code de touche». C'est un identifiant de touche qui permet de savoir quelle touche a été enfoncée. Notez cependant qu'il ne permet pas de savoir si une touche modificatrice (Maj, Ctrl et VerrMaj) a été ou est enfoncé; ainsi, par exemple, a et A ont le même code de touche.

* La colonne ``keysym_num`` montre un code numérique équivalent au symbole de la touche. Il a la particularité d'être différent selon qu'une touche modificatrice a été ou est enfoncé. Par exemple, le chiffre 2 du clavier numérique (dont le symbole de touche est ``KP_2``) et la flèche «sud» du clavier numérique (de symbole ``KP_Down``) ont le même code de touche (88), mais leurs codes numériques ``keysym_num`` sont différents (65433 et 65458, respectivement).

* La colonne “Touche” montre le texte que vous trouverez habituellement sur la touche de votre clavier, comme Tab par exemple.

Il y a beaucoup de noms de touche pour couvrir de nombreux ensembles de caractères internationaux. Ce tableau montre uniquement l'ensemble “Latin-1” pour un clavier type. Pour connaître l'ensemble des possibilités, reportez-vous à la page de manuel de Tk.

.. list-table::
   :widths: 15 10 10 65
   :header-rows: 1

   * - ``keysym``
     - `keycode`
     - `keysym_num`
     - Touche
   * - ``Alt_L``
     - `64`
     - `65513`
     - La touche Alt située à gauche.
   * - ``BackSpace``
     - `22`
     - `65288`
     - La touche Retour Arrières
   * - ``Cancel``
     - `110`
     - `65387`
     - ???
   * - ``Caps_Lock``
     - `66`
     - `65509`
     - Verr Maj
   * - ``Control_L``
     - `37`
     - `65507`
     - La touche Ctrl de gauche
   * - ``Control_R``
     - `105`
     - `65508`
     - La touche Ctrl de droite
   * - ``Delete``
     - `119`
     - `65535`
     - Suppr
   * - ``Down``
     - `116`
     - `65364`
     - ↓
   * - ``End``
     - `115`
     - `65367`
     - Fin
   * - ``Escape``
     - `9`
     - `65307`
     - Echap
   * - ``Execute``
     - `111`
     - `65378`
     - ???
   * - ``F1``
     - `67`
     - `65470`
     - La touche fonction F1
   * - ``F2``
     - `68`
     - `65471`
     - La touche fonction F2
   * - ``Fi``
     - `66+i`
     - `65469+i`
     - La touche fonction Fi
   * - ``F12``
     - `96`
     - `65481`
     - La touche fonction F12
   * - ``Home``
     - `110`
     - `65360`
     - Début
   * - ``Insert``
     - `118`
     - `65379`
     - inser
   * - ``Left``
     - `113`
     - `65361`
     - ←
   * - ``Linefeed``
     - `54`
     - `106`
     - ??? Linefeed (control-J)
   * - ``KP_0``
     - `90`
     - `65456`
     - 0 sur le clavier numérique
   * - ``KP_1``
     - `87`
     - `65457`
     - 1 sur le clavier numérique
   * - ``KP_2``
     - `88`
     - `65458`
     - 2 sur le clavier numérique
   * - ``KP_3``
     - `89`
     - `65459`
     - 3 sur le clavier numérique
   * - ``KP_4``
     - `83`
     - `65460`
     - 4 sur le clavier numérique
   * - ``KP_5``
     - `84`
     - `65461`
     - 5 sur le clavier numérique
   * - ``KP_6``
     - `85`
     - `65462`
     - 6 sur le clavier numérique
   * - ``KP_7``
     - `79`
     - `65463`
     - 7 sur le clavier numérique
   * - ``KP_8``
     - `80`
     - `65464`
     - 8 sur le clavier numérique
   * - ``KP_9``
     - `81`
     - `65465`
     - 9 sur le clavier numérique
   * - ``KP_Add``
     - `86`
     - `65451`
     - \+ sur le clavier numérique
   * - ``KP_Begin``
     - `84`
     - `65437`
     - La touche centrale (même que 5) sur le clavier numérique
   * - ``KP_Decimal``
     - `91`
     - `65454`
     - Symbole de la ponctuation décimale (,) sur le clavier numérique
   * - ``KP_Delete``
     - `91`
     - `65439`
     - Suppr sur le clavier numérique
   * - ``KP_Divide``
     - `106`
     - `65455`
     - / sur le clavier numérique
   * - ``KP_Down``
     - `88`
     - `65433`
     - ↓ sur le clavier numérique
   * - ``KP_End``
     - `87`
     - `65436`
     - Fin sur le clavier numérique
   * - ``KP_Enter``
     - `104`
     - `65421`
     - Entrée sur le clavier numérique
   * - ``KP_Home``
     - `79`
     - `65429`
     - Début sur le clavier numérique
   * - ``KP_Insert``
     - `90`
     - `65438`
     - insert sur le clavier numérique
   * - ``KP_Left``
     - `83`
     - `65430`
     - ←  sur le clavier numérique
   * - ``KP_Multiply``
     - `63`
     - `65450`
     - × sur le clavier numérique
   * - ``KP_Next``
     - `89`
     - `65435`
     - PageDown sur le clavier numérique
   * - ``KP_Prior``
     - `81`
     - `65434`
     - PageUp sur le clavier numérique
   * - ``KP_Right``
     - `85`
     - `65432`
     - →  sur le clavier numérique
   * - ``KP_Subtract``
     - `82`
     - `65453`
     - \- sur le clavier numérique
   * - ``KP_Up``
     - `80`
     - `65431`
     - ↑ sur le clavier numérique
   * - ``Next``
     - `117`
     - `65366`
     - PageDown
   * - ``Num_Lock``
     - `77`
     - `65407`
     - Verr Num
   * - ``Pause``
     - `127`
     - `65299`
     - Pause
   * - ``Print``
     - `111`
     - `65377`
     - ImprÉcran
   * - ``Prior``
     - `112`
     - `65365`
     - PageUp
   * - ``Return``
     - `36`
     - `65293`
     - La touche Entrée (control-M). Le nom ``Enter`` se réfère à un événement associé à la souris et non au clavier; voir “Events”
   * - ``Right``
     - `114`
     - `65363`
     - →
   * - ``Scroll_Lock``
     - `78`
     - `65300`
     - ???ScrollLock
   * - ``Shift_L``
     - `50`
     - `65505`
     - La touche Maj de gauche
   * - ``Shift_R``
     - `62`
     - `65506`
     - La touche Maj de droite
   * - ``Tab``
     - `23`
     - `65289`
     - La touche de Tabulation, Tab
   * - ``Up``
     - `111`
     - `65362`
     - ↑

Écrire son gestionnaire: la classe ``Event``
============================================

Les sections précédentes vous ont expliqué comment décrire l'événement auquel vous souhaitez réagir et comment le lié à l'application. À présent, intéressons-nous à l'écriture du gestionnaire d'événement qui sera appelé lorsque l'événement aura lieu.

Le gestionnaire d'événement recevra un objet de type ``Event`` qui sert à décrire les circonstances de l'événement. Le gestionnaire peut être une fonction ou une méthode. Voici la forme de la déclaration d'une fonction:

.. code-block:: python

        def nomGestionnaire(evt):


Et pour une méthode:

.. code-block:: python

        def nomGestionnaire(self, evt):

Les attributs de l'objet de type ``Event`` passé au gestionnaire, par l'intermédiaire de son paramètre ``evt``, sont décrit ci-dessous. Certains attributs possède toujours une valeur, mais d'autres n'en possède une que pour certains types d'événements.

.. list-table::
   :widths: 15 85
   :header-rows: 0

   * - ``char`` 
     - Si l'événement est produit par l'appui ou le relâchement d'un touche qui produit un caractère ASCII régulier, cet attribut est le caractère sous la forme d'une chaîne. (Pour des touches spéciales comme Suppr, voir l'attribut ``keysym`` ci-dessous)
   * - ``delta`` 
     - Pour un événement du type ``MouseWheel``, cet attribut contient un entier dont le signe est positif pour un déplacement vers le haut, négatif pour un déplacement vers le bas. Sous Windows, cette valeur sera un multiple de 120; par exemple, 120 désigne un défilement vers le haut en une étape et -240 un défilement vers le bas en deux étapes. Sous MacOS, on aurait obtenu les valeurs 1 et -2 dans cet exemple. Pour le support de la molette sous Linux, voir les note sur l'événement de type Button dans “Event types”.
   * - ``height`` 
     - Si l'événement est du type ``Configure``, cet attribut porte la nouvelle hauteur du widget en pixels.
   * - ``keycode`` 
     - Pour un événement de type ``KeyPress`` ou ``KeyRelease``, cet attribut contient le code de touche. Cependant, cet entier n'identifie pas quel caractère de la touche a été produit, ainsi "x" ou "X" ne se différencient pas leur code de touche. Pour des valeurs possibles de cet attribut, voir “Key names”.
   * - ``keysym`` 
     - Pour un événement de type ``KeyPress`` ou ``KeyRelease`` impliquant une touche spéciale, cet attribut porte le nom de touche, par exemple 'Prior' pour la touche PageUp. Voir “Key names” pour une liste complète des nom de touches.
   * - ``keysym_num`` 
     - Pour un événement de type ``KeyPress`` ou ``KeyRelease``, cet attribut est une version numérique de l'attribut ``keysym``. Pour une touche régulière qui produit un seul caractère, cet attribut prend pour valeur le code ASCII du caractère. Pour des touches spéciales, référez-vous à “Key names”.
   * - ``num`` 
     - Si l'événement est associé à un bouton de la souris, cet attribut porte la valeur entière qui indique le numéro du bouton (1, 2 ou 3). Pour le support de la molette sous linux, lier les événements ``Button-4`` et ``Button-5``; lorsque la molette de la souris tourne vers l'avant, cet attribut prend la valeur 4, il prend la valeur 5 dans l'autre sens.
   * - ``serial`` 
     - Un entier qui est incrémenté à chaque fois que le serveur répond à une requête du client. Vous pouvez utiliser cet attribut pour découvrir la séquence temporelle des événements: ceux qui ont eu lieu plus tôt ont une valeur plus petite.
   * - ``state`` 
     - Un entier qui décrit l'état de toutes les touches modificatrice. Reportez-vous à la table des masques des modificateurs pour l'interprétation de cette valeur.
   * - ``time`` 
     - Cet attribut porte un entier qui n'a pas de signification dans l'absolu, mais qui est incrémenté chaque milliseconde. Cela permet à votre application de déterminer, par exemple, le temps écoulé entre deux clic souris.
   * - ``type`` 
     - Un code numérique qui décrit le type de l'événement. Pour l'interprétation de ce code, reportez-vous à “Event types”.
   * - ``widget`` 
     - Porte toujours la référence du widget qui a causé l'événement. Par exemple, si l'événement était un clic souris sur un canevas, cette attricut serait ce canevas.
   * - ``width`` 
     - Si l'événement était du type ``Configure``, cet attribut est la nouvelle largeur du widget en pixels.
   * - ``x`` 
     - L'abscisse de la souris en pixels au moment de l'événement. Elle est relative au coin supérieur gauche du widget sur lequel se trouve la souris.
   * - ``y`` 
     - Similaire à ``x`` mais dans la direction verticale.
   * - ``x_root`` 
     - L'abscisse de la souris au moment de où survient l'événement, relativement au coin supérieur gauche de l'écran.
   * - ``y_root`` 
     - Similaire à ``x_root`` mais dans la direction verticale.

Utilisez ces masques pour tester les bits de la valeur de l'attribut ``state`` pour savoir quel(s) touche(s) modificatrice(s) et/ou bouton(s) ont été utilisé(s) pendant l'événement.

.. list-table::
   :widths: 10 30
   :header-rows: 1

   * - Masque
     - Modificateur
   * - `0x0001` 
     - Maj.
   * - `0x0002` 
     - Verr Maj.
   * - `0x0004` 
     - Control.
   * - `0x0008` 
     - Touche Alt de gauche.
   * - `0x0010` 
     - Verr Num.
   * - `0x0080` 
     - Touche Alt de droite.
   * - `0x0100` 
     - Bouton 1 de la souris.
   * - `0x0200` 
     - Bouton 2 de la souris.
   * - `0x0400` 
     - Bouton 3 de la souris.

Voici un exemple de gestionnaire d'événement. Plus haut, “Levels of binding”, vous trouverez un exemple qui vous montre commment lié l'appui sur le bouton central de la souris à un gestionnaire nommé dessineDisqueOrangeabove. Voici ce gestionnaire:

.. code-block:: python

    def dessineDisqueOrange(evt):
        '''Dessine un disque orange là où se trouve la souris
        '''
        r = 5   # Son rayon
        can.create_oval(event.x-r, event.y-r,
            event.x+r, event.y+r, fill='orange')

Lorsque ce gestionnaire est appelé, la position courante de la souris est *(event.x, event.y)*. La méthode ``create_oval()`` dessine un cercle dont la boîte englobante est un carré centré sur cette position et dont les côtés mesure 2*r.

Truc pour des arguments en plus
===============================

Parfois, vous souhaiterez passer d'autres arguments à un gestionnaire (en plus de l'objet ``Event``)

Voici un exemple. Supposez que votre application comporte un tableau de cases à cocher dont les widget sont mémorisés dans une liste ``ccList``, indexée par le numéro de la case à cocher situé dans ``range(10)``.

Supposer en outre que vous souhaitiez n'écrire qu'un gestionnaire ``ccGest`` pour l'événement ``'<Button-1>'`` sur l'une de ces 10 cases. Votre gestionnaire peut connaître la case sur laquelle a eu lieu le clic en utilisant l'attribut ``widget`` de l'objet ``Event``, mais comment faire pour retrouver son index dans la liste ``ccList`` ?

Il serait agréable d'écrire notre gestionnaire avec un argument supplémentaire pour le numéro de la case à cocher, quelquechose comme:

.. code-block:: python

    def ccGest(evt, ccNb):

Mais un gestionnaire d'événement ne reçoit qu'un argument, l'objet de type ``Event``. Il n'est donc pas possible d'utiliser la fonction ci-dessus qui comporte un argument de trop.

Heureusement, il est possible d'exploiter les valeurs par défaut des fonctions pour parvenir à l'objectif. Observer le code suivant:

.. code-block:: python

     ccListe = [] 
     def creerWidgets():
        #...
        for i in range(10):
            cc = Checkbutton(root, ...)
            ccList.append(cb)
            cc.grid(row=1, column=i)
            def gest(evt, i=i):   1
                return ccGest(evt, i)
            cc.bind('<Button-1>', gest)
        #...
    def ccGest(evt, ccNb):
        #...

Ces lignes définissent un gestionnaire, ``gest()`` qui attend deux arguments. Le premier est l'objet de type ``Event`` habituel et le second a une valeur par défaut qui est exactement celle que nous avons besoin de connaître. Il suffit ensuite de définir le gestionnaire d'événement «réel», ``ccGest()`` pour atteindre le but que nous nous étions fixés.

Cette technique peut être étendue pour fournir autant d'arguments que souhaité à un gestionnaire d'événements.

Événements virtuels
===================

Vous pouvez créer vos propres genres d'événements appelés «événements virtuels». Vous pouvez leur donner le nom que vous souhaitez du moment qu'il est entouré par des doubles paires de chevrons <<…>>.
Par exemple, supposez que vous vouliez créer un nouvel événement appelé <<panic>>, qui est déclenché pour le bouton 3 de la souris ou par la touche Pause. Pour créer cet événement, appeler cette méthode sur un widget ``w`` arbitraire::

    w.event_add('<<panic>>', '<Button-3>', '<KeyPress-Pause>')

Vous pouvez alors utiliser ``'<<panic>>'`` dans n'importe quel séquence d'événement. Par exemple::

    w.bind('<<panic>>', g)

L'appui sur le bouton 3 de la souris ou sur la touche pause dans le widget ``w`` déclenchera le gestionnaire ``g``.

Voir .event_add(), .event_delete(), and .event_info(),  “Universal widget methods” pour plus d'informations sur la création et la gestion des événements virtuels.
