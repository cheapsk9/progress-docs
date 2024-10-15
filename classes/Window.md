# Window

The Window object contains functions and properties related to reading and controlling the state of the window. Most importantly, `Window:Open()` will open the window to display its content.

> [!IMPORTANT]
> It's very important that when users close the hub, that your script stops running. It's highly recommended to listen to the `OnClosing` callback, and stop all loops that your script is running.
## 🔍 Properties

IsMinimized : bool [Read Only]
Whether or not the window is currently minimized. Ignores playing transitions.

IsSmall : bool [Read Only]
Whether the window is currently taking up half (true) or all (false) of the allocated screen area. Ignores playing transitions.

IsOpen : bool [Read Only]
Whether or not the window is currently open. Ignores playing transitions.

ThemeId: number [Read Only]
## 🚀 Methods

ShowMessage (title : string, text : string) : void
Shows a modal message that requires the user to click the OK button to acknowledge and close it.
> [!WARNING] This member is deprecated in favor of `ShowDialog`. Do not use for future work.

ShowDialog (configTable : Dictionary) : void
Shows a dialog inside the window. The configuration is as follows:

| Name        | Type       | Default  | Description                                                                                                                                                               |
| ----------- | ---------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Title       | string     | Optional | The title of the dialog                                                                                                                                                   |
| Text        | string     | Required | The main text of the dialog                                                                                                                                               |
| CopyBoxText | string     | Optional | If specified, will show a read-only text box inside the dialog that the user can use to select the text and copy it. Useful for when clipboard functions are unavailable. |
| Buttons     | Dictionary | Optional | Similar to toasts, this config allows buttons to be placed inside the dialog that can be used to run callbacks. For more information, see the table below.                |
"Buttons" array:
{
... (for *n* options):

| Name      | Type     | Default  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| --------- | -------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Title     | string   | "Button" | The text of the button.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Callback  | function | Optional | The function to call when the button is pressed.                                                                                                                                                                                                                                                                                                                                                                                                             |
| Secondary | boolean  | Optional | Indicates to the user that this button is for the secondary action by using a muted color, rather than a primary. For example, Progress makes use of this internally when the user requests to close the hub. We don't want users to close our hub, but if they must, we give the option. We display the 'OK' button as a muted white color by using `Secondary=true`, and the 'Cancel' button as the theme color to indicate that it is the desired action. |
...
}

SetMinimized (minimized : bool, transition? : bool) : void
Sets whether the hub is currently minimized to the side of the screen.

SetSmall (small : bool, transition? : bool) : void
Sets whether the window is half-size (true) or full-size (false).

Open (transition? : bool) : void
Opens the window.

Close (transition? : bool) : void
Forces the window to close and cleans up the UI.

SetSubtitle(text : string) : void
Sets the subtitle text displayed on the UI, beneath the title.

ChangeTheme (themeId : number) : void
## ⚡ Events

MinimizedChanged (minimized : bool) : RBXScriptSignal
Fires when the user (or scripts) minimize the window.

SizeChanged (small : bool) : RBXScriptSignal
Fires when the user (or scripts) change the window size.

Opened () : RBXScriptSignal
Fires when the window is opened via scripts.

Closing () : RBXScriptSignal
Fires when the user (or scripts) closed the window.

ThemeChanged (themeId : number) : RBXScriptSignal
## 💡 Code Example

The following code snippet showcases the abilities of the Window by doing multiple things with it.
```lua
-- Prints when the window is opened.
api.Window.OnOpened = function()
	print("The window was opened.")
end

-- Prints when the window is minimized.
api.Window.OnMinimizedChanged = function(isMinimized)
	print("The window's minimized state changed to:", isMinimized)
end

-- Prints when the window's size changes.
api.Window.OnSizeChanged = function(isSmall)
	print("The window's size changed. Small:", isSmall)
end

-- Prints when the window is closing.
api.Window.OnClosing = function()
	print("The window is closing.")
end


-- Open the window.
api.Window:Open()

-- Change the window's subtitle to today's date.
api.Window:SetSubtitle(os.date())

-- Set the window to be small
api.Window:SetSmall(true)

-- Wait 2 seconds
task.wait(2)

-- Set the window back to normal
api.Window:SetSmall(false)

-- Wait 2 seconds
task.wait(2)

-- Minimize the window
api.Window:SetMinimized(true)

-- Wait 2 seconds
task.wait(2)

-- Restore the window
api.Window:SetMinimized(false)

-- Wait 5 seconds
task.wait(5)

-- Close the window
api.Window:Close()
```
