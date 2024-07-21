# BaseComponent

A component is any of the following visual objects: Section, Tab, Element.

Components have properties, methods, and events just like normal Roblox instances.
They are created by calling various different functions, such as `API:CreatePage()`, `Page:CreateSection()`, and `Section:CreateElement()`. Components make it easy for you to customize your script's UI layout by providing an intuitive, object-oriented programming approach.

## 🔍 Properties

Visible : bool [Read Only]
Whether or not this component is currently visible to the user.
## 🚀 Methods

SetVisible (visible : bool) : void
Sets whether the component is visible and can be interacted with. If called on a Page, it will force the tab to be removed and the page view will go to the first tab.