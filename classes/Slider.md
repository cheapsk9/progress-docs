# Slider

A slider allows users to select from a range of numbers, clamped between Min and Max, and rounded to the nearest Increment. The value won't be less than `Min`, won't be greater than `Max`, and will be a multiple of `Step`.
## 🔍 Properties

Value: number [Read Only]
The current selected number, as displayed by the Slider.

Min: number [Read Only]
The minimum value which can be picked by this Slider.
Default: 0

Max: number [Read Only]
The maximum value which can be picked by this Slider.
Default: 100

Step: number [Writable]
The amount the Slider is allowed advance. For example, if set to 1, the user can select only integer values, and if set to 0.1, the value will be rounded to the nearest tenth. Setting this value to 0 will disable rounding entirely.
Default: 1
## 🚀 Methods

SetValue (value : number, ignoreStep : bool) : void
Sets the value displayed on the slider. Accounts for the rounding applied by `Step`, unless `ignoreStep` is true.

SetMin (min : number) : void
Sets the minimum selectable value of the slider. If the slider's value is above this, it will be clamped.

SetMax (max : number) : void
Sets the maximum selectable value of the slider. If the slider's value is below this, it will be clamped.
## 📞 Callbacks

OnChanged: number
Called when the user changes the slider's value.
## 💡 Code Example

The following example shows how to create a basic slider:
```lua
-- Create the slider
local slider = Sections.Self.Main:CreateElement("Slider", {
	Value = 3,
	Min = 0,
	Max = 10,
	Step = 1, -- If 0, the slider is free to move without restrictions. If 1, the slider will "snap" to integers.
	Label = {
		Title = "A Cool Slider",
		Text = "I'm a very cool slider that can select any integer from 0-10."
	},
	-- Assign a callback
	-- You can also use slider.Changed:Connect(f), although this is immediate.
	Callback = function(value)
		print("The slider's value changed to:", value)
	end
})

-- Wait 3 seconds
task.wait(3)

-- Change the value to a random number from 0 to 10
slider:SetValue(math.random(0, 10))
```
