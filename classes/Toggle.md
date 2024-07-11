# Toggle

A toggle is a Boolean switch that simply describes an on or off (`true` or `false`) state. As such, it can only be in one of two states at a time.
## 🔍 Properties

Value: bool [Read Only]
The Boolean state of the toggle.
## 🚀 Methods

SetValue (value : bool) : void
Sets the state of the toggle.

Toggle () : void
Inverts the state of the toggle. If the toggle is false, it will be set to true, and vice versa.
## ⚡ Events

Changed () : RBXScriptSignal
Fires when the user changes the state of the toggle.
## 📞 Callbacks

OnChanged: bool
Called when the user changes this Toggle's state.
## 💡 Code Example

```lua
-- Create the toggle
local toggle = Sections.Self.Main:CreateElement("Toggle", {
	Value = true,
	Label = {
		Title = "Toggle",
		Text = "I am a toggle"
	},
	Callback = function(value)
		print("The state of the toggle changed", value)
	end
})

-- Wait 3 seconds
task.wait(3)

-- Set the toggle to a random state every half second for 5 times
for i = 1, 5 do
	toggle:SetValue(math.random() > 0.5)
	task.wait(0.5)
end

-- Wait 2 seconds
task.wait(2)

-- Invert (flip) the state of the toggle
toggle:Toggle()
```
