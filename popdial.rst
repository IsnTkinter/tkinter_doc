.. _DIALOGS:

**********************************
Fenêtres surgissantes de dialogues
**********************************

Tkinter fournit trois sous modules qui servent à créer des fenêtres surgissantes de dialogue avec l'utilisateur:

* ``tkinter.messagebox``: fourni un assortiment de fenêtres de dialogues courantes pour des tâches simples. 

*  ``tkinter.filedialog``: fenêtre de navigation dans le système de fichier.

*  “The tkColorChooser module”, allows the user to select a color.
    
Le sous-module ``messagebox``
=============================

Après avoir importer le sous-module (avec ``from tkinter.messagebox import *`` ou plus prudemment avec ``import tkinter.messagebox as mb``), vous pouvez créer simplement huit sortes de fenêtres pop-ups en appelant les fonctions données ci-après.

.. list-table::
   :widths: 50 50
   :header-rows: 0

   * - .. image:: img/messagedialog/askokcancel.png 
     - ``askokcancel(title, message, options)``
   * - .. image:: img/messagedialog/askquestion.png
     - ``askquestion(title, message, options)``
   * - .. image:: img/messagedialog/askretrycancel.png
     - ``askretrycancel(title, message, options)``
   * - .. image:: img/messagedialog/askyesno.png
     - ``askyesno(title, message, options)``
   * - .. image:: img/messagedialog/askyesnocancel.png
     - ``askyesnocancel(title, messages, options)``
   * - .. image:: img/messagedialog/showerror.png
     - ``showerror(title, message, options)``
   * - .. image:: img/messagedialog/showinfo.png
     - ``showinfo(title, message, options)``
   * - .. image:: img/messagedialog/showwarning.png
     - ``showwarning(title, message, options)``

Dans chaque cas,l'argument *title* est une chaîne à afficher sur le bord haut de la fenêtre surgissante et l'argument *message* est une chaîne qui sera affichée dans le corps de la fenêtre; vous pouvez mettre des sauts de lignes en utlilisant le caractère spécial ``'\n'``.

Les options sont:

``default``

    Sert à indiquer le bouton qui représente le choix par défaut. Si vous ne précisez pas cette option, le premier bouton sera celui du choix par défaut.Which button should be the default choice? If you do not specify this option, the first button (“OK”, “Yes”, or “Retry”) will be the default choice.

    Pour préciser un bouton par défaut, utilisez ``default=C``, où c est l'une des valeurs ``"cancel"``, ``"ignore"``, ``"ok"``, ``"no"``, ``"retry"`` ou ``"yes"``.

``icon``

    Sert à sélectionner l'icone qui sera affichée sur la fenêtre de dialogue. Les valeurs possibles sont ``error``, ``info``, ``question`` ou ``warning``.

``parent``

    Si vous ne configurez pas cette option, la fenêtre surgissante apparaîtra au-dessus de votre fenêtre principale. Pour la faire apparaître au-dessus d'une fenêtre arbitraire ``w``, utilisez ``parent=w``.

Chacune des fonctions ``ask...`` retourne une valeur qui dépend du bouton sur lequel l'utilisateur a cliqué afin de supprimer la fenêtre surgissante.

* ``askokcancel``, ``askretrycancel``, et ``askyesno`` retournent toutes un booléen: ``True`` si l'utilisateur a cliqué sur le bouton "Ok", "Oui" ou "Ré-essayer", ``False`` s'il a cliqué sur "Non" ou sur "Annuler".

* ``askyesnocancel`` retourne ``True``, ``False``, ou ``None`` selon que l'utilisateur a cliqué sur le bouton "Oui", "Non" ou "Annuler".

* ``askquestion`` retourne une chaîne ``'yes'`` pour "Oui", ou ``'no'`` pour "Non".
    
Le sous-module ``filedialog``
=============================

Le sous-module ``filedialog`` fournit des fenêtres surgissantes qui peuvent vous servir à donner la capacité à l'utilisateur de trouver un fichier existant ou de créer de nouveaux fichiers.

.. py:method:: askopenfilename(option=value, ...)

    Produit une fenêtre surgissante qui permet à l'utilisateur de sélectionner un fichier existant. Si l'utilisateur sélectionne un fichier qui n'existe pas, une popup apparaîtra indiquant que le fichier sélectionné n'existe pas.

.. py:method:: asksaveasfilename(option=value, ...)

    Produit une fenêtre surgissante qui permet à l'utilsateur de créer un nouveau fichier ou de remplacer un fichier qui existe déjà par un autre. Si l'utilisateur sélectionne un fichier qui existe déjà, une popup apparaît pour mettre en garde sur le fait que le fichier existe déjà et pour demander si l'utilisateur souhaite vraiment le remplacer.

Les options des deux fonctions sont les mêmes:

``defaultextension=s``

    L'extension du fichier par défaut, c'est à une chaîne qui commence par un point «.». Si l'utilisateur utilise un point dans le nom de fichier, cette option n'a pas d'effet. Autrement, l'extension donnée est concaténée au nom de fichier fournit par l'utilisateur.

    Par exemple, si vous utilisez defaultextension='.jpg' et que l'utilisateur saisi 'gojiro', le nom de fichier utilisé sera au final 'gojiro.jpg'.

``filetypes=[(label1, pattern1), (label2, pattern2), ...]``

    Une liste dont les éléments sont des 2-tuples qui contiennent des noms de type de fichier et des motifs de sélection qui serviront à sélectionner les fichiers qui apparaîtront dans le listing de la fenêtre surgissante. A list of two-element tuples containing file type names and patterns that will select what appears in the file listing. In the screen picture below, note the pull-down menu labeled “Files of type:”. The filetypes argument you supply will populate this pull-down list. Each pattern is a file type name (“PNG” in the example) and a pattern that selects files of a given type (“(\*.png)” in the example). 

``initialdir=D``

    Le chemin du dossier dont il faut afficher le contenu initialement. Le dossier par défaut est le dossier de travail actuel (celui qui contient le fichier du programme).

``initialfile=F``

    Le nom de fichier à afficher initialement dans le champ "Nom de fichier:".

``parent=W``

    Pour faire en sorte que la fenêtre surgissante apparaîsse au-dessus d'une fenêtre W, utilisez parent=w. Par défaut, la fenêtre surgissante apparaît au-dessus de la fenêtre principale de votre application.

``title=T``

    Sert à donner un titre à la fenêtre de dialogue.

Si l'utilisateur sélectionne un fichier, la valeur de retour est le chemin absolue du fichier sélectionné. Si l'utilisateur utilise le bouton "Annuler", la fonction retourne une chaîne vide.

Here is an example:

The tkColorChooser module
=========================

To give your application's user a popup they can use to select a color, import the tkColorChooser module and call this function:

.. code-block:: python

        result = tkColorChooser.askcolor(color, option=value, ...)

Arguments are:

``color``

    The initial color to be displayed. The default initial color is a light gray. 

``title=text``

    The specified text appears in the pop-up window's title area. The default title is “Color”. 

``parent=W``

    Make the popup appear over window W. The default behavior is that it appears over your root window. 

If the user clicks the OK button on the pop-up, the returned value will be a tuple `(triple, color)`, where triple is a tuple (R, G, B) containing red, green, and blue values in the range [0,255] respectively, and color is the selected color as a regular Tkinter color object.

If the users clicks Cancel, this function will return (None, None).

Here's what the popup looks like on the author's system:

