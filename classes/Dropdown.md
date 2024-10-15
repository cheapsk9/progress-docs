# Dropdown

The Dropdown element allows users to select from a list of values.
## 🔍 Properties

Values : Array [Read Only]
The current values displayed in the dropdown list.
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().
> Use AddValues(), SetValues(), and RemoveValues() to change the values displayed in the list.

Selected : Array [Read Only]
The values that are currently selected in the dropdown list.
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().
> Use AddSelection(), SetSelection(), and RemoveSelection() to change the seleced values.

MultiSelect : bool [Read Only]
Marks whether the dropdown is standard or multi dropdown.
false = Standard, true = Multi-Selection
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().
> Use SetMultiSelect() to change whether this dropdown is multi-selection.

SelectionLocks : bool [Writable]
If enabled, when the user selects an option, they will be unable to unselect it unless they "pass it" to another option.
> [!NOTE]
> This property only applies to one-select dropdowns, not multi-dropdown.

SelectionForced : bool [Read Only] [TBD]
If true, will require that one element is always selected. This way, the number of selections will always be one. If no values are selected from the calling script, the first value will be selected as a fallback. If no values are in the list, this will be unable to function and the number of selections will be zero. Setting this property to true will also lock selections identically to having `LockSelection` set to true.
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().
> Use SetSelectionForced() to change if the selection is forced.

> [!NOTE]
> This property only applies to one-select dropdowns, not multi-dropdown.

Enabled : bool [Writable] [TBD]
Sets whether the dropdown options can be interacted with.
The dropdown can still be expanded, but attempting to change the list selection will do nothing.
Default: true

PlaceholderText : string [Read Only]
The placeholder text to show if there are no selected values.
Default: "Select..."
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().
> Use SetPlaceholderText() to change the placeholder text.

AutoUpdateNames : bool [Writable]
Describes whether names of `Instance` values should be updated automatically when they change name. Does not apply to metatables. You will need to update metatables manually.
Default: true

UpdateNamesOnInput : bool [Writable] [TBD]
If true, whenever a dropdown option is interacted with, such as hovered, selected, etc, it will update the name by calling the `__tostring` metamethod. This only works for metatables. Does not apply to `Instance` values. Otherwise, it is highly recommended to use **UpdateNames()** when you know a metatable name is updated.
Default: true

RemoveDestroyedInstances : bool [Writable] [Not Yet Implemented]
Removes `Instance` values from the dropdown options once they have been destroyed.
Default: false
## 🚀 Methods

AddValues (objects : Tuple<Array, any>, selected? : Tuple<Array, any>, tweenSelection? : bool) : void [Not Yet Implemented]
Adds values to the dropdown's list. New values get added at the bottom, although you can manually set their LayoutOrder with DropDownValue.Object.LayoutOrder

SetValues (objects : Tuple<Array, any>, selected? : Tuple<table, any>, tweenSelection? : bool) : void
Sets the values for the dropdown, overwriting the whole list.

RemoveValues (objects : Tuple<Array, any>) : void [Not Yet Implemented]
Removes values from the dropdown's list.


AddSelection (objectsToAdd : Tuple<Array, any>, tweenSelection? : bool) : void [Not Yet Implemented]
Adds a selection to the objects in the list.

SetSelection (selection : Tuple<Array, any>, tweenSelection? : bool) : void
Overwrites the entire selection for the Dropdown's list.

RemoveSelection (objectsToRemove : Tuple<Array, any>, tweenSelection? : bool) : void [Not Yet Implemented]
Removes the selection from the objects in the list.


SetPlaceholderText (text : string) : void
Sets the placeholder text for the Dropdown to display when there are no selected values.

UpdateNames (values : table) : void [Not Yet Implemented]
If using Instances or metatables and the name of a metatable has changed (\_\_tostring metamethod), call this function to update the name displayed. This needs to be called manually due to performance concerns.

SetSelectionForced (forced : bool, reselect : bool, tweenSelection? : bool) : void [Not Yet Implemented]
Changes whether or not the selection is forced.
`forced` changes the forced state, see `SelectionForced` for more information.
The `reselect` parameter defines if the selection should revert to only the first value in the list.
This needs to be called manually due to the immediate changes of the `reselect` parameter.

SetMultiSelection (multi : bool, reselect : bool, tweenSelection? : bool) : void [Not Yet Implemented]
Changes the multi-select state of the dropdown.
`multi` sets whether or not the dropdown is standard selection or multi-selection. (Default: false)
The `reselect` parameter defines if the selection should revert to only the last selected value, and only applies if `multi` is set to true. (Default: true)
This needs to be called manually due to the immediate changes of the `reselect` parameter.
## 📞 Callbacks

