.. _LABELFRAME:

***********************************
Les cadres étiquetés ``LabelFrame``
***********************************

 The LabelFrame widget, like the Frame widget, is a spatial container—a rectangular area that can contain other widgets. However, unlike the Frame widget, the LabelFrame widget allows you to display a label as part of the border around the area.

Here is an example of a LabelFrame widget containing two Button widgets. Note that the label “Important controls” interrupts the border. This widget illustrates the default GROOVE relief (Voir :ref:`reliefs`).
and the default 'nw' label anchor, which positions the label at the left side of the top of the frame.

To create a new LabelFrame widget inside a root window or frame parent:

.. py:class:: LabelFrame(parent, option, ...)

        This constructor returns the new LabelFrame widget. Options:

        :arg bg: or background 
                The background color to be displayed inside the widget; Voir :ref:`couleurs`.
        :arg bd: or borderwidth 
                Width of the border drawn around the perimeter of the widget; Voir :ref:`dimensions`.
                The default value is two pixels.
        :arg cursor: 
                Selects the cursor that appears when the mouse is over the widget; Voir :ref:`pointeurs`.
        :arg fg: or foreground 
                Color to be used for the label text.
        :arg height: 
                The vertical dimension of the new frame. This will be ignored unless you also call .grid_propagate(0) on the frame; Voir :ref:`autres-meth-grille`.
        :arg highlightbackground: 
                Color of the focus highlight when the widget does not have focus.
        :arg highlightcolor:
                The color of the focus highlight when the widget has focus.
        :arg highlightthickness: 
                Thickness of the focus highlight.
        :arg labelanchor: 
                Use this option to specify the position of the label on the widget's border. The default position is 'nw', which places the label at the left end of the top border. For the nine possible label positions, refer to this diagram:
        :arg labelwidget: 
                Instead of a text label, you can use any widget as the label by passing that widget as the value of this option. If you supply both labelwidget and text options, the text option is ignored.
        :arg padx: 
                Use this option to add additional padding inside the left and right sides of the widget's frame. The value is in pixels.
        :arg pady: 
                Use this option to add additional padding inside the top and bottom of the widget's frame. The value is in pixels.
        :arg relief: 
                This option controls the appearance of the border around the outside of the widget. The default style is tk.GROOVE; for other values, Voir :ref:`reliefs`.
        :arg takefocus: 
                Normally, the widget will not receive focus; supply a True value to this option to make the widget part of the focus traversal sequence. For more information, see Section 53, “Focus: routing keyboard input”.
        :arg text: 
                Text of the label.
        :arg width: 
                The horizontal dimension of the new frame. This will be ignored unless you also call .grid_propagate(0) on the frame; Voir :ref:`autres-meth-grille`.
