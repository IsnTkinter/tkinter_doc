.. _APPEARANCE:

************************************************
Standardizing appearance and the option database
************************************************

It's easy to apply colors, fonts, and other options to the widgets when you create them. However,

* if you want a lot of widgets to have the same background color or font, it's tedious to specify each option each time, and

* it's nice to let the user override your choices with their favorite color schemes, fonts, and other choices. 

Accordingly, we use the idea of an option database to set up default option values.

* Your application can specify a file (such as the standard .Xdefaults file used by the X Window System) that contains the user's preferences. You can set up your application to read the file and tell Tkinter to use those defaults. See the section on the .option_readfile() method, above, in the section on Section 26, “Universal widget methods”, for the structure of this file.

* Your application can directly specify defaults for one or many types of widgets by using the .option_add() method; see this method under Section 26, “Universal widget methods”. 

Before we discuss how options are set, consider the problem of customizing the appearance of GUIs in general. We could give every widget in the application a name, and then ask the user to specify every property of every name. But this is cumbersome, and would also make the application hard to reconfigure—if the designer adds new widgets, the user would have to describe every property of every new widget.

So, the option database allows the programmer and the user to specify general patterns describing which widgets to configure.

These patterns operate on the names of the widgets, but widgets are named using two parallel naming schemes:

a) Every widget has a class name. By default, the class name is the same as the class constructor: 'Button' for buttons, 'Frame' for a frame, and so on. However, you can create new classes of widgets, usually inheriting from the Frame class, and give them new names of your own creation. See Section 27.1, “How to name a widget class” for details.

b) You can also give any widget an instance name. The default name of a widget is usually a meaningless number (see Section 5.11, “Window names”). However, as with widget classes, you can assign a name to any widget. See the section Section 27.2, “How to name a widget instance” for details. 

Every widget in every application therefore has two hierarchies of names—the class name hierarchy and the instance name hierarchy. For example, a button embedded in a text widget which is itself embedded in a frame would have the class hierarchy Frame.Text.Button. It might also have an instance hierarchy something like .mainFrame.messageText.panicButton if you so named all the instances. The initial dot stands for the root window; see Section 5.11, “Window names” for more information on window path names.

The option database mechanism can make use of either class names or instance names in defining options, so you can make options apply to whole classes (e.g., all buttons have a blue background) or to specific instances (e.g., the Panic Button has red letters on it). After we look at how to name classes and instances, in Section 27.3, “Resource specification lines”, we'll discuss how the options database really works.

How to name a widget class
==========================

For example, suppose that Jukebox is a new widget class that you have created. It's probably best to have new widget classes inherit from the Frame class, so to Tkinter it acts like a frame, and you can arrange other widgets such as labels, entries, and buttons inside it.

You set the new widget's class name by passing the name as the class\_ option to the parent constructor in your new class's constructor. Here is a fragment of the code that defines the new class::

    class Jukebox(tk.Frame):
        def __init__(self, master):
            '''Constructor for the Jukebox class
            '''
            tk.Frame.__init__(self, master, class_='Jukebox')
            self.__createWidgets()
            ...

To give an instance name to a specific widget in your application, set that widget's name option to a string containing the name.

How to name a widget instance
=============================

Here's an example of an instance name. Suppose you are creating several buttons in an application, and you want one of the buttons to have an instance name of panicButton. Your call to the constructor might look like this::

    self.panic = tk.Button(self, name='panicButton', text='Panic', ...)
    
Each line in an option file specifies the value of one or more options in one or more applications and has one of these formats::

    app option-pattern: value
    option-pattern: value

The first form sets options only when the name of the application matches app; the second form sets options for all applications.

For example, if your application is called xparrot, a line of the form::

    xparrot*background: LimeGreen

sets all background options in the xparrot application to lime green. (Use the -name option on the command line when launching your application to set the name to 'xparrot'.)

The option-pattern part has this syntax::

    {{*|.}name}...option

That is, each option-pattern is a list of zero or more names, each of which is preceded by an asterisk or period. The last name in the series is the name of the option you are setting. Each of the rest of the names can be either:

* the name of a widget class (capitalized), or

* the name of an instance (lowercased). 

The way the option patterns work is a little complicated. Let's start with a simple example::

    *font: times 24

This line says that all font options should default to 24-point Times. The * is called the loose binding symbol, and means that this option pattern applies to any font option anywhere in any application. Compare this example::

    *Listbox.font: lucidatypewriter 14

The period between Listbox and font is called the tight binding symbol, and it means that this rule applies only to font options for widgets in class Listbox.

As another example, suppose your xparrot application has instances of widgets of class Jukebox. In order to set up a default background color for all widgets of that class Jukebox, you could put a line in your options file like this::

    xparrot*Jukebox*background: PapayaWhip

The loose-binding (*) symbol between Jukebox and background makes this rule apply to any background option of any widget anywhere inside a Jukebox. Compare this option line::

    xparrot*Jukebox.background: NavajoWhite

This rule will apply to the frame constituting the Jukebox widget itself, but because of the tight-binding symbol it will not apply to widgets that are inside the Jukebox widget.

In the next section we'll talk about how Tkinter figures out exactly which option value to use if there are multiple resource specification lines that apply. 

Rules for resource matching
===========================

When you are creating a widget, and you don't specify a value for some option, and two or more resource specifications apply to that option, the most specific one applies.

For example, suppose your options file has these two lines::

    *background: LimeGreen
    *Listbox*background: FloralWhite

Both specifications apply to the background option in a Listbox widget, but the second one is more specific, so it will win.

In general, the names in a resource specification are a sequence n1, n2, n3, ..., o where each ni is a class or instance name. The class names are ordered from the highest to the lowest level, and o is the name of an option.

However, when Tkinter is creating a widget, all it has is the class name and the instance name of that widget.

Here are the precedence rules for resource specifications:

1) The name of the option must match the o part of the option-pattern. For example, if the rule is

   xparrot*indicatoron: 0

   this will match only options named indicatoron.

2) The tight-binding operator (.) is more specific than the loose-binding operator (*). For example, a line for \*Button.font is more specific than a line for \*Button*font.

3) References to instances are more specific than references to classes. For example, if you have a button whose instance name is panicButton, a rule for \*panicButton*font is more specific than a rule for \*Button\*font.

4) A rule with more levels is more specific. For example, a rule for \*Button*font is more specific than a rule for \*font.

5) If two rules have same number of levels, names earlier in the list are more specific than later names. For example, a rule for xparrot*font is more specific than a rule for \*Button*font. 