OnSelectionChanged (values : Array) : RBXScriptSignal
Returns a list of the currently selected objects.

> [!NOTE] Note
> Below are special callbacks that pertain to user behavior within the dropdown. These special callbacks only fire if the user interacts with the dropdown, or if the selection was forced by ForceSelection. They do not fire when scripts change them. For listening to script changes, use `OnSelectionChanged`.

OnValueSelected (value : any) : RBXScriptSignal
Fires when a value is selected, and returns that value.
This only applies to selection being gained, not taken away. So, if `MultiSelect` is true or on a standard list with `SelectionLocks` set to false, and the user unselects the last value, this will not fire, however the `SelectionChanged` and `SelectionDiffered` events will fire.

OnValueUnselected (value : any) : RBXScriptSignal
Fires when a value is unselected, and returns that value.

OnSelectionDifference (selected : Tuple<any, nil>, unselected : Tuple<any, nil>) : RBXScriptSignal
This callback combines `OnValueSelected` and `OnValueUnselected` into one for convenience. Whenever the selection is changed (user selecting or unselecting an object), the selected object, if applicable, will be passed to the first value, and the unselected object, if applicable, will be passed to the second value.
The following chart is a list of outcomes from user input returned by this callback:

| `OnSelectionDifference` User Action             | `selected`     | `unselected`     |
| ----------------------------------------------- | -------------- | ---------------- |
| Selecting a value in a multi-dropdown           | selected value | `nil`            |
| Unselecting a value in a multi-dropdown         | `nil`          | unselected value |
| Transferring the selection in a single-dropdown | current value  | previous value   |
## 💡 Code Example

The following code truly demon-strates the power of the API, so try to follow along! It creates a config, and modifies it to make two separate dropdowns: a single-select dropdown, and a multi-select dropdown. Then, it prints the selection, modifies it, and prints it again.

```lua
-- Define our base configuration for both dropdowns. It's worth noting that previous configurations are always safe to use later and are never overwritten.
local dropdownConfig = {
	Values = {
		"Option 1",
		"Option 2",
		"Option 3",
		"Option 4",
		"Option 5"
	},
	Selected = {
		"Option 1",
	},
	OnSelectionChanged = function(values)
		print("Selection was changed to:", unpack(values))
	end,
	OnSelectionDifference = function(selected, unselected)
		print("Selection difference:", selected, unselected)
	end,
	OnValueSelected = function(value)
		print("Value selected:", value)
	end,
	OnValueUnselected = function(value)
		print("Value unselected:", value)
	end
}

-- Add to config for dropdown #1
dropdownConfig.Label = {
	Title = "Dropdown",
	Text = "I am a dropdown that can only select from one value at a time."
}

-- Create dropdown #1
local dropdown1 = sections.Self.Main:CreateElement("Dropdown", dropdownConfig)

-- Add to config for dropdown #2
dropdownConfig.MultiSelect = true
dropdownConfig.Label = {
	Title = "Multi Dropdown",
	Text = "I am a dropdown that can select from multiple values at a time."
}

-- Create dropdown #2
local dropdown2 = sections.Self.Main:CreateElement("Dropdown", dropdownConfig)

-- Define `selected` and `values` variables from `dropdown2.Selected` and `dropdown2.Values`, which dynamically change.
local selected = dropdown2.Selected
local values = dropdown2.Values

--[[
Unlike Roblox instances, table references returned by an element can be safely held onto forever.
So, instead of indexing `dropdown2.Selected` and `dropdown2.Values` each time, for example, you can just keep them in a `selected` or `values` variable.
Then, whenever the selected values change, since it's a table, it will change its values as well.
--]]
print("Values:", unpack(values))
print("Selected:", unpack(selected))

-- Wait 3 seconds
task.wait(3)

-- Change the values of dropdown #2 (this also changes the selection too!)
dropdown2:SetValues(
	{ -- Values
		"Hello", -- String value
		"world",
		2, -- Number value
		game, -- Instance value
		workspace.CurrentCamera -- Another instance value. This should be removed if it's destroyed from the Workspace.
	},
	{ -- Selected
		"yoyoyo", -- Invalid; will be ignored.
		"world",
		2
	}
)

-- Example of reusing the `selected` and `values` variables later
-- Prints a different result, since it's the same table being changed and therefore does not need a new reference.
print("Values:", unpack(values))
print("Selected:", unpack(selected))
```