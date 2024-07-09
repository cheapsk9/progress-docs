# Alert

Alerts are messages that display within the current page, and can have different types. Alert types have different colors and icons to stand out to the user. Place alerts at places where you need the user to see something important, or to capture their attention. For a list of alert types, see [Alert Types](alerts-reference.md).
## 🔍 Properties

AlertType: number [Read Only]
The type of alert. `0` if the alert type is unset.
> [!IMPORTANT]
> This member is read-only after setting it in CreateElement().
> Use SetAlertType() to change the alert type.
## 🚀 Methods

SetAlertType (alertType : number) : void
Sets the type of the alert. See `AlertType` for more details.