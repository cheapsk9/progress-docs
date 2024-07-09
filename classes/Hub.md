# Hub

All hub-related controls and properties.
## 🚀 Methods

CreatePage (tabText : string, tabIcon : string) : Page(Dictionary)
Creates a page with a tab to display in the Home section.

FocusPage (page : Dictionary) : void
Forces the passed Page to be selected.

DestroyPage (page : Dictionary) : void
Removes the passed Page from the UI entirely.
## ⚡ Events

PageChanged (currentPage : Dictionary, previousPage : Dictionary) : RBXScriptSignal
Fires when the user changes pages. The first parameter is the current page that the user went to, and the second is the previous page the user was on. Does not fire if the user clicks the same tab they are currently on.

## 📞 Callbacks

OnPageChanged: Dictionary, Dictionary
Called when the user changes the color picker's displayed color.