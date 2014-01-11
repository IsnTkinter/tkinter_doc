.. _FOCUS:

*****************************
Focus: routing keyboard input
*****************************

Dire qu'un widget a le focus signifie que les saisis au clavier sont actuellement dirigées vers ce widget.

* Par «traversée du focus», nous entendons la séquence des widgets qui sont visités (qui obtiennent le focus) lorsque l'utilisateur navigue de widget en widget en utilisant la touche Tab. Voir ci-dessous pour les règles qui régissent la traversée du focus.

* Vous pouvez déplacer le focus dans l'autre sens en utilisant la combinaison Maj+Tab.

* Les widget ``Entry`` et ``Text`` sont conçus pour accepter les entrées au clavier, et si l'un de ces widges possède le focus, chaque caractère que vous tapez seront ajoutés au texte. Les caractères d'édition habituels comme ← et →  auront l'effet habituels.

* Comme un widget ``Text`` peut contenir des tabulations, vous devez utiliser la combinaison Control+Tab pour déplacer le focus au-delà d'un tel widget.

* La plupart des autres type de widgets seront normalement visités par la traversées du focus, et lorsqu'ils ont le focus:

  + Les ``Button`` peuvent être «cliqués» en utilisant la barre d'espace.

  + Les ``Checkbutton`` peuvent être basculés entre coché et non coché en utilisant la barre d'espace.

  + Dans les ``Listbox``, les touches ↑ et ↓  servent à faire défiler une ligne vers le bas ou vers le haut; les touches PageUp et PageDown font défiler d'une «page»; et la barre espace sélectionne la ligne courante ou la dé-sélection si elle était déjà sélectionnée.

  + Vous pouvez cocher un bouton radio en appuyant sur la barre espace.

  + Un ``Scale`` horizontal répond aux touches ←  et → , et s'ils sont orienté verticalement, ils répondent aux touches ↑ et ↓.

  + Pour un widget ``Scrollbar``, les touches PageUp et PageDown déplace la barre de défilement d'une page. Les touches ↑ et ↓ déplace les barres de défilement verticale d'une unité et les touches ←  et →  auront un effet similaire avec une bare de défilement horizontale.

* La plupart des widgets disposent d'une ligne de contour qui indique à l'utilisateur le composant graphique qui possède actuellement le focus. Il s'agit, normalement, d'un cadre fin noir situé juste autour du bord du widget (s'il en possède un). Pour les widgets qui n'ont pas par défaut de mise en valeur du focus (précisément, les cadres, les étiquettes et les menus), vous pouvez donner une valeur non nulle à l'option **highlightthickness** afin de rendre la mise en valeur du focus visible.

* Vous pouvez aussi changer la couleur de la ligne de mise en valeur de focus en utilisant l'option **highlightcolor**. 

* Les widgets qui appartiennent au classes ``Frame``, ``Label``, et ``Menu`` ne sont pas visité par la traversée du focus (par défaut). Vous pouvez cependant mettre leur option **takefocus** à 1 pour les rendre accessible à la traversée du focus. Vous pouvez aussi sortir n'importe quel widget de cette traversée en donnant la valeur 0 à son option **takefocus**.

L'ordre dans lequel la touche Tab visite les widgets est:

* Pour les enfant d'un même parent, le focus suit l'ordre dans lequel les widgets ont été créés.

* Pour les widgets qui peuvent en contenir d'autres, comme les cadres Frame, le conteneur (parent) est visité en premier (sauf si son option **takefocus** est à 0), puis il visite les widgets enfants, récursivement, dans l'ordre où ils ont été créés.

En résumé: pour contrôler l'ordre de la traversée du focus de vos widgets, créés les dans cet ordre. Si vous ne souhaitez pas qu'un widget soit visité, positionnez son option **takefocus** à 0, et pour ceux qui ne sont pas visités par défaut, positionnez cette option à 1 si vous souhaitez qu'ils le soient.

La description précédente décrit le fonctionnement par défaut système de focus pour la saisie clavier de tkinter. Il y a une autre façon, complètement différent, de le gérer en laissant aller le focus là où la souris va. Dans “Universal widget methods”, référez-vous à la méthode ``.tk_focusFollowsMouse()``. 

Vous pouvez aussi ajouter, modifier, supprimer des comportements relatifs à l'utilisation du clavier ou de la souris pour chacun de vos widgets en utilisant des liaisons par événements. Voir “Events” pour en savoir plus.
