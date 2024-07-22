# Button

A button is a basic interaction element that can be clicked. It can also display text on its surface.
## 🔍 Properties

Text : string [Read Only]
The text displayed on the button.
Default: "Button"
## 🚀 Methods

SetText (text : string) : void
Sets the text displayed on the button.
## ⚡ Events

Click () : RBXScriptSignal
Fires when the user presses and releases their cursor on the button.

> [!NOTE]
> Buttons do not have callbacks, because they don't need them. The `Click` event is wired directly to Roblox's `MouseButton1Click ()` event. To have a function fire when a button is clicked, connect to the `Click` event instead.
## 💡 Code Example

```lua
-- Create the button
local button = sections.Self.Main:CreateElement("Button", {
	Text = "Press me!",
	Label = {
		Title = "Am a cool button",
		Text = "Press me for important information regarding your fridge."
	}
})

-- Bind click event to the button
button.Click:Connect(function()
	UI.Window:ShowMessage(
		"Test Message",
		"I have hacked into your Samsung fridge.\nYou should be very scared right now. Real!"
	)
end)

-- Wait 3 seconds
task.wait(3)

-- Change the button's text
button:SetText("Example")
```
