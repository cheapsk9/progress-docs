# Section

Sections allow you to organize elements on a page into separate categories. This can help your users find things more easily and mitigates the need to break categories into separate pages just to split content. For example, in a tab for auto-farm, you may want to put a section for auto-farming mobs and auto-farming items, rather than putting them together or in separate pages.

A section can be created with [`Page:CreateSection`](./Page.md).
## 🔍 Properties

Page : Dictionary [Read Only]
The [`Page`](./Page.md) that this section belongs to.

Title : string [Read Only]
The title text of this section.

TitleVisible : bool [Read Only]
## 🚀 Methods

CreateElement (name : string, configTable : Dictionary) : Dictionary
Creates an element to be displayed or interacted with in this section.

SetPage (page : Dictionary) : void
Sets which page this section belongs to.

SetTitle (text : string) : void
Sets the title displayed on the section.
## 💡 Code Example

With our existing sections we made [previously](./Page.md), we can now start to assign elements to them.
```lua
-- Now that we have our sections created, we can create some elements within them.
sections.Self.Main:CreateElement("Button", {
	Label = {
		"Hello, section",
		"I am an example button in a section"
	}
})
-- Update as of September: You can also place elements directly into pages.
pages.Self:CreateElement("Button", {
	Label = {
		"Hello, page",
		"I am an example button in the page"
	}
})
```
