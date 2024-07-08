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
Fires when the user changes the text in the TextBox.

Focused () : RBXScriptSignal
Fires when the TextBox is focused.

FocusReleased () : RBXScriptSignal
Fires when the TextBox focus is released.