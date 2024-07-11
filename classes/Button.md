# Button

A button is a basic interaction element that can be clicked. It can also display text on its surface.
## 🔍 Properties

Text: string [Read Only]
The text displayed on the button.
## 🚀 Methods

SetText (text : string) : void
Sets the text displayed on the button.
## ⚡ Events

Click () : RBXScriptSignal
Fires when the user presses and releases their cursor on the button.

> [!NOTE]
> Buttons do not have callbacks, because they don't need them. The `Click` event is wired directly to Roblox's `MouseButton1Click ()` event. To have a function fire when a button is clicked, connect to the `Click` event instead.