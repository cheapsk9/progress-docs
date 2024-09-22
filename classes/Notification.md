Notifications are ephemeral toast elements that appear for a brief amount of time and then disappear. The notifications are docked to the right side of the screen. To spawn a notification, see [API:ShowToast()](../api.md).

## 🔍 Properties

Closed : bool [Read Only]
Describes whether the notification is currently closed.
To get whether the notification is opened, simply do `local opened = not notification.Closed`
## 🚀 Methods

Close () : void
Forces the notification to tween out and close.