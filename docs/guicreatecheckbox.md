This function creates a [checkbox](/docs/element/gui/checkbox.md "wikilink").

Syntax
------

``` lua
element guiCreateCheckBox ( float x, float y, float width, float height, string text, bool selected, bool relative, [element parent = nil] )
```

### Required Arguments

[thumb|Test Checkbox](/docs/image:checkbox.png.md "wikilink")

-   **x:** A float of the 2D x position of the checkbox on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the checkbox on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the text field next to the checkbox. This is affected by the *relative* argument.
-   **height:** A float of the height of the text field next to the checkbox. This is affected by the *relative* argument.
-   **text:** The text to be displayed next to the checkbox.
-   **selected:** A boolean representing whether the checkbox created should be selected by default.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing measures relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the checkbox is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns [element](/docs/element.md "wikilink") of the checkbox if it was created succesfully, *false* otherwise.

Example
-------

This example creates a GUI window with a checked and an unchecked checkbox and adds a command to toggle their visibility

``` lua
function drawGUI()
    local guiWindow = guiCreateWindow(100,100,200,100,"Checkbox test area",false,false) -- create the container window
    local checkedBox = guiCreateCheckBox(20,30,150,20,"Checked checkbox",true,false,guiWindow) -- note the parameter after header, it will make the checkbox be checked
    local uncheckedBox = guiCreateCheckBox(20,60,150,20,"Unchecked checkbox",false,false,guiWindow) -- not here though
    guiSetVisible(guiWindow,false) -- set it invisible just in case
    return guiWindow -- we return the guiWindow
end
function cmdGUI(cmd)
    if not checkBoxWindow then -- if it hasn't been declared yet
        checkBoxWindow = drawGUI() -- we draw the gui window
        guiSetVisible(checkBoxWindow,true) -- we set it visible again. Strictly speaking it's not necessary, could have omitted both this and the upper guiSetVisible, but this is needed if you want to cache a window without actually showing it
    else -- if we actually have run this function before and declared checkBoxWindow
        guiSetVisible(checkBoxWindow, not guiGetVisible(checkBoxWindow)) -- we just toggle the visibility. If it was visible, not visible returns false and thus sets it's visibility false, effectivly hiding it   
    end
    showCursor(not isCursorShowing()) -- similar to above visibility
end
addCommandHandler("guiwindow",cmdGUI) -- trigger cmdGUI function with this command
```

See Also
--------
