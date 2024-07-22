# Label

The **Label** element is simply a blank placeholder element with nothing in it. Since all elements have a label container attached to them, you can use the Label property of the config table to make a label. As a result, this is an empty 0px width element with no special purpose, other than to display the attached label.

See also: The `Label` property of [`BaseElement`](./BaseElement.md)

This component has no defined members.
## 💡 Code Example

```lua
sections.Self.Main:CreateElement("Label", {
	Label = {
		Title = "I am a label!",
		Text = "I am a description"
	}
})
```
