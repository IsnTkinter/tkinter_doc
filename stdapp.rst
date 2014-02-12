.. _APPEARANCE:

******************************************************
Normaliser l'apparence: la base de données des options
******************************************************

Il est facile d'appliquer des couleurs, des polices de caractères et tout un tas d'options aux widgets lorsque vous les créez. Cependant,

* Si vous souhaitez que plusieurs widgets aient la même couleur de fond ou la même police de caractères, il est laborieux d'indiquer à chaque fois la même option pour chaque widget, et

* il est sympathique de laisser l'utilisateur faire ses propres choix pour ces options, lesquelles surchargeront les valeurs choisies par défaut pour l'application.

En conséquence, Tkinter utilise l'idée de base de données des options pour régler les valeurs d'options qui seront utilisées par défaut.

* Votre application peut utiliser un fichier (comme le fichier standard .Xdefaults utilisé par le système X Window) qui contient les préférences de l'utilisateur. Vous pouvez configurer votre application pour qu'elle lise ce fichier et qu'elle indique à Tkinter d'utiliser ces valeurs par défaut. Voir la section ci-dessous pour le format d'un tel fichier et aussi la méthode option_readfile() dans  “Universal widget methods”.

* Votre application peut aussi préciser de nombreuses valeurs d'options pour un ou plusieurs types de widgets en utilisant la méthode option_add(); voir “Universal widget methods”. 

Avant d'expliquer la manière de configurer ces options, réfléchissons au problème de la personnalisation des interfaces graphiques en général. Nous pourrions donner à chaque widget de l'application un nom et demander à l'utilisateur de préciser les options pour chaque widget nommé. Mais cela serait très fastidieux et rendrait difficile la tâche de reconfiguration de l'application dans le cas où le concepteur ajouterait de nouveaux widgets: l'utilisateur devrait alors configurer complètement chaque nouveau composant.

Pour ces raisons, la base de données des options permet au programmeur et à l'utilisateur d'indiquer des schémas généraux pour décrire les widgets à configurer.

Ces schémas opèrent sur les noms des widgets, mais les widgets sont nommés en utilisant deux schémas de nommage parallèles:

a) Chaque widget possède un nom de classe. Par défaut, ce nom de classe est le même que celui du constructeur: ``'Button'`` pour les boutons, ``'Frame'`` pour les cadres et ainsi de suite. Cependant, vous pouvez créer de nouvelles classes de widgets, ordinairement en héritant de la classe générale ``'Frame'`` et en donnant un nom à votre classe dérivée. Voir “How to name a widget class” pour des détails supplémentaires.

b) Vous pouvez aussi donner à chaque widget un nom d'instance. Par défaut, le nom d'un widget est un nombre sans signification particulière (voir “Window names”). Cependant, comme pour les classes de widget, vous pouvez donner un nom à n'importe quel widget. Voir “How to name a widget instance” pour plus de détails.

Ainsi, chaque widget de chaque application possède deux hiérarchies de noms: la hiérarchie des noms de classes et la hiérarchie des nom d'instances. Par exemple, un bouton qui fait partie d'un widget ``Text`` lui-même inclus dans un widget ``Frame`` (un cadre) aura comme nom hiérachique de classe ``Frame.Text.Button``. Il peut aussi avoir un nom hiérachique d'instance, quelquechose comme ``.mainFrame.messageText.panicButton`` si vous avez choisis ces noms pour chaque instance. Le point initial d'un tel nom se rapporte à la fenêtre principale (racine); voir “Window names” pour plus d'informations sur les chemins de nommage des fenêtres. 

Le mécanisme de la base de données des options peut se servir de ces deux systèmes de nommage (celui des classes ou celui des instances) pour définir les options. Vous pouvez ainsi appliquer un jeu d'options à une classe entière de widgets (par exemple, tous les boutons auront une couleur d'arrière plan bleu) ou à des instances spécifiques (par exemple, le bouton «panique» aura un texte en rouge). 

Nous commencerons par décrire les moyens de donner un nom aux classes puis aux instances. Ensuite, nous décrirons le fonctionnement de la base de données des options dans “Resource specification lines”.

Donner un nom à une classe de widget
====================================

Par exemple, supposons que ``Jukebox`` soit une nouvelle classe de widget que vous avez créé. Vous l'aurez probablement dérivé de la classe ``Frame`` de telle sorte que, pour Tkinter, son comportement général soit celui d'un cadre, dans lequel vous pouvez donc insérer et arranger d'autres widgets comme des étiquettes, des boîtes de saisie et des boutons.

Vous configurez le nom de cette nouvelle classe de widget en l'indiquant à l'option **class_** du constructeur parent (celui de ``Frame`` dans cette exemple). Voici un fragment de code pour illuster la définition de cette nouvelle classe::

    class Jukebox(Frame):
        def _init_(self, parent):
            '''Le constructeur de la classe Jukebox'''
            # on appelle le constructeur de la classe Frame dont dérive celle-ci
            Frame._init_(self, parent, class_='Jukebox')
            # on appelle une méthode privée pour la construction des autres widgets
            # qui composent le Jukebox
            self._creerWidgets()
            ...

Donner un nom d'instance à un widget particulier
================================================

Pour donner un nom d'instance à un widget particulier de votre application, configurer son option **name** avec la chaîne qui contient le nom voulu.

