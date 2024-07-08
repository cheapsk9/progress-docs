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