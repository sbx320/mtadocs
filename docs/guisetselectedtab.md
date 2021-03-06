This function is used to change the currently selected [tab](/docs/element/gui/tab.md "wikilink") in a [tab panel](/docs/element/gui/tab_panel.md "wikilink").

Syntax
------

``` lua
bool guiSetSelectedTab ( element tabPanel, element theTab )
```

### Required Arguments

-   **tabPanel:** The [tab panel](/docs/element/gui/tab_panel.md "wikilink") which current tab you want to change.
-   **theTab:** The [tab](/docs/element/gui/tab.md "wikilink") which will be the new active tab.

### Returns

Returns *true* if the selected tab was changed to a new one successfully, *false* otherwise.

Example
-------

This example changes the selected tab to the next available tab.

``` lua
local tabPanel = guiCreateTabPanel ( 0, 0.1, 1, 1, true) --create a tab panel which fills the whole window
local tab1 = guiCreateTab("Welcome",tabPanel) --create a tab for the tab panel above
local tab2 = guiCreateTab("Info",tabPanel)--create another tab for the tab panel at the top

function check()
   if(guiGetSelectedTab(tabPanel)==tab1)then --Check what tab is currently shown
      guiSetSelectedTab(tabPanel,tab2) --if the "Welcome" tab is selected, change it to tab2("Info" tab)
   else
      guiSetSelectedTab(tabPanel,tab1) --if the "Info" tab is selected, change it to tab1("Welcome" tab)
   end
end
```

See Also
--------
