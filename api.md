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
