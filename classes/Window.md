# Window

The Window object contains functions and properties related to reading and controlling the state of the window. Most importantly, `Window:Open()` will open the window to display its content.
## 🔍 Properties

IsMinimized: bool
Whether or not the window is currently minimized. Ignores playing transitions.

IsSmall: bool
Whether the window is currently taking up half (true) or all (false) of the allocated screen area. Ignores playing transitions.

IsOpen: bool
Whether or not the window is currently open. Ignores playing transitions.

Theme: number
## 🚀 Methods

ShowMessage (title : string, text : string)
Shows a modal message that requires the user to click the OK button to acknowledge and close it.

SetMinimized (minimized : bool, transition? : bool)
Sets whether the hub is currently minimized to the side of the screen.

SetSmall (small : bool, transition? : bool)
Sets whether the window is half-size (true) or full-size (false).

Open (transition? : bool)
Opens the window.

Close (transition? : bool)
Forces the window to close and cleans up the UI.

ChangeTheme (themeId : number)
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