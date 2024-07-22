# BaseValue

This is an abstract class which manages value objects (objects which can hold a user-defined value)
## 🔍 Properties

Enabled : bool [Read Only]
## 🚀 Methods

SetEnabled (enabled : bool) : void [Not Yet Implemented]

> [!NOTE]
> Most events and callbacks relating to `BaseValue` components changing state only fire when interacted with by users. If a script changes the value manually, the events will not fire unless explicitly stated in the documentation for that component. For example, with the `TextBox` Instance, it is impossible to tell whether scripts or the user fired the `Changed` event.