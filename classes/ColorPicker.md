# ColorPicker

A color picker is a powerful interface that allows your users to select any of the valid >1.6 million RGB colors. But, if that many colors are overwhelming and makes it difficult to choose from, there are basic colors that are displayed when first opened. When the user selects one of the basic colors (or uses the button at the bottom to advance), it will give them options to refine the color if they'd like, offering the ability to select the hue, saturation, and value with mouse or touch input, or they can input color values such as RGB, HSV, or hex using text boxes.
## 🔍 Properties

Value : Color3 [Read Only]
The current selected color, as displayed by the ColorPicker.
## 🚀 Methods

SetValue (value : Color3) : void
Sets the current selected color of the ColorPicker.

Open () : void
Forces the Color Selection UI to open on this ColorPicker. Use the `Changed` event of the Color Picker to listen when the user interacts with it. Note that if the user closes the color picker, it will not fire.
## 📞 Callbacks

OnChanged: Color3
Called when the user changes the color picker's displayed color.
## 💡 Code Example

```lua
-- Create the color picker
local colorPicker = sections.Self.Main:CreateElement("ColorPicker", {
	Value = Color3.fromRGB(100, 0, 50),
	Label = {
		Title = "Color picker",
		Text = "I am a color picker. Click me to choose from over 1.6 million colors."
	},
	OnChanged = function(value)
		print("Color picker changed value:", value)
	end
})

-- Wait 3 seconds
task.wait(3)

-- Set the color picker's value to a random color
colorPicker:SetValue(BrickColor.random().Color)
```
