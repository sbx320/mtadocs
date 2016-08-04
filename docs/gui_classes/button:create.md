<pageclass class="client" subcaption="GUI Class method"></pageclass>

This function allows creation of a GUI Button, which is a clickable item as part of GUI.

Syntax
------

``` lua
buttonObject Button:Create ( float x, float y, float width, float height, string text, [ bool relative = false, element parent = nil ] )
```

### Required Arguments

-   **x:** A float of the 2D x position of the GUI button on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the GUI button on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the GUI button. This is affected by the *relative* argument.
-   **height:** A float of the height of the GUI button. This is affected by the *relative* argument.
-   **text:** A string of the text that will be displayed as a label on the button.

### Optional Arguments

-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing sizes relative to the parent.
-   **parent:** This is the parent that the gui button is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns a buttonObject if it was successfully created which then can use other methods, false otherwise.

Example
-------

This example creates an edit box alongside an “Output!” button. When the button is clicked, it will output the message in the text box into the Chat Box.

``` lua
addEventHandler ( "onClientResourceStart", getResourceRootElement(),
    function( )
        --create a button object
        local button = Button:Create( 0.7, 0.1, 0.2, 0.1, "Output!", true );
        --Create a TextBox (formally edit box)
        textBox = TextBox:Create( 0.3, 0.1, 0.4, 0.1, "Type your message here!", true )
        textBox:MaxLength( 128 ) --the max chatbox length is 128, so force this

        -- and attach the outputTextBox function to the button
        button:AddOnClick( outputTextBox );
    end
)
--setup our function to output the message to the chatbox
function outputTextBox( )
        local text = textBox:Text( ) --get the text from the TextBox
        outputChatBox ( text ) --output that text
end
```

See Also
--------

[Back to GUI Classes page](/docs/GUI_Classes.md "wikilink")