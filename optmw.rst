.. _OPTIONMENU:

*********************
Les options d'un menu ``OptionMenu``
*********************

 Le but de ce widget est d'offrir un ensemble fixe de choix à l'utilisateur dans un menu déroulant.

Les illustrations ci-dessus montrent un OptionMenu dans deux états. L'exemple de gauche montre le widget dans sa forme initiale. L'exemple de droite montre à quoi il ressemble lorsqu'avec la souris on a cliqué dessus et qu'on a choisi 'boat'.

Pour créer un nouveau widget OptionMenu en tant qu'enfant d'une fenêtre ou un cadre nommé parent:

.. py:class:: OptionMenu(parent, variable, choix1, choix2, ...)

        Le constructeur renvoie le nouveau widget OptionMenu. La variable est une instance de la classe StringVar (voir la section 52, «Les variables de contrôle: les valeurs derrière les widgets") qui est associée au widget, et les arguments restants sont les choix à afficher dans le widget sous forme de chaînes.

        L'illustration ci-dessus a été créée avec cet extrait de code
        
        .. code-block:: python

                optionList = ('train', 'plane', 'boat')
                self.v = tk.StringVar()
                self.v.set(optionList[0])
                self.om = tk.OptionMenu(self, self.v, \*optionList)


        Pour savoir quel choix est sélectionné dans un widget OptionMenu, la méthode .get() sur la variable de contrôle associée retournera ce choix comme une chaîne.
