# Login

All login-related controls and properties.
## 🔍 Properties

IsWhitelist : bool [Read Only]
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
> [!WARNING] This member is deprecated in favor of `OnLogin`. Do not use for future work.
## 📞 Callbacks

OnLogin (key : Tuple<string, nil>)
Fires when the user clicks the login button. If using a key, this will return the key in the key text box, otherwise if using a whitelist, it returns `nil`.
## 💡 Code Example

**This ugly code here from the old UI docs (ignore):**
```lua
local UI = loadstring(game:HttpGet("https://raw.githubusercontent.com/cheapsk9/progress/main/main.lua"))()
UI.Login:SetVisible(true)
UI.Window:Open()
UI.LoginRequest:Connect(function(key)
    -- key validation here, THIS IS JUST AN EXAMPLE DONT MAKE FUN OF ME LOL
    if key == "secret" then
        -- success!
        print(success)
        -- For now, we will use CloseWindow until we implement the rest of the hub
        UI.Window:Close()
        proceed() -- proceed with whatever
    else
        -- failure
        UI.Window:ShowMessage("Error", "Could not validate key. Please ensure you have entered it correctly.")
    end
end)
```


