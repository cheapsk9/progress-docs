# Section

Sections allow you to organize elements on a page into separate categories. This can help your users find things more easily and mitigates the need to break categories into separate pages just to split content. For example, in a tab for auto-farm, you may want to put a section for auto-farming mobs and auto-farming items, rather than putting them together or in separate pages.
## 🔍 Properties

Tab: Dictionary [Read Only]
The tab that this section belongs to.

Title: string [Read Only]
The title text of this section.
## 🚀 Methods

CreateElement (name : string, configTable : Dictionary) : Dictionary
Creates an element to be displayed or interacted with in this section.

SetPage (page : Dictionary) : void
Sets which page this section belongs to.

SetTitle (text : string) : void
Sets the title displayed on the section.
