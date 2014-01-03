.. _Label:

************************
Les étiquettes ``Label``
************************

Label widgets can display one or more lines of text in the same style, or a bitmap or image. 
To create a label widget in a root window or frame parent:

.. py:class:: Label(parent, option, ...)

   The constructor returns the new Label widget. Options include:


   :arg activebackground:
       Background color to be displayed when the mouse is over the widget.
   
   :arg activeforeground:
       Foreground color to be displayed when the mouse is over the widget.
   :arg anchor:
       This options controls where the text is positioned if the widget has more space than the text needs. The default is anchor=tk.CENTER, which centers the text in the available space. For other values, Voir :ref:`ancrage`.
       For example, if you use anchor=tk.NW, the text would be positioned in the upper left-hand corner of the available space.
   :arg background: 
      or bg	The background color of the label area. Voir :ref:`couleurs`.
   :arg bitmap:
      Set this option equal to a bitmap or image object and the label will display that graphic. Voir :ref:`bitmaps`.
      and Voir :ref:`images`.
   :arg borderwidth:
      or border .Width of the border around the label; Voir :ref:`dimensions`.
      The default value is two pixels.
   :arg compound:
      If you would like the Label widget to display both text and a graphic (either a bitmap or an image), the compound option specifies the relative orientation of the graphic relative to the text. Values may be any of tk.LEFT, tk.RIGHT, tk.CENTER, tk.BOTTOM, or tk.TOP. For example, if you specify compound=BOTTOM, the graphic will be displayed below the text.
   :arg cursor:
      Cursor that appears when the mouse is over this label. Voir :ref:`pointeurs`.
   :arg disabledforeground:
      The foreground color to be displayed when the widget's state is tk.DISABLED.
   :arg font:
      If you are displaying text in this label (with the text or textvariable option, the font option specifies in what font that text will be displayed. Voir :ref:`polices`.
   :arg foreground:
      or fg ; If you are displaying text or a bitmap in this label, this option specifies the color of the text. If you are displaying a bitmap, this is the color that will appear at the position of the 1-bits in the bitmap. Voir :ref:`couleurs`.
   :arg height:	
      Height of the label in lines (not pixels!). If this option is not set, the label will be sized to fit its contents.
   :arg highlightbackground:
      Color of the focus highlight when the widget does not have focus.
   :arg highlightcolor:
      The color of the focus highlight when the widget has focus.
   :arg highlightthickness:
      Thickness of the focus highlight.
   :arg image:
      To display a static image in the label widget, set this option to an image object. Voir :ref:`images`.
   :arg justify:
      Specifies how multiple lines of text will be aligned with respect to each other: tk.LEFT for flush left, tk.CENTER for centered (the default), or tk.RIGHT for right-justified.
   :arg padx:
      Extra space added to the left and right of the text within the widget. Default is 1.
   :arg pady:	
      Extra space added above and below the text within the widget. Default is 1.
   :arg relief:
      Specifies the appearance of a decorative border around the label. The default is tk.FLAT; for other values, Voir :ref:`reliefs`.
   :arg state:
      By default, an Entry widget is in the tk.NORMAL state. Set this option to tk.DISABLED to make it unresponsive to mouse events. The state will be tk.ACTIVE when the mouse is over the widget.
   :arg takefocus:
      Normally, focus does not cycle through Label widgets; see Section 53, “Focus: routing keyboard input”. If you want this widget to be visited by the focus, set takefocus=1.
   :arg text:
      To display one or more lines of text in a label widget, set this option to a string containing the text. Internal newlines ('\n') will force a line break.
   :arg textvariable:
      To slave the text displayed in a label widget to a control variable of class StringVar, set this option to that variable. SeeSection 52, “Control variables: the values behind the widgets”.
   :arg underline:
      You can display an underline (_) below the nth letter of the text, counting from 0, by setting this option to n. The default is underline=-1, which means no underlining.
   :arg width:
      Width of the label in characters (not pixels!). If this option is not set, the label will be sized to fit its contents.
   :arg wraplength:
      You can limit the number of characters in each line by setting this option to the desired number. The default value, 0, means that lines will be broken only at newlines.


There are no special methods for label widgets other than the common ones (see Section 26, “Universal widget methods”). 
