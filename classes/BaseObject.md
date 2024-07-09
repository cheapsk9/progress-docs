# BaseObject
## 🔍 Properties

ObjectName: string [Read Only]
The name of the component for easy referencing.

Instance: Instance [Read Only]
The *real* object (Roblox Instance) reference to this object, if applicable. Otherwise, returns nil.

Parent: Dictionary [Read Only]
The parent object of this object. For Pages, this will be `nil`, but for Sections, this will be the corresponding Tab, and for Elements, it will be the corresponding Section.
## 🚀 Methods

Destroy () : void
Destroys the object. If it has any children objects, those will be destroyed too. The table reference will still be valid, but will not have any external references, so can be freely garbage collected.
## ⚡ Events

Destroying () : RBXScriptSignal
Fired immediately before the object is destroyed.
However, due to deferred events, it is not guaranteed that this event will fire immediately before destroying. Recommended to use the callback `OnDestroying` instead.
## 📞 Callbacks

OnDestroying: void
Called immediately before the object is destroyed.