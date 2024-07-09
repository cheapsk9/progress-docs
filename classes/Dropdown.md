# Dropdown

The Dropdown element allows users to select from a list of values.
## 🔍 Properties

Values: Array [Read Only]
The current values displayed in the dropdown list.
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().
> Use AddValues(), SetValues(), and RemoveValues() to change the values displayed in the list.

Selected: Array [Read Only]
The values that are currently selected in the dropdown list.
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().
> Use AddSelection(), SetSelection(), and RemoveSelection() to change the seleced values.

MultiSelect: bool [Read Only]
Marks whether the dropdown is standard or multi dropdown.
false = Standard, true = Multi-Selection
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().
> Use SetMultiSelect() to change whether this dropdown is multi-selection.

SelectionLocks: bool [Writable]
If enabled, when the user selects an option, they will be unable to unselect it unless they "pass it" to another option.
> [!NOTE]
> This property only applies to one-select dropdowns, not multi-dropdown.

SelectionForced: bool [Read Only]
If true, will require that one element is always selected. This way, the number of selections will always be one. If no values are selected from the calling script, the first value will be selected as a fallback. If no values are in the list, this will be unable to function and the number of selections will be zero. Setting this property to true will also lock selections identically to having `LockSelection` set to true.
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().
> Use SetSelectionForced() to change if the selection is forced.

> [!NOTE]
> This property only applies to one-select dropdowns, not multi-dropdown.

Enabled: bool [Writable]
Sets whether the dropdown options can be interacted with.
The dropdown can still be expanded, but attempting to change the list selection will do nothing.
Default: true

PlaceholderText: string [Read Only]
The placeholder text to show if there are no selected values.
Default: "Select..."
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().
> Use SetPlaceholderText() to change the placeholder text.

AutoUpdateNames: bool [Writable]
Describes whether names of `Instance` values should be updated automatically when they change name. Does not apply to metatables. You will need to update metatables manually.

UpdateNamesOnInput: bool [Writable]
If true, whenever a dropdown option is interacted with, such as hovered, selected, etc, it will update the name by calling the `__tostring` metamethod. This only works for metatables. Does not apply to `Instance` values. Otherwise, it is highly recommended to use **UpdateNames()** when you know a metatable name is updated.

RemoveDestroyedInstances: bool [Writable]
Removes `Instance` values from the dropdown options once they have been destroyed.
## 🚀 Methods

AddValues (objects : Tuple<Array, any>, selected? : Tuple<Array, any>, tweenSelection? : bool) : void
Adds values to the dropdown's list. New values get added at the bottom, although you can manually set their LayoutOrder with DropDownValue.Object.LayoutOrder

SetValues (objects : Tuple<Array, any>, selected? : Tuple<table, any>, tweenSelection? : bool) : void
Sets the values for the dropdown, overwriting the whole list.

RemoveValues (objects : Tuple<Array, any>) : void
Removes values from the dropdown's list.


AddSelection (objectsToAdd : Tuple<Array, any>, tweenSelection? : bool) : void
Adds a selection to the objects in the list.

SetSelection (selection : Tuple<Array, any>, tweenSelection? : bool) : void
Overwrites the entire selection for the Dropdown's list.

RemoveSelection (objectsToRemove : Tuple<Array, any>, tweenSelection? : bool) : void
Removes the selection from the objects in the list.


SetPlaceholderText (text : string) : void
Sets the placeholder text for the Dropdown to display when there are no selected values.

UpdateNames (values : table) : void
If using Instances or metatables and the name of a metatable has changed (\_\_tostring metamethod), call this function to update the name displayed. This needs to be called manually due to performance concerns.

SetSelectionForced (forced : bool, reselect : bool, tweenSelection? : bool) : void
Changes whether or not the selection is forced.
`forced` changes the forced state, see `SelectionForced` for more information.
The `reselect` parameter defines if the selection should revert to only the first value in the list.
This needs to be called manually due to the immediate changes of the `reselect` parameter.

SetMultiSelection (multi : bool, reselect : bool, tweenSelection? : bool) : void
Changes the multi-select state of the dropdown.
`multi` sets whether or not the dropdown is standard selection or multi-selection. (Default: false)
The `reselect` parameter defines if the selection should revert to only the last selected value, and only applies if `multi` is set to true. (Default: true)
This needs to be called manually due to the immediate changes of the `reselect` parameter.
## ⚡ Events

ValueSelected(object : Dictionary) : RBXScriptSignal
Fires when a value is selected, and returns that value.
This only applies to selection being gained, not taken away. So, if `MultiSelect` is true or on a standard list with `SelectionLocks` set to false, and the user unselects the last value, this will not fire, however the `SelectionChanged` and `SelectionDiffered` events will fire.

SelectionChanged(objects : Array) : RBXScriptSignal
Returns a list of the currently selected objects.

SelectionDiffered(selected : object, unselected : object) : RBXScriptSignal

ValueUnselected(object : Dictionary) : RBXScriptSignal
Fires when a value is unselected, and returns that value.
> [!NOTE]
> These events only fire if the user interacts with the dropdown, or if the selection was forced by ForceSelection. They do not fire when scripts change them to prevent potential infinite loops.

