# The API

The **API** is the base of all of Progress. The API is returned through the `loadstring`/`require`.
For example:
```lua
local api = loadstring(game:HttpGet("https://link.to.progress/main.lua"))()
```

The API returns an object which you can interact with via scripts to control the UI library.
Under the API, certain objects have functions under them which you can call. To interact with the API, you can call these underlying functions.
For example:
```lua
local window = api.Window

window:Open()
window:ShowMessage(
    "Test Message", -- Title
    "This is a test message!" -- Description
)
```

Functions of the API are also programmed to throw the least amount of errors possible (so there's less chance of Progress being detected through `LogService`), so be sure that the API is doing what you expect. If not, your calls to the API could be failing silently. A debug console specific to Progress is being planned for the future.

Example of passing the API to a script from a basic loader:
```lua
-- Example of a lookup table with PlaceId as key and loadstring Url as value
local gameLookupTable = {
	[1234] = "https://raw.githubusercontent.com/Prosexy/games/game1234.lua",
	[2345] = "https://raw.githubusercontent.com/Prosexy/games/game2345.lua",
	[8765] = "https://raw.githubusercontent.com/Prosexy/games/game8765.lua",
	[9876] = "https://raw.githubusercontent.com/Prosexy/games/game9876.lua"
}

local gameScriptUrl = gameLookupTable[game.PlaceId]
if gameScriptUrl then
	Progress = api  -- Pass the API into the game script. Global var, not local.
	loadstring(gameScriptUrl)()
end
```

From the game script's side:
```lua
-- Localize api
local api = Progress

api.Window:ShowMessage("Hello!", "Hello from the other side!")
```
## 🔍 Properties

Base: Instance [Read Only]
A reference to the Base.

Screen: Instance [Read Only]
The screen `ScreenGui` object.
> [!NOTE]
> Due to the result of a patch, this variable no longer returns the screen, but rather the `Base`.
> To access the screen, use Base.Screen.

Renderer: Instance [Read Only]
The `BasePart` that the GUI `SurfaceGui` is adorned to.

Gui: Instance [Read Only]
The GUI `SurfaceGui` itself.

Window: Dictionary [Read Only]
A reference to the [Window](classes/Window.md) object.

Login: Dictionary [Read Only]
A reference to the [Login](classes/Login.md) object.

Hub: Dictionary [Read Only]
A reference to the [Hub](classes/Hub.md) object.
## ⚡ Events

Destroying () : RBXScriptSignal
Fired when the hub is removed from memory.

ShowToast (configTable : Dictionary) : void
Displays a toast notification whose configuration is determined by the passed `configTable`.

Toasts have the following properties. All are optional and not required, but the more information you give it, the more detailed and formed your toast will be.

| Name                   | Type                | Default  | Description                                                                                                                                                        |
| ---------------------- | ------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Title                  | string              | Optional | The title of the notification                                                                                                                                      |
| Text                   | string              | Required | The main text of the notification                                                                                                                                  |
| Type                   | number              | 0        | The type of notification. See [Toast Types](./toasts-reference.md). If unset, the notification will be styled according to the current theme colors, with no icon. |
| Duration               | number              | 5        | Duration (in seconds) the notification should stay visible                                                                                                         |
| Transparent            | bool                | Optional | Whether the notification should appear fully opaque (false, 0% transparency) or slightly transparent (true, 25% transparency)                                      |
| CloseWhenButtonClicked | boolean             | Optional | Whether to close the notification when one of the provided action buttons in `Buttons` is clicked.                                                                 |
| CloseButtonVisible     | boolean             |          | Whether the close button is visible on the notification.                                                                                                           |
| Buttons                | table of dictionary | Optional | An array of buttons to be displayed. (see below)                                                                                                                   |
 "Buttons" array:
 {
... (for *n* options):

| Name     | Type     | Default  | Description                                      |
| -------- | -------- | -------- | ------------------------------------------------ |
| Title    | string   | "Button" | The text of the button.                          |
| Callback | function | Optional | The function to call when the button is pressed. |
...
}
Example of buttons structure:
```lua
Buttons = {
	{
		Title = "OK"
		Callback = function()
			-- do something as a confirmation action
		end
	},
	{
		Title = "Cancel"
		Callback = function() end
		-- do nothing, notification will close as long as CloseWhenButtonClicked is true.
	}
}
```