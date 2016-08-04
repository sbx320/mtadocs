<pageclass class="client" subcaption="GUI Class method"></pageclass>

You can use this method to attach a function to a sham event which is triggered when text changes. The function you pass to this method will be triggered whenever button text changes (when [object:Text](/GUI_Classes/GUISharedFuncs:Text.md "wikilink") is used)

Syntax
------

``` lua
bool Button:AddOnTextChanged ( function func )
```

### Required Arguments

-   **func:** the function you want to add to a list of functions triggered when text changes

  
``` lua
function func( buttonObject btn, string oldText, string newText )
```

Parameters which are passed to this function

-   **btn:** button object which was created with [Button:Create](/GUI_Classes/Button:Create.md "wikilink") and the function was attached to
-   **oldText** string containing old text before the text was changed
-   **newText** string containing new text of the button

### Returns

-   **true** if function was added successfully
-   **false** otherwise

Example
-------

This example creates a button. The button has two functions attached to it, one is triggered when user clicks the button (to change text on the button) and the other one is triggered when the text has changed (which sets the text back to the old text).

``` lua
addEventHandler ( "onClientResourceStart", getResourceRootElement(),
    function( )
        --create a button object
        local button = Button:Create( 0.7, 0.1, 0.2, 0.1, "Hello", true );

        -- and attach a function to the button which changes its text
        button:AddOnClick( changeMyText );

        -- add myTextHasChanged to the list of triggered functions when text changes
        button:AddOnTextChanged( myTextHasChanged );
    end
)

--setup a function to change the text
function changeMyText ( )
    local text = button:Text( ) --get the text from the button
    if text == "Hello" then
        -- if text of button was "Hello", change it to "World!"
        button:Text( "World!" );
        button:Enabled( false );
    end
end

function myTextHasChanged( btn, oldText, newText  )
    -- if new text is "World!" then set a timer which will change it back to old text (in this case "Hello")
    -- and enable the button
    if newText == "World!" then
        setTimer( btn:Text, 2500, 1, oldTex );
        setTimer( btn:Enabled, 2500, 1, true );
    end
end
```

See Also
--------

[Back to GUI Classes page](/GUI_Classes.md "wikilink")