Voici un exemple d'une instance nommée. Supposons que vous ayez créé plusieurs boutons pour l'application et que vous souhaitiez que l'un des boutons reçoive le nom d'instance ``panicButton``. L'appel du constructeur pour cet instance devrait ressembler à cela::

    panic = Button(root, name='panicButton', text='Panique', ...)
    
Chaque ligne d'un fichier d'options précise la valeur d'une ou de plusieurs options d'une ou de plusieurs applications. Une telle ligne est de l'une des formes suivantes::

    app option-pattern: valeur
    option-pattern: valeur

La première forme sert à configurer une ou plusieurs options pour une application particulière dont le nom est *app*; la deuxième forme configure une ou plusieurs options de toutes les applications qui utiliseront le fichier.

Par exemple, si votre application s'appelle *pacman*, une ligne de la forme::

    pacman*background: LimeGreen

toutes les options **background** (couleur d'arrière plan) prendrons la valeur par défaut vert citron ('LimeGreen'). (Utilisez l'option -name sur la ligne de commande au moment de lancer votre application pour lui donner le nom *pacman*.)

La partie *option-pattern* possède la syntaxe suivante::

    {{*|.}name}...option

Ce qui veut dire que chaque *option-pattern* est une liste de 0 ou plusieurs noms, chacun desquels est précédé par une astérisk * ou par un point. Le dernier nom de la série est le nom de l'option que vous souhaitez configurer. Les autres noms peuvent être:

* Le nom d'une classe de widget (première lettre en majuscule), ou

* le nom d'une instance (en minuscule). 

La manière dont le schéma d'option fonctionne un est un peu compliqué. Commençons avec un exemple simple::

    *font: times 24

Cette ligne précise que l'option de police de caractères *font* sera par défaut une fonte Times de 24 point. Le symbole * signifie: appliquer cette valeur à toutes les options **font** de tous les widgets de toutes les applications. Comparez avec cet exemple::

    *Listbox.font: lucidatypewriter 14

Ici, la règle vaut pour l'option **font** de tous les widgets de classe ``Listbox`` de toutes les applications.

Encore un exemple. Supposez que votre application *pacman* possède des instances de widget de classe ``Jukebox``. Si vous souhaitiez régler la couleur d'arrière plan de tous les widgets situés dans un widget arbitraire de classe ``Jukebox``, vous pourriez préciser cela dans votre fichier d'option avec une ligne comme celle-ci::

    pacman*Jukebox*background: PapayaWhip

L'astérisk * situé entre ``Jukebox`` et l'option **background** indique que la valeur (vert papaye) de l'option **background** doit être appliquée par défaut à tous les composants de tous les ``Jukebox`` de l'application *pacman*. Comparez encore avec cette ligne::

    pacman*Jukebox.background: NavajoWhite

Cette règle ne s'appliquera qu'au cadre (``Frame``) dont dérive directement le widget ``Jukebox``. Le point qui sépare ``Jukebox`` et **background** précise que la règle ne s'applique pas aux enfants du jukebox.

Dans la section suivante, nous parlerons de la manière précise avec laquelle Tkinter détermine quelle valeur d'option utiliser lorsqu'il rencontre plusieurs lignes de spécifications qui pourraient être appliquées.

Priorités des règles de spécifications
======================================

Lorsque vous créez un widget, que vous ne précisez pas les valeurs de certaines options et que plusieurs règles s'appliquent pour une option donnée, la règle la plus spécifique s'applique.

Par exemple, supposons que votre fichier d'options aient les deux lignes suivantes::

    *background: LimeGreen
    *Listbox*background: FloralWhite

Les deux lignes s'appliquent à l'option background d'un widget Listbox, mais la deuxième est plus spécifique, c'est donc elle qui sera appliquée.

En général, les noms d'une ligne de spécification forment une séquence *n1, n2, n3, ..., o* où chaque *ni* est un nom de classe ou d'instance. Les noms de classes sont ordonnés du plus haut niveau (hiérarchique) au plus bas et o est le nom d'une option.

Cependant, lorsque Tkinter est en train de créer un widget, il ne dispose que du nom de classe et dun nom d'instance de ce widget.

Voici les règles de priorité pour appliquer les spécifications:

1) Le nom d'une option doit correspondre à la partie notée o du schéma d'option. Par exemple, si la règle est:

   ``pacman*indicatoron: 0``

   la correspondance n'aura lieu que pour l'option **indicatoron**.

2) L'opérateur point (.) est plus spécifique que l'opérateur astérisk (*). Par exemple, une ligne comme ``*Button.font`` est plus spécifique qu'une ligne ``*Button*font``.

3) Les références à des instances sont plus spécifiques que les référence à des classes. Par exemple, si vous avez un bouton dont le nom d'instance est *panicButton*, la règle ``*panicButton*font`` est plus spécifique que la règle ``*Button*font``.

4) Plus une règle a de niveaux plus elle est spécifique. Par exemple, la règle ``*Button*font`` est plus spécifique que la règle ``*font``.

5) Si deux règles ont le même nombre de niveaux, les noms qui apparaîssent plus tôt dans la liste sont plus spécifiques que ceux qui apparaîssent plus tard. Par exemple, la règle ``xparrot*font`` est plus spécifique que la règle ``*Button*font``. 
