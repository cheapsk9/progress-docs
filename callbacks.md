# Callbacks

Callbacks in Progress have some special properties to them. These properties are explained below.
## Protected Calling
Callbacks are handled in a sanitized way. The callback function is wrapped in a `pcall` to avoid detection via `LogService`, so if your called function fails and you try looking in the console for an error message, there will be none. A debug console is planned to be implemented in the future to make debugging easier for these kinds of problems.
## Prioritized Execution Order
Callbacks are also always fired before events. This is to maintain backwards-compatibility with the deferred event system. If you want an action to be fired immediately rather than firing through the next task scheduler cycle, it is highly recommended to use callbacks instead of events wherever possible. However, sometimes you can't use callbacks (for example, on buttons). In this case, it is fine to use events instead.