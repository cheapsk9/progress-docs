# ColorPicker

A color picker is a powerful interface that allows your users to select any of the valid >1.6 million RGB colors. But, if that many colors are overwhelming and makes it difficult to choose from, there are basic colors that are displayed when first opened. When the user selects one of the basic colors (or uses the button at the bottom to advance), it will give them options to refine the color if they'd like, offering the ability to select the hue, saturation, and value with mouse or touch input, or they can input color values such as RGB, HSV, or hex using text boxes.
## 🔍 Properties

Value: Color3 [Read Only]
The current selected color, as displayed by the ColorPicker.
## 🚀 Methods

SetValue (value : Color3) : void
Sets the current selected color of the ColorPicker.

Open () : void
Forces the Color Selection UI to open on this ColorPicker. Use the `Changed` event of the Color Picker to listen when the user interacts with it. Note that if the user closes the color picker, it will not fire.
## ⚡ Events

Changed (value : Color3) : RBXScriptSignal
Fires when the user changes the color via the Color Selection UI.
## 📞 Callbacks

OnChanged: void
Called when the color picker changes color.