# Page

A page (also known as a tab in some other UI libraries) is a container for sections, which hold elements. It comes with its own tab, which can have text and an icon.
## 🔍 Properties

TabIcon : string [Read Only]
The name corresponding to the icon that this tab uses.

TabText : string [Read Only]
The text displayed on the tab.

TabInstance : Instance [Read Only]
A reference to the tab instance displayed on the sidebar.

Focused : bool [Read Only]
Whether or not the tab is in focus.
## 🚀 Methods

CreateElement (name : string, configTable : Dictionary) : Dictionary
Creates an element to be displayed or interacted with in this page.
> [!TIP] Update!
> You can now place elements directly into pages! You no longer need to create a section to place elements into. If you ever wanted to have an uncategorized element, now you can.

CreateSection (name : string, placeholder : bool, titleHidden : bool) : void
Creates a [`Section`](./Section.md) to group elements into. The second param is for legacy purposes and unused.

SetTabText (text : string) : void
Sets the text displayed on the tab.

SetTabIcon (icon : string) : void
Sets the icon displayed on the tab. For a list of icon names, see the [Icon Reference](icons-reference.md).

Focus () : void
Selects the tab and moves the page view to its corresponding page.
## ⚡ Events

PageEnter () : RBXScriptSignal
Fires when the user enters this page.

PageLeave () : RBXScriptSignal
Fires when the user leaves this page.
## 💡 Code Example

Using the pages we created [previously](./Hub.md), we can create sections with them. Next, we will [use them](./Section.md).
```lua
-- After creating our pages, we can create sections within them.
local sections = {
	Self = {
		Main = pages.Self:CreateSection("Main", false),
		Another = pages.Self:CreateSection("Cool Little Section", false)
	},
	Example = {
		Main = pages.Teleports:CreateSection("Another Page", false)
	},
	Alerts = {
		Main = pages.Alerts:CreateSection("Alerts", false)
	}
}
-- Next, we will create some elements within our newly-created sections.
```
