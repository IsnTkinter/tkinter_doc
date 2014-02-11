.. _DIALOGS:

*********************
Fenêtres de dialogues
*********************

Tkinter fournit trois sous modules qui servent à créer des fenêtres préconfigurées, dites fenêtres de dialogue. Ces fenêtres sont utiles pour transmettre une information à l'utilisateur ou pour lui demander quelquechose. Ces sont des fenêtres popups ou «surgissantes» car leur durée de vie est limitée: elles sont détruites dès que l'utilisateur déclare avoir pris en compte l'information transmise ou lorsqu'il répond à la question posée (généralement en cliquant sur un bouton).

* ``tkinter.messagebox``: fournit un assortiment de fenêtres de dialogue pour des tâches simples (avertir, demander quelquechose).

* ``tkinter.filedialog``: fenêtre de dialogue pour récupérer le nom d'un fichier.

* ``tkinter.colorchooser``: fenêtre de dialogue pour récupérer une couleur.

Pour utiliser un sous-module, il faut l'importer. Par exemple, si notre application propose d'ouvrir un fichier, on utilisera sans doute une fenêtre de dialogue du sous-module *tkinter.filedialog*. L'entête de notre programme ressemblera alors à::

        from tkinter import *
        from tkinter.filedialog import *
        ...
    
Le sous-module ``messagebox``
=============================

Après avoir importé le sous-module ``messagebox``, vous pouvez créer simplement huit sortes de fenêtres popups en appelant les fonctions données ci-après.

.. list-table::
   :widths: 50 50
   :header-rows: 0

   * - .. image:: img/messagedialog/askokcancel.png 
     - .. py:function:: askokcancel(title, message, option=valeur, ...)
   * - .. image:: img/messagedialog/askquestion.png
     - .. py:function:: askquestion(title, message, option=valeur, ...)
   * - .. image:: img/messagedialog/askretrycancel.png
     - .. py:function:: askretrycancel(title, message, option=valeur, ...)
   * - .. image:: img/messagedialog/askyesno.png
     - .. py:function:: askyesno(title, message, option=valeur, ...)
   * - .. image:: img/messagedialog/askyesnocancel.png
     - .. py:function:: askyesnocancel(title, messages, option=valeur, ...)
   * - .. image:: img/messagedialog/showerror.png
     - .. py:function:: showerror(title, message, option=valeur, ...)
   * - .. image:: img/messagedialog/showinfo.png
     - .. py:function:: showinfo(title, message, option=valeur, ...)
   * - .. image:: img/messagedialog/showwarning.png
     - .. py:function:: showwarning(title, message, option=valeur, ...)

Dans chaque cas, l'argument *title* permet de donner un titre à la fenêtre de dialogue et l'argument *message* est une chaîne qui sera affichée dans le corps de la fenêtre; vous pouvez mettre des sauts de lignes en utlilisant le caractère spécial ``'\n'``.

Les options sont:

**default**

    Sert à indiquer le bouton qui représente le choix par défaut. Si vous ne précisez pas cette option, le premier bouton sera celui du choix par défaut.Which button should be the default choice? If you do not specify this option, the first button (“OK”, “Yes”, or “Retry”) will be the default choice.

    Pour préciser un bouton par défaut, utilisez ``default=C``, où c est l'une des valeurs ``"cancel"``, ``"ignore"``, ``"ok"``, ``"no"``, ``"retry"`` ou ``"yes"``.

**icon**

    Sert à sélectionner l'icone qui sera affichée sur la fenêtre de dialogue. Les valeurs possibles sont ``error``, ``info``, ``question`` ou ``warning``.

**parent**

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

**defaultextension**

    L'extension du fichier par défaut, c'est à une chaîne qui commence par un point «.». Si l'utilisateur utilise un point dans le nom de fichier, cette option n'a pas d'effet. Autrement, l'extension donnée est concaténée au nom de fichier fournit par l'utilisateur.

    Par exemple, si vous utilisez defaultextension='.jpg' et que l'utilisateur saisi 'gojiro', le nom de fichier utilisé sera au final 'gojiro.jpg'.

**filetypes**

    Une liste de la forme ``[(etiquette1, motif1), (etiquette2, motif2), ...]`` dont les éléments sont des 2-tuples qui contiennent des noms de type de fichier et des motifs de sélection qui serviront à sélectionner les fichiers qui apparaîtront dans le listing de la fenêtre surgissante. A list of two-element tuples containing file type names and patterns that will select what appears in the file listing. In the screen picture below, note the pull-down menu labeled “Files of type:”. The filetypes argument you supply will populate this pull-down list. Each pattern is a file type name (“PNG” in the example) and a pattern that selects files of a given type (“(\*.png)” in the example). 

**initialdir**

    Le chemin du dossier dont il faut afficher le contenu initialement. Le dossier par défaut est le dossier de travail actuel (celui qui contient le fichier du programme).

**initialfile**

    Le nom de fichier à afficher initialement dans le champ "Nom de fichier:".

**parent**

    Pour faire en sorte que la fenêtre surgissante apparaîsse au-dessus d'une fenêtre ``W`` , utilisez ``parent=w``. Par défaut, la fenêtre surgissante apparaît au-dessus de la fenêtre principale de votre application.

**title**

    Sert à donner un titre à la fenêtre de dialogue.

Si l'utilisateur sélectionne un fichier, la valeur de retour est le chemin absolue du fichier sélectionné. Si l'utilisateur utilise le bouton "Annuler", la fonction retourne une chaîne vide.

Here is an example:

Le sous-module ``colorchooser``
===============================

Pour fournir à l'utilisateur de votre application un moyen simple de sélectionner une couleur, importer le sous-module colorchooser et appeler cette fonction:

.. code-block:: python

        couleur = askcolor(couleur, option=valeur, ...)

Les arguments ou options sont:

**color**

    La couleur initale à afficher. Gris léger par défaut.

**title**

    Le titre de la fenêtre. "Couleur" par défaut.

**parent**

    Pour faire apparaître la popup au-dessus d'une fenêtre ``W``. Le comportement par défaut est de la faire apparaître au-dessus de la fenêtre principale du programme.

If the user clicks the OK button on the pop-up, the returned value will be a tuple `(triple, color)`, where triple is a tuple (R, G, B) containing red, green, and blue values in the range [0,255] respectively, and color is the selected color as a regular Tkinter color object.

If the users clicks Cancel, this function will return (None, None).

Here's what the popup looks like on the author's system:

