.. _CONNECTING:

*******************************************************
Connecter la logique de votre applications aux widgets
*******************************************************

Les sections précédentes vous ont appris à placer et à configurer les widgets qui forment l'interface graphique de votre application.

Nous allons à présent aborder le problème de la gestion des actions de l'utilisateur sur l'interface ainsi créée: Il s'agit de connecter la logique de votre application avec les actions de l'utilisateur sur l'interface graphique.

* Pour rendre votre application réactive à des événements comme l'appui sur un bouton de la souris ou sur une touche du clavier, il y a deux méthodes:

  + Certains widgets commes les boutons - ``Button`` - possèdent une option **command** qui vous permet de préciser une procédure (fonction sans arguments), appelé gestionnaire ou *handler*, qui sera appelé à chaque fois que l'utilisateur clique dessus.

    La séquence des événements pour utiliser un widget ``Button`` est très précise: l'utilisateur doit déplacer son pointeur de souris au-dessus du widget sans appuyer sur le bouton gauche de la souris, puis il doit appuyer sur ce bouton gauche et, ensuite, le relâcher tandis que le pointeur de la souris est toujours au-dessus du widget. Aucune autre séquence d'événements ne produira "l'enfoncement" du widget Button.

  + Il y a un mécanisme bien plus général qui permet de rendre votre application réactive à toute sorte d'action de la part de l'utilisateur: l'appui ou le relâchement d'une touche arbitraire du clavier ou d'un bouton de la souris; le déplacement de la souris à l'intérieur, autour, ou en dehors d'un widget; et beaucoup d'autres actions ou événements. Comme avec un gestionnaire associé à **command**, dans ce mécanisme vous écrivez une fonction de type gestionnaire (*handler*) qui sera appelée à chaque fois que certains types d'événements se produisent. Ce mécanisme est décrit de manière détaillé dans :ref:`EVENTS`.

* La plupart des widget attendent que vous leur fournissiez une ou plusieurs variables de contrôle; ce sont des objets spéciaux qui servent à connecter certains widgets entre eux et avec votre programme, cela afin que vous puissiez lire et modifier les propriétés de ces widgets. Voir :ref:`CTRLVARIABLES`.
