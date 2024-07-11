# TextBox

The TextBox element is a simple rectangular area for text input.
## 🔍 Properties

Value: string [Read Only]
The text in the TextBox.

PlaceholderText: string [Read Only]
The placeholder text to display when nothing is in the TextBox.
Default value: ""
## 🚀 Methods

SetValue (value : string) : void
Sets the text in the TextBox.

SetPlaceholderText (text : string) : void
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
## 💡 Code Example

```lua
-- Create the text box
Sections.Self.Main:CreateElement("TextBox", {
	Value = "Default Text",
	PlaceholderText = "Placeholder Text",
	Label = {
		Title = "This is a text box.",
		Text = "You type stuff into it, and it does cool things."
	},
	Callback = function(value)
		print("The textbox's text changed to:", value)
	end
})

-- Wait 3 seconds
task.wait(3)

-- Change the textbox's text
TextBox:SetValue("Hello, world!")
```
