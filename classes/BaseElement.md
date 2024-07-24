# BaseElement

An element is any one of the following: Alert, Button, ColorPicker, Dropdown, Label, Slider, TextBox, Toggle.

Elements display with a first-come-first-serve basis, meaning elements that are added first display at the top of the list.

Elements have properties, methods, and events just like normal Roblox instances.
They are created by calling `Section:CreateElement()`. A config table describes how the element should behave.

## 🔍 Properties

Label : Dictionary [Read Only]
The table of the label passed to this element.
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().  
> Use SetLabel() to change the label displayed on the element.

## 🚀 Methods

SetLabel (label : Dictionary) : void
Sets the label displayed on the element.
## 💡 Code Example

The below code example shows how to use `SetLabel` to change an element's displayed label. You can choose to only include in the table the parts of the label you want to change, such as `Title` or `Text`. 
```lua
-- Create a label container (or ANY element)
local label = sections.Self.Main:CreateElement("Label", {
	Label = {
		Title = "Hello, world",
		Text = "This is an example label"
	}
})

-- Wait 3 seconds
task.wait(3)

-- Update the label of this element, changing both the title and text.
label:SetLabel({
	Title = "Hello again!",
	Text = "I have updated my text"
})

-- Wait 3 more seconds
task.wait(3)

-- Update the label again, this time only changing the title.
label:SetLabel({
	Title = "I have updated my title"
})
```
