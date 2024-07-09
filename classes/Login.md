# Login

All login-related controls and properties.
## 🔍 Properties

IsWhitelist: bool [Read Only]
Whether the authentication method uses a key (false) or whitelist (true).
## 🚀 Methods

SetKeyLink (text : string) : void
Sets the link to be copied if the user chooses to use the key system.

SetWhitelistLink (text : string) : void
Sets the link to be copied if the user chooses to use the whitelist system.

SetDiscordLink (text : string) : void
Sets the link to the Discord server to be displayed in the "Need help?" page.

SetWhitelist (whitelist : string) : void
Sets whether the authentication method uses a key or whitelist.
## ⚡ Events

WhitelistChanged (whitelist : bool) : RBXScriptSignal
Fires when the user (or scripts) change the whitelist state.

LoginRequest (key : Tuple<string, nil>) : RBXScriptSignal
Fires when the user clicks the login button. If using a key, this will return the key in the key text box, otherwise if using a whitelist, it returns `nil`.