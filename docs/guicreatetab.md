This function creates a tab on a pre-existing tab panel. A tab is a button as well as a 'dimension' that can be used to switch between information by clicking on the tabs. Tabs are sorted on a tab panel in the order that they are created.

Syntax
------

``` lua
element guiCreateTab ( string text, element parent )
```

### Required Arguments

[frame|Example GUI tab panel with two tabs.](/docs/image:gui-tabpanelandtab.png.md "wikilink")

-   **text:** The caption for the tab
-   **parent:** The parent tab panel, as a tab panel [element](/docs/element.md "wikilink") type

### Returns

Returns a tab element if successful, *false* otherwise.

Example
-------

This example creates a information window and adds two tabs to a “tabPanel” tabpanel, and adds some other gui elements to it.

``` lua
local myWindow = guiCreateWindow ( 0, 0, 0.5, 0.4, "Information", true )--create a window which has "Information" in the title bar.
local tabPanel = guiCreateTabPanel ( 0, 0.1, 1, 1, true, myWindow ) --create a tab panel which fills the whole window
local tabMap = guiCreateTab( "Map Information", tabPanel ) -- create a tab named "Map Information" on 'tabPanel'
local tabHelp = guiCreateTab( "Help", tabPanel ) -- create another tab named "Help" on 'tabPanel'

-- adds a label (text) to each tab
guiCreateLabel(0.02,0.04,0.94,0.2,"This is information about the current map",true,tabMap)
guiCreateLabel(0.02,0.04,0.94,0.92,"This is help text.",true,tabHelp)
```

See Also
--------
