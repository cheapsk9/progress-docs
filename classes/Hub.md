# Hub

All hub-related controls and properties.
## 🚀 Methods

CreatePage (tabText : string, tabIcon : string) : Page(Dictionary)
Creates a page with a tab to display in the Home section.

FocusPage (page : Dictionary) : void
Forces the passed Page to be selected.

DestroyPage (page : Dictionary) : void
Removes the passed Page from the UI entirely.
## 💡 Code Example

The following code example creates a few pages in the hub, in a table which we will reference [later](./Page.md).
```lua
-- Creates a few pages in the hub.
local pages = {
	Self = UI.Hub:CreatePage("Self", "home")
	Teleports = UI.Hub:CreatePage("Teleports", "swirl")
	Alerts = UI.Hub:CreatePage("Alerts", "bell-ring")
}
-- This table of pages can be used elsewhere later in the script.
```
