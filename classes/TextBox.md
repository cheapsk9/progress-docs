# TextBox

The TextBox element is a simple rectangular area for text input.
## 🔍 Properties

Value: string [Read Only]
The text in the TextBox.

PlaceholderText: string [Read Only]
The placeholder text to display when nothing is in the TextBox.
## 🚀 Methods

SetValue (value : string) : void
Sets the text in the TextBox.

SetPlaceholderText (placeholder : string) : void
Sets the placeholder text of the TextBox.
## ⚡ Events

Changed (value : string) : RBXScriptSignal
Fires when the user (or scripts) changes the text in the TextBox.
> [!WARNING]
> This event is also fired when scripts change the value. Be careful to not cause infinite loops

Focused () : RBXScriptSignal
Fires when the TextBox is focused.

FocusReleased () : RBXScriptSignal
Fires when the TextBox focus is released.
## 📞 Callbacks

OnChanged: string
Called when the TextBox's text changes.
> [!WARNING]
> This callback is also called when scripts change the value. Be careful to not cause infinite loops
