This function is for creating a new dxGUI window.

Syntax
------

``` lua
element dxCreateWindow( float x, float y, float width, float height, string titleBarText,[int color=white,string font=default,string theme=dxGetDefaultTheme()] )
```

### Required Arguments

-   **x:** A float of the 2D x position of the dxGUI window on a player's screen.
-   **y:** A float of the 2D y position of the dxGUI window on a player's screen.
-   **width:** A float of the width of the dxGUI window.
-   **height:** A float of the height of the dxGUI window.
-   **titleBarText:** A string of the text that will be displayed in the title bar of the window.
-   **color:** This the color of dxGUI: tocolor(255,255,255,255).
-   **font:** This the font text of dxGUI titleBarText: “default-bold”.
-   **theme:** This the theme of dxGUI: “Lighter Black”,“Lighter Blue”,“Orange” in themes.xml you can add more.

### Returns

Returns a dxgui window element if it was created successfully, false otherwise.

Example
-------

**Example 1:** This example creates a window.

``` lua
exports.dxGUI_v1:dxCreateWindow(0,0,250,300,"hola",tocolor(255,0,0,255),"default-bold","Orange")
```

Tutorial by pekio123
--------------------
