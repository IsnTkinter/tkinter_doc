`Next`_ / `Previous`_ / `Contents`_ / `TCC Help System`_ / `NM Tech
homepage`_


Tkinter 8.5 reference: a GUI for Python
=======================================






4.1. The `.grid()` method
~~~~~~~~~~~~~~~~~~~~~~~~~

To display a widget ` * `w`*` on your application screen:

::

         * `w`*.grid( * `option`*= * `value`*, ...)


This method registers a widget ` * `w`*` with the grid geometry
manager—if you don't do this, the widget will exist internally, but it
will not be visible on the screen. For the options, see `Table 1,
“Arguments of the `.grid()` geometry manager”`_.

**Table 1. Arguments of the `.grid()` geometry manager**
`column` The column number where you want the widget gridded, counting
from zero. The default value is zero. `columnspan` Normally a widget
occupies only one cell in the grid. However, you can grab multiple
cells of a row and merge them into one larger cell by setting the
`columnspan` option to the number of cells. For example, ` *
`w`*.grid(row=0, column=2, columnspan=3)` would place widget ` * `w`*`
in a cell that spans columns 2, 3, and 4 of row 0. `in_` To register `
* `w`*` as a child of some widget ` * `w 2 `*`, use `in_= * `w 2 `*`.
The new parent ` * `w 2 `*` must be a descendant of the ` * `parent`*`
widget used when ` * `w`*` was created. `ipadx` Internal x padding.
This dimension is added inside the widget inside its left and right
sides. `ipady` Internal y padding. This dimension is added inside the
widget inside its top and bottom borders. `padx` External x padding.
This dimension is added to the left and right outside the widget.
`pady` External y padding. This dimension is added above and below the
widget. `row` The row number into which you want to insert the widget,
counting from 0. The default is the next higher-numbered unoccupied
row. `rowspan` Normally a widget occupies only one cell in the grid.
You can grab multiple adjacent cells of a column, however, by setting
the `rowspan` option to the number of cells to grab. This option can
be used in combination with the `columnspan` option to grab a block of
cells. For example, ` * `w`*.grid(row=3, column=2, rowspan=4,
columnspan=5)` would place widget ` * `w`*` in an area formed by
merging 20 cells, with row numbers 3–6 and column numbers 2–6.
`sticky` This option determines how to distribute any extra space
within the cell that is not taken up by the widget at its natural
size. See below.


+ If you do not provide a `sticky` attribute, the default behavior is
  to center the widget in the cell.
+ You can position the widget in a corner of the cell by using
  `sticky=tk.NE` (top right), `tk.SE` (bottom right), `tk.SW` (bottom
  left), or `tk.NW` (top left).
+ You can position the widget centered against one side of the cell by
  using `sticky=tk.N` (top center), `tk.E` (right center), `tk.S`
  (bottom center), or `tk.W` (left center).
+ Use `sticky=tk.N+tk.S` to stretch the widget vertically but leave it
  centered horizontally.
+ Use `sticky=tk.E+tk.W` to stretch it horizontally but leave it
  centered vertically.
+ Use `sticky=tk.N+tk.E+tk.S+tk.W` to stretch the widget both
  horizontally and vertically to fill the cell.
+ The other combinations will also work. For example,
  `sticky=tk.N+tk.S+tk.W` will stretch the widget vertically and place
  it against the west (left) wall.




**Next: **`4.2. Other grid management methods`_ **Contents: **`Tkinter
8.5 reference: a GUI for Python`_ **Previous: **`4. Layout
management`_ **Help: **`Tech Computer Center: Help System`_ **Home:
**`About New Mexico Tech`_


John W. Shipman Comments welcome: `tcc-doc@nmt.edu`_ Last updated:
2013-06-24 12:46 URL:
http://www.nmt.edu/tcc/help/pubs/tkinter/web/grid.html
.. _tcc-doc@nmt.edu: mailto:tcc-doc@nmt.edu
.. _About New Mexico Tech: http://www.nmt.edu/
.. _TCC Help System: http://www.nmt.edu/tcc/
.. _4.2. Other grid management methods: http://infohost.nmt.edu/tcc/help/pubs/tkinter/web/grid-methods.html
.. _Tech Computer
        Center: Help System: http://www.nmt.edu/tcc/help/
.. _ geometry
        manager”: http://infohost.nmt.edu/tcc/help/pubs/tkinter/web/grid.html#grid-arguments
.. _4. Layout management: http://infohost.nmt.edu/tcc/help/pubs/tkinter/web/layout-mgt.html
.. _ 8.5 reference: a GUI for Python: http://infohost.nmt.edu/tcc/help/pubs/tkinter/web/index.html


