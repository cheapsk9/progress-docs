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

CreateSection (name : string, titleVisible : bool) : void
Creates a section to group elements into.

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
