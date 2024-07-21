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
