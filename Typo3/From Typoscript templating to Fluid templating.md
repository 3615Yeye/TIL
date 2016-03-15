Why Fluid ?
Modern and powerfull syntax compared to Typoscript.

# Page information
The {data} variable contains the page informations like the title, author, lastUpdate...

To see all the available informations, add the following to your template :
<f:debug title="Data-Variable">{data}</f:debug>

# VHS extension
Fluid View Helpers is a collection of ViewHelpers to perform rendering tasks which are not natively supported by Fluid.

It's useful at least for the menu.
Don't forget to add the namespace where vhs is used (see below).

# Menu
Like a boss using vhs : https://worksonmymachine.org/blog/a-guide-to-menu-rendering-with-fluidtypo3

# Namespaces
Two way to declare namespaces :
- {namespace v=FluidTYPO3\Vhs\ViewHelpers}
- <div xmlns:v="http://typo3.org/ns/FluidTYPO3/Vhs/ViewHelpers">
