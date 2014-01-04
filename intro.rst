.. _INTRO:

*********************************************************
Une interface graphique multiplateforme (GUI) pour Python
*********************************************************

Tkinter sert à réaliser des interfaces graphiques pour l'utilisateur (GUI) 
à l'aide d'un ensemble de composants graphiques (widgets).

Ce document s'inspire (et traduit) la référence suivante : lien à faire.

Nous commencerons par la part visible de tkinter en créant des composants 
graphiques (widgets) puis en les disposant sur l'écran. Ensuite, nous expliquerons
comment connecter cette «façade graphique» de l'application à la logique qui se trouve
derrière.

Un exemple simple
=================

Voici un programme «tkinter» minimal qui contient un seul bouton «Quitter»::

    # Chargement du module tkinter
    from tkinter import * # pour Python2 ce serait Tkinter
    
    # Construction de la fenêtre principale «root»
    root = Tk()
    root.title('Simple exemple')
    # Construction d'un simple bouton
    qb = Button(root, text='Quitter', command=root.quit)
    
    # Placement du bouton dans «root»
    qb.pack()
    
    # Lancement de la «boucle principale»
    root.mainloop()                          

La dernière instruction ``root.mainloop()`` permet à l'application
de recevoir des informations de la souris et du clavier (entre autres).

Définitions
===========

Avant d'entrer dans le coeur du sujet, voici quelques termes utilisés 
fréquemment ensuite:

.. glossary::

    **Fenêtre** (*window*)
        Ce terme prend des sens différents suivant le contexte, mais
        en général il renvoie à une aire rectangulaire quelque part sur votre écran.

    **Fenêtre mère** (*top-level window*)
        Une fenêtre qui existe de manière indépendante sur l'écran.
        Elle sera décorée conformément à votre gestionnaire de bureau et munie des petits boutons habituels.
        On peut la déplacer et généralement la redimensionner même si votre application peut limiter cela.

    **Composant graphique** (*widget*)
        terme générique désignant tous les éléments qui forment l'interface
        graphique utilisateur. Par exemple, les boutons (*buttons*), les boutons «radio» (*radiobuttons*), les champs de saisie (*entry*),
        les étiquettes (*labels*), les cadres (*frames*) ...

    **Cadre** (*frame*)
        Dans tkinter, c'est l'unité de base pour l'organisation d'une mise en forme complexe.
        Un cadre est une zone rectangulaire qui peut contenir d'autres composants graphiques (*widgets*).

    **enfant, parent**
        Lorsqu'un composant graphique est créé, une relation parent/enfant est établie.
        Par exemple, si on place une étiquette (*label*) dans un cadre (*frame*), le cadre est le parent de l'étiquette.
