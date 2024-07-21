# Type Coercion

Roblox objects natively support [type coercion](https://create.roblox.com/docs/luau/type-coercion), meaning if a value isn't in the type that is expected, Luau will 'coerce' that value to be of the correct type. For example, you may think that the following operation would fail, since they are strings:

```lua
print("1" + "2")
```

However, thanks to Luau's type coercion, the operation does not fail, and prints `3`.

The APIs in Progress also automatically coerce types. For example, if you try to create a label and set the text to a number, it will work because in Progress' code, it automatically calls `tostring` on the Text field. For example:
```lua
local label = Sections.Self.Main:CreateElement("Label", {
	Label = {
		Title = "The value of pi is...",
		Text = math.pi -- The value of math.pi is a number, not a string
	}
})
```

The same concept applies to the reverse: setting a number value to a string. Progress' internal code automatically applies `tonumber` on any number values passed to sanitize them. For example:
```lua
local slider = Sections.Self.Main:CreateElement("Slider", {
	Value = "3", -- expects number but is a string
	Min = 0,
	Max = 10,
	Label = {
		Title = "Coercion Example",
		Text = "string -> number coercion example"
	}
})
```