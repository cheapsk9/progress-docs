# Slider

A slider allows users to select from a range of numbers, clamped between Min and Max, and rounded to the nearest Increment.
## 🔍 Properties

Value: number [Read Only]
The current selected number, as displayed by the Slider.

Min: number [Read Only]
The minimum value which can be picked by this Slider.

Max: number [Read Only]
The maximum value which can be picked by this Slider.

Increment: number [Read Only]
The amount the Slider is allowed advance. For example, if set to 1, the user can select only integer values, and if set to 0.1, the value will be rounded to the nearest tenth. Setting this value to 0 will disable rounding entirely.
## 🚀 Methods

SetValue (value : number) : void
Sets the value displayed on the slider.

SetMin (min : number) : void
Sets the minimum selectable value of the slider.

SetMax (max : number) : void
Sets the maximum selectable value of the slider.

SetIncrement (increment : number) : void
Sets the rounding increment of the slider.
## ⚡ Events

Changed (value : number) : RBXScriptSignal
Fires when the user changes the slider's value.