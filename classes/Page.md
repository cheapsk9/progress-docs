# Page

A page (also known as a tab in some other UI libraries) is a container for elements. It comes with its own tab, which can have text and an icon.
## 🔍 Properties

TabIcon: string [Read Only]
The name corresponding to the icon that this tab uses.
> [!IMPORTANT]
> This member is read-only, and can not be changed or written to.

TabText: string [Read Only]
The text displayed on the tab.
> [!IMPORTANT]
> This member is read-only, and can not be changed or written to.

Focused: bool [Read Only]
Whether or not the tab is in focus.
## 🚀 Methods

CreateSection (name : string, iconName : string)
Creates a section to group elements into.

SetTabText (text : string) : void
Sets the text displayed on the tab.

SetTabIcon (icon : string) : void
Sets the icon displayed on the tab. For a list of icon names, see [here].

Focus () : void
Selects the tab and moves the page view to its corresponding page.
## ⚡ Events

PageFocused () : RBXScriptSignal

PageFocusReleased () : RBXScriptSignal