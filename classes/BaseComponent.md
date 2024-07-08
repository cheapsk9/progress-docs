# BaseComponent

A component is any of the following visual objects: Section, Tab, Element.

Components have properties, methods, and events just like normal Roblox instances.
They are created by calling various different functions, such as `API:CreateTab()`, `Tab:CreateSection()`, and `Section:CreateElement()`. Components make it easy for you to customize your script's UI layout by providing an intuitive, object-oriented programming approach.

## 🔍 Properties

ComponentName: string [Read Only]
The name of the component for easy referencing.
> [!IMPORTANT]
> This member is read-only, and can not be changed or written to.

Visible: bool [Read Only]
Whether or not this component is currently visible to the user.
> [!IMPORTANT]
> This member is read-only, and can not be changed or written to.

Parent: Dictionary [Read Only]
The parent component of this component. For tabs, this will be `nil`, but for Sections, this will be the corresponding Tab, and for Elements, it will be the corresponding Section.
> [!IMPORTANT]
> This member is read-only, and can not be changed or written to.
## 🚀 Methods

Destroy () : void
Destroys the section, and consequently, all of its children components. The table reference will still be valid, but will not have any external references, so can be freely garbage collected.

SetVisible (visible : bool) : void
Sets whether the component is visible and can be interacted with. If called on tabs, it will force the tab to close and the page view will go to the first tab.

Destroyed() : RBXScriptSignal
Fired when the element is destroyed.

Callbacks

Destroying()